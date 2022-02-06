---
description: >-
  Bridging helps foster cross-chain communication and break down barriers with
  different block chains. It helps transfer assets, execute transactions among
  different chains.
---

# Concepts

<mark style="color:red;">Explain bridging concepts, current bridging technology, why this technology over others, future plans on using state proofs.</mark>

<mark style="color:red;">Explain concept of generic chain connector</mark>

<mark style="color:red;">Explain Disaster Recovery</mark>

Before building the Zero Bridge, we asked ourselves many questions from very basic ones like the usability of the Bridge to more intricate ones that centered on the security, reliability of the bridge. We asked:

#### What is the user trying to accomplish when initiating a transaction between the chains?

#### What should be the user experience for a non-crypto user?

#### How do we manage transaction cost, speed, usability and reliability of the system?

#### Would we feel safe to use the bridge to transfer millions or billions of money?

#### How are the infrastructure components (Relayers, Attestors, etc.) compensated?

These questions led us to many discussions and deciding on the architecture of the bridge. We realized that the implementation of a bridge needed to address the trillemma of building any blockchain application: **Security, Scalability and De-centralization**.&#x20;

![](../.gitbook/assets/bridge-trillemma.jpg)

Unfortunately, solving one of these issues conflicted with the other. So, building a Bridge required accepting these requirements with some assumptions and limitations. There are many ways to build a bridge:

* use Atomic swap like Hash Time Locked Contract (HTLC) method.
* use a Trusted custodian, usually a group of trusted resource for added security and de-centralization
* Running a lighter node of a chain in the other chain to conduct on-chain validation

For our TestNet implementation, our scope was to bridge assets among Ethereum, Algorand and Polygon chains. We decided to use the Trusted Custodian approach with a group of Soldiers to validate the transaction. We used the "Lock & Mint" method of transferring tokens between the chains. Users send a native token from their wallet and it appears as a Wrapped Asset in the destination chain.

For an Ethereum to Algorand transfer scenario, the user sends a Token (ERC20) from the wallet in Ethereum. The Token is locked in the Bridge Smart contract and a mapped Algorand Standard Asset (ASA) is released from a Multi-sig account to the user's Algorand wallet. The user can redeem the ERC20 by initiating a transfer action from Algorand that releases the Token from the Bridge Smart Contract to user Ethereum wallet.

![Use case: Bridging Tokens among Ethereum,  Algorand and Polygon](../.gitbook/assets/3.bridge-usecase.jpg)
