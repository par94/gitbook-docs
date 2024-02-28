# Types

### AssetData

Ƭ **AssetData**: `Object`

**Type declaration**

| Name               | Type     |
| ------------------ | -------- |
| `local`            | `string` |
| `adopted`          | `string` |
| `canonical_id`     | `string` |
| `canonical_domain` | `string` |
| `domain`           | `string` |
| `key`              | `string` |
| `id`               | `string` |

***

### Pool

Ƭ **Pool**: `Object`

**Type declaration**

| Name             | Type        |
| ---------------- | ----------- |
| `domainId`       | `string`    |
| `name`           | `string`    |
| `symbol`         | `string`    |
| `local`          | `PoolAsset` |
| `adopted`        | `PoolAsset` |
| `lpTokenAddress` | `string`    |
| `canonicalHash`  | `string`    |
| `swapFee`        | `string`    |
| `adminFee`       | `string`    |
| `address?`       | `string`    |

***

### PoolAsset

Ƭ **PoolAsset**: `Object`

**Type declaration**

| Name       | Type        |
| ---------- | ----------- |
| `address`  | `string`    |
| `name`     | `string`    |
| `symbol`   | `string`    |
| `decimals` | `number`    |
| `index`    | `number`    |
| `balance`  | `BigNumber` |

***

### ConnextSupport

Ƭ **ConnextSupport**: `Object`

**Type declaration**

| Name       | Type        |
| ---------- | ----------- |
| `assets`   | `string`\[] |
| `chainId`  | `number`    |
| `domainId` | `string`    |
| `name`     | `string`    |

***

### XTransferStatus

Ƭ **XTransferStatus**: `Object`

**Type declaration**

<table><thead><tr><th>Name</th><th width="106.66666666666666">Type</th><th>Value</th></tr></thead><tbody><tr><td><code>XCalled</code></td><td><code>string</code></td><td>"XCalled"</td></tr><tr><td><code>Executed</code></td><td><code>string</code></td><td>"Executed"</td></tr><tr><td><code>Reconciled</code></td><td><code>string</code></td><td>"Reconciled"</td></tr><tr><td><code>CompletedFast</code></td><td><code>string</code></td><td>"CompletedFast"</td></tr><tr><td><code>CompletedSlow</code></td><td><code>string</code></td><td>"CompletedSlow"</td></tr></tbody></table>

### XTransferErrorStatus

Ƭ **XTransferStatus**: `Object`

**Type declaration**

| Name           | Type   | Value            |
| -------------- | ------ | ---------------- |
| LowSlippage    | string | "LowSlippage"    |
| LowRelayerFee  | string | "LowRelayerFee"  |
| ExecutionError | string | "ExecutionError" |
| NoBidsReceived | string | "NoBidsReceived" |
