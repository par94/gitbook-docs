# Tracking xCalls

Every `xcall` is associated with a unique `transferId` that can be used to track its lifecycle through a cross-chain transaction.

## Connextscan

The easiest option to track an `xcall` is by using [Connextscan](https://testnet.connextscan.io/) to look up any `transferId`. In the top right search box, enter the `transferId` of interest.

Connextscan will pull up current status of the associated `xcall`.&#x20;

## Querying Subgraphs

You can also query the [hosted subgraphs](../../resources/subgraphs.md#mainnet-subgraphs) on each chain to check the transaction status.&#x20;

1. Make note of the transaction hash that interacted with the Connext contract.
2. Navigate to the hosted subgraph for the origin domain and query by the xcall's transaction hash or the transfer ID.

```graphql
query OriginTransfer {
  originTransfers(
    where: {
      # Query by the transaction hash of the xcall
      transactionHash: "<TRANSACTION_HASH>",
      # Or by the xcall's transfer ID
      transferId: "<TRANSFER_ID>"
    }
  ) {
    # Meta Data
    chainId
    nonce
    transferId
    to
    delegate
    receiveLocal
    callData
    slippage
    originSender
    originDomain
    destinationDomain
    transactionHash
    bridgedAmt
    status
    timestamp
    normalizedIn
    # Asset Data
    asset {
      id
      adoptedAsset
      canonicalId
      canonicalDomain
    }
  }
}
```

3. Navigate to the hosted subgraph for the destination domain and query by the `transferId` obtained from the origin domain subgraph.

```graphql
query DestinationTransfer {
  destinationTransfers(
    where: {
      transferId: "<TRANSFER_ID>"
    }
  ) {
    # Meta Data
    chainId
    nonce
    transferId
    to
    callData
    originDomain
    destinationDomain
    delegate
    # Asset Data
    asset {
      id
    }
    bridgedAmt
    # Executed event Data
    status
    routers {
      id
    }
    originSender
    # Executed Transaction
    executedCaller
    executedTransactionHash
    executedTimestamp
    executedGasPrice
    executedGasLimit
    executedBlockNumber
    # Reconciled Transaction
    reconciledCaller
    reconciledTransactionHash
    reconciledTimestamp
    reconciledGasPrice
    reconciledGasLimit
    reconciledBlockNumber
    routersFee
    slippage
  }
}
```

4. If there was a nested `xcall` involved on the destination side, the `executedTransactionHash` from step 3 can be used as the _new_ origin-side transaction hash. To trace the nested `xcall`, go back to step 1 using this `executedTransactionHash` but instead consider the current destination domain as the origin domain.

## XCall Status

| Status        | Description                                                                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| XCalled       | Transaction has been initiated on origin.                                                                                                                                 |
| Executed      | Funds have been delivered and calldata executed on destination, if applicable. If this happens before Reconciled, then this was a fast path transfer (non-authenticated). |
| Reconciled    | Funds have been reimbursed to routers. If this happens before Executed, then this was a slow path transfer (authenticated).                                               |
| CompletedFast | Transaction has been Executed and then Reconciled.                                                                                                                        |
| CompletedSlow | Transaction has been Reconciled and then Executed.                                                                                                                        |
