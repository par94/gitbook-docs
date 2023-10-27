---
description: 'ERC-7281: Sovereign Bridged Tokens'
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# xERC20

## What are xERC20 tokens?

xERC20 ([`ERC-7281`](https://ethereum-magicians.org/t/erc-7281-sovereign-bridged-tokens/14979)) tokens are crosschain ERC-20 which can be transferred with no slippage across chains without compromising on security.

Today, when you want to make your token available on multiple chains, you have to either:

1. Provide significant liquidity to a bridge on each chain (and require users to take **slippage** when transferring across chains); or
2. Mint a _**new**_ representation of your token through the bridge, locking yourself into that bridge and its security model forever.

xERC20s are **natively crosschain without compromises.** This makes your token:

* Transferrable across chains with no slippage.
* Deployed and fully controlled by you, the token issuer, including the ability to set rate limits on a per-bridge basis.
* \[When bridged through Connext] Secured fully by Ethereum L1 and the canonical bridges of each chain.
* \[Coming Soon] Fungible against the token representations minted by canonical bridges (rollup bridges, Polygon PoS bridge, etc.)

For more information about the open standard, please check out [https://www.xerc20.com/](https://www.xerc20.com/).

{% hint style="info" %}
Connext officially supports industry adoption of [ERC-7281: Sovereign Bridged Tokens](https://ethereum-magicians.org/t/erc-7281-sovereign-bridged-tokens/14979), which will allow token issuers to retain full sovereign control and flexibility over their tokens, regardless of which bridges they choose.&#x20;

The following sections of this guide will walk through how to set up xERC20s. Secondarily, it provides instructions on how to configure Connext as one of your token's allowed bridges.
{% endhint %}

