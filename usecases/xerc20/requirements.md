# Setup Overview

The steps to set up your xERC20 are very straightforward:

1. Choose a Home chain for your tokens (or whatever chain your token is already deployed to!)
2. Deploy [Mintable/Burnable](https://github.com/defi-wonderland/xTokens) Token representations on the other chains you want to support.
3. Allow bridges to support your xERC20 with custom rate limits.&#x20;

To enable Connext as one of your allowlisted bridges:

1. Send your token addresses to the Connext Labs team.
2. Give the Connext contracts rights to mint your token.
3. Work with the team to signal to Connext routers to supply fast-liquidity for your token.

💡 It is entirely possible for you to run your own router to supply fast path liquidity in Connext if you’d like! If this is prohibitively complex, however, we _**already**_ have an ecosystem of routers that can work with you to add liquidity for your token.

Routers are **highly** capital efficient (and earn money from fees), and so the network only needs about 1/8th of your expected 24h volume in liquidity in your token. Please contact us and we can help put you in touch with a router partner!

{% hint style="info" %}
You can expose bridging functionality to your users either through the [Connext Bridge](https://bridge.connext.network/) or by integrating directly into your project’s website/app. We recommend the latter because it makes your UX as smooth as possible! 😄
{% endhint %}

In the next section, we will go through all these steps in detail.
