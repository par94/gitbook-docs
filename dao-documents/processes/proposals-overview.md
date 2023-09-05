---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Proposals Overview

{% hint style="warning" %}
This document is currently subject to public review before being finalized. If you notice a revision that needs to be made or have feedback, please [request a revision](https://github.com/connext/gitbook-docs/issues/new) or start a conversation with us on Discord at [https://discord.gg/connext](https://discord.gg/connext).
{% endhint %}

## **Types of Proposals**

There are three main types of governance proposals you can make:

1. **Executable Proposal:** \
   This is a proposal for a series of smart contract operations to be executed by accounts the DAO controls. These can include transfers of tokens as well as arbitrary smart contract calls. Examples of this include allocating funding to a workstream multisig wallet, or upgrading Connext core contract. Executable proposals have a quorum requirement of 4% (24 million) NEXT tokens and require a minimum approval of 50% to pass.
2. **Social Proposal:** \
   This proposal seeks the consensus of the DAO members on a matter that cannot be implemented or enforced via on-chain mechanisms. Social proposals have a quorum requirement of 4% (24 million) NEXT tokens and require a minimum approval of 50% to pass.
3. **Constitutional Amendment:** \
   This is a social proposal that asks the DAO to amend the constitution. Draft proposal should include the exact changes proposed to be made to the constitution. Quorum of 6% (36 million) is currently required and a minimum approval of two thirds to pass.

***

## **Phases of Proposal**

### **Phase 1: Request for Comments**

_A governance forum post providing description of a proposal._

#### To create a Request for Comment:

* Ask a general, non-biased question to the community on forum about a potential change. Forum posts should be labeled as follows: “Request for Comment - \[Your Title Here]“.
* Reach out to your network to build support for the proposal. Discuss the proposal and solicit delegates to provide feedback on it. Be willing to respond to questions and comments. Share your viewpoint, but try to remain impartial.

{% hint style="info" %}
**Note**: The length of this phase should be correlated to the complexity of the proposal and allow for meaningful feedback. It’s in the proposal author’s interest to get as much feedback from the community as possible in this stage.
{% endhint %}

### **Phase 2: Temperature check**

_A second separate governance forum post outlining the proposal in detail and incorporating any feedback from the phase 1. The post should be accompanied by a Snapshot poll. The Snapshot poll runs for 5 days and is decided by a majority._

#### To Create a Temperature Check:

* Use feedback from Phase 1 and create a new Snapshot poll that covers the options that have gained support. Set the poll duration to 5 days. Ensure at least 600,000 NEXT is delegated to your address or find a delegate who has enough delegated NEXT to meet the threshold.
* Create a new topic in the Proposal Discussion category on the forum titled: \
  **“Temperature Check — \[Your Title Here]“**.&#x20;
  * This will alert the community that this topic is ready to move to an off-chain signaling vote and solicit participation. Any topics beginning with Temperature Check that have not started with a Request for Comment should be removed by community moderators. Make sure that the discussion thread links to the new Snapshot poll and the Request for Comment thread.
* At the end of 5 days, whichever option has the majority of votes wins, and can be included in a governance proposal for Stage 3. If the option to make no change wins, the topic should be closed by community moderators.

{% hint style="info" %}
**Note**: If authors make significant changes to the proposal based on feedback, they can decide to submit a new version to the Temperature Check. They need to create a new Snapshot poll and create a new topic on forum named “Temperature Check V2 — \[Your Title Here]“. They are required to link all previous votes and discussions to the new topic.
{% endhint %}

### **Phase 3: Formal Vote**

_A final governance forum post incorporating any feedback from the Temperature Check phase._\
_The proposal in this phase should include the following sections:_ [_Proposal Structure Guidelines_](https://www.notion.so/Proposal-Structure-Guidelines-b1af4d62cee04d0d9d2b5cafac46825b?pvs=21)

#### To Create a Formal Vote:

1. Create a topic in the Proposal Discussion category on forum titled “Formal Vote \[Social/Constitutional/Executable \[Proposal Number]] — \[Your Title Here]” and link to any relevant Snapshot polls/discussion threads. Proposal numbers should be in a “CIP#” format. Topics that begin with “Formal Vote” that have not successfully passed the Temperature Check and Request for Comment stages should be removed by community moderators.
2. Ensure at least 600,000 NEXT is delegated to your address in order to submit a proposal, or find a delegate who has enough delegated NEXT to meet the proposal threshold and propose on your behalf.
   * **Social Proposal or Constitutional Amendment:** \
     Navigate to Snapshot and schedule the proposal for a snapshot vote. If the snapshot vote passes, the proposal is passed and you are done!
   * **Executable Proposal:**\
     Generate the transaction using the Connext Zodiac module. If the transaction is not cross-chain, the SAFE transaction builder can be used to generate the executable data. Submit the proposal to a vote via Snapshot transaction builder. Votes last for 3 days, are delayed by 4 days after creation, and include “For”, “Abstain”, and “Against” as the voting options. If the proposal passes, anyone can request execution via Snapshot UI. Requesters must post a 5 WETH bond and there is a 3-day delay. Once the delay elapses, anyone can execute the proposal via Snapshot which will return the bond to the requester and execute on-chain transaction.

{% hint style="info" %}
**Note**: SAFE admins retain authority to delete proposals and submit their own multisig transactions, serving as a security council with veto power on community votes. More information about the Security Council is available [here](https://docs.connext.network/v/dao-documentation/collective/security-council).
{% endhint %}
