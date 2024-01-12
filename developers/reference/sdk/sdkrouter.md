# SdkRouter

SDK class encapsulating router functions.

## Hierarchy

*   `SdkShared`

    ↳ **`SdkRouter`**

## Methods

### addLiquidityForRouter

▸ **addLiquidityForRouter**(`params`): `Promise`<`TransactionRequest`>

Returns the transaction request for adding liquidity to a router.

**Parameters**

| Name                  | Type     | Description                              |
| --------------------- | -------- | ---------------------------------------- |
| `params`              | `Object` | addLiquidityForRouter parameters object. |
| `params.amount`       | `string` | The amount of the token to add.          |
| `params.domainId`     | `string` | The domain ID.                           |
| `params.router`       | `string` | The address of the router.               |
| `params.tokenAddress` | `string` | The address of the token.                |

**Returns**

`Promise`<`TransactionRequest`>

providers.TransactionRequest object.

***

### removeRouterLiquidity

▸ **removeRouterLiquidity**(`params`): `Promise`<`TransactionRequest`>

Returns the transaction request for removing liquidity from a router.

**`Remarks`**

This function is permissioned to the router owner only.

**Parameters**

| Name                  | Type     | Description                                            |
| --------------------- | -------- | ------------------------------------------------------ |
| `params`              | `Object` | removeRouterLiquidity parameters object.               |
| `params.amount`       | `string` | The amount of the token to add.                        |
| `params.domainId`     | `string` | The domain ID.                                         |
| `params.recipient`    | `string` | The address where the removed funds will be delivered. |
| `params.tokenAddress` | `string` | The address of the token.                              |

**Returns**

`Promise`<`TransactionRequest`>

providers.TransactionRequest object.

***

### removeRouterLiquidityFor

▸ **removeRouterLiquidityFor**(`params`): `Promise`<`TransactionRequest`>

**Parameters**

| Name                  | Type     |
| --------------------- | -------- |
| `params`              | `Object` |
| `params.amount`       | `string` |
| `params.domainId`     | `string` |
| `params.recipient`    | `string` |
| `params.router`       | `string` |
| `params.tokenAddress` | `string` |

**Returns**

`Promise`<`TransactionRequest`>

***

### create

▸ `Static` **create**(`_config`): `Promise`<`SdkRouter`>

Create a singleton instance of the SdkRouter class.

**Parameters**

| Name                    | Type                                                                                   | Default value | Description                                             |
| ----------------------- | -------------------------------------------------------------------------------------- | ------------- | ------------------------------------------------------- |
| `_config`               | `Object`                                                                               | undefined     | SdkConfig object.                                       |
| `_config.chains`        | `Record`<`string`, { providers: string\[] }>                                           | undefined     | Chain config, at minimum with providers for each chain. |
| `_config.signerAddress` | `string`                                                                               | undefined     | Signer address for transactions.                        |
| `_config.logLevel`      | `"fatal"` \| `"error"` \| `"warn"` \| `"info"` \| `"debug"` \| `"trace"` \| `"silent"` | "info"        | (optional) Logging severity level.                      |
| `_config.network`       | `"testnet"` \| `"mainnet"`                                                             | "mainnet"     | (optional) Blockchain environment to interact with.     |

**Returns**

`Promise`<`SdkRouter`>

providers.TransactionRequest object.

**`Example`**

```ts
import { SdkRouter } from "@connext/sdk";

const config = {
  signerAddress: "<wallet_address>",
  network: "mainnet",
  chains: {
    6648936: { // the domain ID for Ethereum Mainnet
      providers: ["https://rpc.ankr.com/eth"],
    },
    1869640809: { // the domain ID for Optimism
      providers: ["https://mainnet.optimism.io"]
    },
    1886350457: { // the domain ID for Polygon
      providers: ["https://polygon-rpc.com"]
    },
  },
}

const sdkRouter = await SdkRouter.create(config);
```

{% hint style="info" %}
See the [Deployments](broken-reference) page for all domain IDs and asset addresses.
{% endhint %}
