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

| Name            | Type     | Value           |
| --------------- | -------- | --------------- |
| `XCalled`       | `string` | "XCalled"       |
| `Executed`      | `string` | "Executed"      |
| `Reconciled`    | `string` | "Reconciled"    |
| `CompletedFast` | `string` | "CompletedFast" |
| `CompletedSlow` | `string` | "CompletedSlow" |
