# Setup Guide

Hello! 👋 This document will guide you through the process of setting up your xERC20 token with Connext.

## Prerequisites

Let’s assume the following information about your token before we begin:

1. Your token is already deployed to a “home” chain. The implementation here doesn’t matter.
2. If your token is deployed to other chains, it has a owner-controlled mint/burn interface or is upgradeable.

## Deploying Token Representations

{% hint style="info" %}
💡 The below sections specifically focus on testnet deployment. See [Mainnet Deployment](setup-guide.md#mainnet-deployment) for mainnet-specific information.
{% endhint %}

The first thing you will need to do is deploy a representation of your token to each chain that you want to support with the following properties:

* MUST support a standard mint/burn interface.
* MUST give Connext’s contracts the rights to mint/burn the token.
* SHOULD be an upgradeable implementation so you can mi}grate to the full xERC20 standard in the future (which supports fungibility with canonical bridges).

## Getting Allowlisted

After deployment, your token representations need to be allowlisted in Connext before the protocol can know to mint/burn them across chains. This process involves submitting two PRs:

1.  The first PR must be submitted to our [ChainData mappings](https://github.com/connext/chaindata/blob/main/crossChain.json).

    * For each chain in the mappings that your token is deployed to, add an object that looks like the following, keyed by your token address. Note that the `mainnetEquivalent` field refers to your asset’s address on Ethereum L1 - this is used to retrieve oracle pricing data in the cases where it is relevant. If your token is not deployed to Ethereum L1, feel free to leave this field blank.

    ```json
    "0xc234A67a4F840E61adE794be47de455361b52413": {
        "name": "Dai Stablecoin",
        "symbol": "DAI",
        "mainnetEquivalent": "0x6B175474E89094C44Da98b954EedeAC495271d0F",
        "decimals": 18
    },
    ```
2.  The second PR must be submitted to [our allowlisting scripts](https://github.com/connext/monorepo/blob/main/packages/deployments/contracts/src/cli/init/config/testnet/production.ts).

    * Each representation is indexed by domain (a Connext-specific identifier per chain that exists for forward compatibility with non-evm chains). [You can find a list of domains here](broken-reference).

    ```json
    {
      name: "WMATIC",
      canonical: {
        domain: "9991",
        address: "0x9c3c9283d3e44854697cd22d3faa240cfb032889",
        decimals: 18,
      },
      representations: {
        "1735356532": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
        "1735353714": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
        "9991": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
        /// ARBITRUM-GOERLI
        "1734439522": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
        /// ZKSYNC-TEST
        "2053862260": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
        /// CONSENSYS-ZKEVM-TEST
        "1668247156": {
          local: "0xcAA61BCAe7D37Fe9C33c0D8671448254eef44D63",
          adopted: "0xcAA61BCAe7D37Fe9C33c0D8671448254eef44D63",
        },
        /// POLYGON-ZKEVM-TEST
        "1887071092": {
          local: "0x0000000000000000000000000000000000000000",
          adopted: "0x0000000000000000000000000000000000000000",
        },
      },
    ```

{% hint style="info" %}
📌 Please reference the ChainData PR in your PR to our allowlisting scripts to make it easier for the reviewer!
{% endhint %}

Once this is done, the Connext Labs team will review your PRs to sanity check deployment details. Once your PR is approved, your tokens will be whitelisted and transferrable across chains!

## ConnextScan and Bridge Support

To make it easier to test and track your token transfers, we recommend adding your token to ConnextScan (the Connext network explorer) and the Connext Bridge. You’ll need to submit two more PRs for this:

1.  Submit a PR to [the ConnextScan repository config](https://github.com/CoinHippo-Labs/connextscan-ui/blob/main/config/testnet/assets.json).

    * As an example:

    ```json
    {
      "id": "tkn",
      "symbol": "TKN",
      "name": "TKN",
      "image": "/logos/assets/tkn.png",
      "is_stablecoin": true,
      "contracts": [
        {
          "contract_address": "0x16F63C5036d3F48A239358656a8f123eCE85789C",
          "chain_id": 5,
          "decimals": 18,
          "symbol": "TKN"
        },
        {
          "contract_address": "0x3Db593146464816F10d4eBA4743C76A5A4D08425",
          "chain_id": 420,
          "decimals": 18,
          "symbol": "TKN"
        }
      ],
      "color": "#000000"
    },
    ```
2.  Submit a PR to the [Bridge repository config](https://github.com/CoinHippo-Labs/connext-bridge/blob/main/config/testnet/assets.json).

    * As an example:

    ```json
    {
      "id": "tkn",
      "symbol": "TKN",
      "name": "TKN",
      "image": "/logos/assets/tkn.png",
      "is_stablecoin": true,
      "contracts": [
        {
          "contract_address": "0x16F63C5036d3F48A239358656a8f123eCE85789C",
          "chain_id": 5,
          "decimals": 18,
          "symbol": "TKN"
        },
        {
          "contract_address": "0x3Db593146464816F10d4eBA4743C76A5A4D08425",
          "chain_id": 420,
          "decimals": 18,
          "symbol": "TKN"
        }
      ],
      "color": "#000000",
      "group": "other_tokens"
    },
    ```

And that’s it! Once these PRs are merged, you should see your token appear on [https://testnet.connextscan.io](https://testnet.connextscan.io) and [https://testnet.bridge.connext.network](https://testnet.bridge.connext.network).

## Router Liquidity

At this point, your token should be transferrable across chains with no added fees or slippage. However, because of how Connext’s model works, these transfers will happen in large batches through Ethereum L1 roughly once every 2-3 hours.

{% hint style="info" %}
💡 Learn more about [fast and slow path execution here](../../concepts/how-it-works/transaction-lifecycle.md).
{% endhint %}

If your usecase requires fast (i.e. <2 minute) transfers across chains, you will need some routers in our network to supply some liquidity to execute transactions immediately on behalf of users.

1.  **For testnet**. This is pretty easy to set up:

    * Mint or faucet your tokens to your address on each supported chain.
    * Navigate to a router’s page on Connextscan - we recommend [the Connext Labs router here](https://testnet.connextscan.io/router/0xd2ad711861ab345977b7379c81165708c8717ff1) as other routers may have inconsistent uptime.
    * Click `Manage Router`
    * Add liquidity on each chain

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48b6e1ee-e854-4e31-8dbc-947d526b5a51/Untitled.png)
2. **For mainnet.** Please reach out to the Connext team and we can help work through options here with our router partners.

## Mainnet Deployment

Getting set up on mainnet is largely the same as the testnet process. You’ll need to submit PRs to the following files instead of the testnet ones:

1. [ChainData (same file as above instructions).](https://github.com/connext/chaindata/blob/main/crossChain.json)
2. [Mainnet allowlist config](https://github.com/connext/monorepo/blob/main/packages/deployments/contracts/src/cli/init/config/mainnet/production.ts).
3. [Mainnet ConnextScan config.](https://github.com/CoinHippo-Labs/connextscan-ui/blob/main/config/mainnet/assets.json)
4. [Mainnet Bridge config.](https://github.com/CoinHippo-Labs/connext-bridge/blob/main/config/mainnet/assets.json)
