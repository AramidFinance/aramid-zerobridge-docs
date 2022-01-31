---
description: 'There are many approaches to swapping assets between two disparate chains:'
---

# Concepts

<mark style="color:red;">Explain bridging concepts, current bridging technology, why this technology over others, future plans on using zk proofs.</mark>

* Use Atomic swap like Hash Time Locked Contract (HTLC) method, without middle man
* Use a trusted custodian, usually a group of trusted resource for added security and de-centralization
* Full on-chain validation
* On chain validation by running lighter node of the other chain to validate block headers

While designing the architecture, we took into account the challenges associated with trillemma of building a bridge: **Security, De-centralization and Scalability**.

We asked ourselves many questions from very basic to more intricate what reflected on the these challenges:

#### What problem the user is trying to solve when initiating a transaction between the chains?

#### Who is submitting and what transactions on the Blockchain?

#### How do we manage transaction cost, speed, usability and reliability of the system?

#### Would we use the bridge to transfer a billion dollar bill?

#### What trust assumptions are embedded into the system?

#### How are the infrastructure components (Relayers, Attestors, etc.) compensated?

Solution to one question became a bottleneck for the other. It is a vexing problem that defied any clear-cut solution.

For our TestNet implementation, we used a group of trusted resources called validators to swap assets among Ethereum, Algorand and Polygon chains.

We used the "Lock & Mint" method of transferring tokens between the chains. Users send a native token from their wallet and it appears as a Wrapped Asset in the destination chain. For an Ethereum to Algorand transfer scenario, the user sends a Token (ERC20) from the wallet in Ethereum. The Token is locked in the Bridge Smart contract and a mapped Algorand Standard Asset (ASA) is released from a Multi-Sig account to the user's Algorand wallet. The user can now redeem the ERC20 by initiating a transfer action from Algorand that releases the Token from the Bridge Smart Contract to user Ethereum wallet.

![Ethereum to Algorand Transfer](../.gitbook/assets/bridge-usecase1.png)

![Algorand to Ethereum Transfer](../.gitbook/assets/bridge-usecase2.png)
