# FAQ

## Where can I find the the supported chains, assets, domainIDs, and Connext contracts?

An updated list can be found in [Deployments](broken-reference).

## What are token "flavors"?

<figure><img src="../.gitbook/assets/assets.png" alt=""><figcaption></figcaption></figure>

## How do I find the canonical details of a token?

The canonical domainId and tokenId of a token can be found by calling the [`getTokenId`](https://github.com/connext/monorepo/blob/3d0af2251b2d8d244d2617be6fb738c09a571022/packages/deployments/contracts/contracts/core/connext/helpers/TokenRegistry.sol#L176) function of `TokenRegistry`.

Example:

* The token of interest is TestERC20 (`0x7ea6eA49B0b0Ae9c5db7907d139D9Cd3439862a1`) on Goerli. We want to figure out its canonical domainId and tokenId.
* Find the Connext contract address on Goerli [from here](broken-reference), click its link to open up the Diamond Inspector on Louper.
* Find the `TokenFacet` and click the "Read" button.
* Select the `getTokenId` method and input the TestERC20 address to obtain its canonical details.

<figure><img src="../.gitbook/assets/read_tokenId.png" alt=""><figcaption></figcaption></figure>

*   Alternatively, you can call `getTokenId` using a tool like Foundry's `cast` to read from the contract.

    ```bash
    cast call --chain goerli 0x99A784d082476E551E5fc918ce3d849f2b8e89B6 "getTokenId(address)(uint32,bytes32)" "0x7ea6eA49B0b0Ae9c5db7907d139D9Cd3439862a1" --rpc-url <goerli_rpc_url>
    ```

    Returns:

    ```bash
    1735353714 # the canonical domainId is Goerli
    0x0000000000000000000000007ea6ea49b0b0ae9c5db7907d139d9cd3439862a1 # the canonical bytes32 tokenId
    ```

## What if I just want to test the destination-side target function?

If there’s no token transfer involved then just set `transactingAssetId: address(0)` and `amount: 0`.

## Do I need to do anything with the AMB contracts?

No, you do not need to deploy or even interact with AMB contracts directly.

