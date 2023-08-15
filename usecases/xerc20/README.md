---
description: >-
  Connext is the most secure and efficient way to create crosschain tokens: no
  infrastructure is required, and the smart contracts are easy to implement.
  Tokens can then be moved almost instantly.
---

# xERC20

## What are Connext xERC20 tokens?

xERC20 tokens are crosschain ERC-20 which can be transferred with no slippage across chains without compromising on security.

{% hint style="info" %}
Connext officially supports industry adoption of [ERC-7281: Sovereign Bridged Tokens](https://ethereum-magicians.org/t/erc-7281-sovereign-bridged-tokens/14979), which will allow token issuers to retain full sovereign control and flexibility over their tokens, regardless of which bridges they choose. These documents discuss our _Connext_ _implementation_ of this proposed standard.&#x20;
{% endhint %}

Today, when you want to make your token available on multiple chains, you have to either:

1. Provide significant liquidity to a bridge on each chain (and require users to take **slippage** when transferring across chains); or
2. Mint a _**new**_ representation of your token through the bridge, locking yourself into that bridge and its security model forever.

Connext provides a new approach to making your token **natively crosschain without compromises.** This makes your xToken:

* Transferrable across chains with no slippage.
* Deployed and fully controlled by you, the token issuer.
* Secured fully by Ethereum L1 and the canonical bridges of each chain.
* \[Coming Soon] Fungible against the token representations minted by canonical bridges (rollup bridges, Polygon PoS bridge, etc.)
