# Chain Abstraction Guide

A chain abstraction integration will generally involve two steps: writing an adapter contract and constructing `calldata` for users to send.

The [Chain Abstraction Reference](https://github.com/connext/chain-abstraction-reference) is an example repository with adapter contracts and a frontend that implements the full stack of the integration. We'll be referencing code from it in this guide.

## Adapter Contract

The adapter is a smart contract that integrators must build. It should implement the [`xReceive`](broken-reference) interface and be deployed to all destination chains that the integrating protocol supports. After the user's transaction has been dispatched and their funds/data arrive on the destination chain, this contract will be called to handle all the execution logic for the protocol.

The execution logic includes a swap and a "forward call". The swap converts the Connext-bridged asset into the asset that will be used for the protocol's function call (a.k.a "target function"). The forward call is where the adapter contract actually calls the "target function".

The following sections will walk through how to implement these two parts.

### Installation

Assuming you're using [Foundry](https://book.getfoundry.sh/), you can add the Connext contracts to your project by running the following command to install the [`connext-integration`](https://github.com/connext/connext-integration/tree/main) repository as a submodule:

```bash
forge install connext/connext-integration
```

The library will be installed to `lib/connext-integration`.

### SwapForwarderXReceiver

The [`SwapForwarderXReceiver`](https://github.com/connext/chain-abstraction-integration/blob/main/contracts/destination/xreceivers/Swap/SwapForwarderXReceiver.sol#L11) is an audited abstract contract that should be implemented by adapter contracts.

```solidity
abstract contract SwapForwarderXReceiver is ForwarderXReceiver, SwapAdapter {
  using Address for address;

  /// @dev The address of the Connext contract on this domain.
  constructor(address _connext) ForwarderXReceiver(_connext) {}

  /// INTERNAL
  /**
   * @notice Prepare the data by calling to the swap adapter. Return the data to be swapped.
   * @dev This is called by the xReceive function so the input data is provided by the Connext bridge.
   * @param _transferId The transferId of the transfer.
   * @param _data The data to be swapped.
   * @param _amount The amount to be swapped.
   * @param _asset The incoming asset to be swapped.
   */
  function _prepare(
    bytes32 _transferId,
    bytes memory _data,
    uint256 _amount,
    address _asset
  ) internal override returns (bytes memory) {
    //highlight-start
    (address _swapper, address _toAsset, bytes memory _swapData, bytes memory _forwardCallData) = abi.decode(
      _data,
      (address, address, bytes, bytes)
    );
    //highlight-end

    uint256 _amountOut = this.exactSwap(_swapper, _amount, _asset, _toAsset, _swapData);

    return abi.encode(_forwardCallData, _amountOut, _asset, _toAsset, _transferId);
  }
}
```

Notice that the `_prepare` function expects a `bytes memory _data` parameter that will be decoded into:

* `_swapper`: The specific swapper that will be used for the swap on the destination domain.
* `_toAsset`: The asset that should be swapped into.
* `_swapData`: The encoded swap data that will be constructed offchain (using the [Chain Abstraction SDK](https://github.com/connext/monorepo/tree/main/packages/agents/chain-abstraction) in the next section).
* `_forwardCallData`: The forward call data that the receiver contract will call on the destination domain.

### Adapter Contract

The adapter inherits `SwapForwarderXReceiver` and implements the `_forwardFunctionCall` method.&#x20;

For example, let's take a look at the `Greeter` from the [Chain Abstraction Reference](https://github.com/connext/chain-abstraction-reference) repo and pretend that this is the existing contract for a protocol that wants to use the chain abstraction pattern.

```solidity
pragma solidity ^0.8.19;

import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";

interface IGreeter {
  function greetWithTokens(address _token, uint256 _amount, string calldata _greeting) external;
}

contract Greeter is IGreeter {
  string public greeting;
  IERC20 public WETH;

  event GreetingUpdated(string _greeting);

  constructor(address _WETH) {
    WETH = IERC20(_WETH);
  }

  function greetWithTokens(address _token, uint256 _amount, string calldata _greeting) external override {
    IERC20 token = IERC20(_token);

    require(_token == address(WETH), "Token must be WETH");
    require(_amount > 0, "Amount cannot be zero");
    require(
      token.allowance(msg.sender, address(this)) >= _amount,
      "User must approve amount"
    );

    token.transferFrom(msg.sender, address(this), _amount);

    greeting = _greeting;
    emit GreetingUpdated(_greeting);
  }
}
```

The "target function" we want to call cross-chain is `greetWithTokens` which takes payment in any amount of WETH to update the greeting.

So `GreeterAdapter` below is the adapter contract that needs to be created:

```solidity
pragma solidity ^0.8.19;

import {IERC20} from "@openzeppelin/contracts/token/ERC20/IERC20.sol";
import {SwapForwarderXReceiver} from "lib/chain-abstraction-integration/contracts/destination/xreceivers/Swap/SwapForwarderXReceiver.sol";
import {IGreeter} from "./Greeter.sol";

contract GreeterAdapter is SwapForwarderXReceiver {
  IGreeter public immutable greeter;

  constructor(address _connext, address _greeter) SwapForwarderXReceiver(_connext) {
    greeter = IGreeter(_greeter);
  }

  function _greetWithTokens(address _token, uint256 _amount, string memory _greeting) internal {
    IERC20 token = IERC20(_token);
    token.approve(address(greeter), _amount);
    greeter.greetWithTokens(_token, _amount, _greeting);
  }

  function _forwardFunctionCall(
    bytes memory _preparedData,
    bytes32 /*_transferId*/,
    uint256 /*_amount*/,
    address /*_asset*/
  ) internal override returns (bool) {
    (bytes memory _forwardCallData, uint256 _amountOut, ,) = abi.decode(
      _preparedData,
      (bytes, uint256, address, address)
    );
    (address _token, string memory _greeting) = abi.decode(_forwardCallData, (address, string));

    // Forward the call
    _greetWithTokens(_token, _amountOut, _greeting);

    return true;
  }
}

```

The `_forwardFunctionCall` function unwraps data which includes arguments for the forward call (`greetWithTokens`) and the amount of tokens received after the swap. It then "forwards" the call to the `greeter` contract.

That's it!

## Origin Domain Transaction

The second part of the integration is to set up the transaction that users send on the origin domain. This involves a few steps but Connext's [Chain Abstraction SDK](https://www.npmjs.com/package/@connext/chain-abstraction) makes this process easier:

1. Use `getPoolFeeForUniV3` to fetch the `poolFee` for a specific swap route on the destination domain
2. Construct the `forwardCallData` for the integrating protocol's "target function"
3. Use `getXCallCallData` to construct the `calldata` that will be passed into `xcall`
4. Use `prepareSwapAndXCall` to combine the swap and the `xcall` into a single transaction request

With Connext's [Core SDK](https://www.npmjs.com/package/@connext/sdk):

1. Use `estimateRelayerFee` to fetch the `relayerFee` for the `xcall`
2. Use `calculateAmountReceived` to show users the expected amount received on the destination domain

### Installation

For installing the SDKs, use **Node.js v18**.

```bash
npm install @connext/chain-abstraction @connext/sdk
```

### 1) Get the pool fee

First we need to retrieve inputs for the destination swap. The function `getPoolFeeForUniV3` returns the poolFee of the UniV3 pool for a given token pair which will be used in the UniV3 router execution. The poolFee is the fee that is charged by the pool for trading tokens.

```ts
export const getPoolFeeForUniV3 = async (
  domainId: string,
  rpc: string,
  token0: string,
  token1: string,
):
```

The function takes four parameters:

* `domainId`: The target domain ID.
* `rpc`: The RPC endpoint for a given domain.
* `token0`: The first token address.
* `token1`: The second token address.

The function returns a `Promise` that resolves to a string representing the poolFee of the UniV3 pool.

**Example**

```ts
// asset address
const POLYGON_WETH = "0x7ceB23fD6bC0adD59E62ac25578270cFf1b9f619";
const POLYGON_USDC = "0x2791bca1f2de4661ed88a30c99a7a9449aa84174";
// Domain details
const POLYGON_DOMAIN_ID = "1886350457";
const POLYGON_RPC_URL = "https://polygon.llamarpc.com";

const poolFee = await getPoolFeeForUniV3(POLYGON_DOMAIN_ID, POLYGON_RPC_URL, POLYGON_WETH, POLYGON_USDC);
```

### 2) Encode the forward call

This step depends on the target function. In our `Greeter` example, the encoded calldata is quite simple:

```typescript
const forwardCallData = utils.defaultAbiCoder.encode(
  ["address", "string"],
  [POLYGON_WETH, "hello world"],
);
```

### 3) Construct the xcall

The `getXCallCallData` function generates calldata to be passed into `xcall`. This combines the destination swap and the forward call.

```ts
export const getXCallCallData = async (
  domainId: string,
  swapper: Swapper,
  forwardCallData: string,
  params: DestinationCallDataParams,
)
```

It takes four parameters.

* `domainId`: A string representing the destination domain ID.
* `swapper`: A string representing which swapper should be used. It can be `UniV2`, `UniV3`, or `OneInch`.
* `forwardCallData`: encoded data for passing into the target contract using `abiencoder`.
*   `params`: An object containing the following fields.

    ```ts
    {
      fallback: string;
      swapForwarderData: {
        toAsset: string;
        swapData: {
          amountOutMin: string;
        } | {
          amountOutMin: string;
          poolFee: string;
        };
        forwardCallData: {
          cTokenAddress: string;
          underlying: string;
          minter: string;
        } | {} | {};
      }
    }
    ```
* `fallback`: The fallback address to send funds to if the forward call fails on the destination domain.
* `swapForwarderData`: An object with the following fields.
  * `toAsset`: Address of the token to swap into on the destination domain.
  * `swapData`: Calldata that the swapper contract on the destination domain will use to perform the swap.
  * `forwardCallData`: Calldata that the xReceive target on the destination domain will use in the forward call.

The function returns the encoded calldata as a string.

**Example**

```ts
const params: DestinationCallDataParams = {
  fallback: USER_ADDRESS as `0x${string}`,
  swapForwarderData: {
    toAsset: POLYGON_WETH,
    swapData: {
      amountOutMin: "0",
      poolFee,
    },
  },
};

const xCallData = await connextService.getXCallCallDataHelper(
  destinationDomain,
  forwardCallData,
  params,
);
```

### 4) Prepare swap and xcall

The `prepareSwapAndXCall` function constructs the `TransactionRequest` that contains the origin swap and `xcall`.

```ts
export const prepareSwapAndXCall = async (
  signerAddress: string,
  params: SwapAndXCallParams,
):
```

It takes two parameters:

* `signerAddress` (required): The address of the signer to send a transaction from.
* `params`: An object containing the following fields:
  * `originDomain` (required): The origin domain ID.
  * `destinationDomain` (required): The destination domain ID.
  * `fromAsset` (required): The address of the asset to swap from.
  * `toAsset` (required): The address of the asset to swap to.
  * `amountIn` (required): The number of fromAsset tokens.
  * `to` (required): The address to send the asset and call with the calldata on the destination.
  * `delegate` (optional): The fallback address on the destination domain which defaults to `to`.
  * `slippage` (optional): Maximum acceptable slippage in BPS which defaults to 300. For example, a value of 300 means 3% slippage.
  * `route` (optional): The address of the swapper contract and the data to call the swapper contract with.
  * `callData` (optional): The calldata to execute (can be empty: "0x").
  * `relayerFeeInNativeAsset` (optional): The fee amount in native asset.
  * `relayerFeeInTransactingAsset` (optional): The fee amount in the transacting asset.

The function returns a Promise that resolves to a `TransactionRequest` object to be sent to the RPC provider.

**Example**

```ts
const swapAndXCallParams = {
  originDomain: "1886350457",
  destinationDomain: "6450786",
  fromAsset: OPTIMISM_WETH
  toAsset: OPTIMISM_USDC,
  amountIn: "1000000000000000000"; // 1 WETH
  to: signerAddress,
  relayerFeeInTransactingAsset: "100000", // 0.1 USDC
};

const txRequest = await prepareSwapAndXCall(swapAndXCallParams, signerAddress);
```

### 5) Estimate relayer fee

Relayer fees must be paid by the user initiating `xcall`. The Core SDK exposes an `estimateRelayerFee` function (see [Estimating Fees](chain-abstraction-guide.md#5-estimate-relayer-fee)) that returns an estimate given current gas prices on the origin and destination domains.

### 6) Estimate amount received

Showing an estimate of the final amount to be used in the destination target function can be informative for users. The `getEstimateAmountReceived` function returns this estimate which accounts for slippage from the origin and destination swaps as well as the bridge operation itself.&#x20;
