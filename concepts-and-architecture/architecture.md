---
description: Aramid Protocol
---

# Architecture

Aramid Protocol architecture ensures secure and reliable asset transfer between the chains. The system has smart contracts and tokens deployed in the Ethereum and Polygon chains. A multisig account owns the ASAs in the Algorand chain. A peer-to-peer soldier network generates a cryptographic proof by verifying message signatures off chain and submits request on chain after threshold signtaure is reached. The multisig is further verified on chain before the asset is released.&#x20;

### Bridge Setup

As part of bootsrapping the system, the Contract is deployed with a set of trusted soldiers. To use an ERC20 token for bridging assets, it must be whitelisted by the bridge. There is an ERC20 to ASA mappings defined in the system that ensure correct token is deposited in the destination chain.

### Smart Contracts

The core of the bridge includes _lockAsset_ and _releaseToken_ methods.&#x20;

The _lockAsset_ method deposits the token in the contract using ERC20 tranfer methods.

In `releaseToken`, we expect to get a validator encoded array of bytes submitted to the bridge, along with corresponding transaction parameters. The array of bytes is decoded and is compared to the transaction parameters. Along with this, the decoded array of bytes is checked for uniqueness against the list of confirmed validators.

If all decoded addresses are unique, and there are enough of them (> bridge defined threshold), and they match with the proposed transaction parameters, and the transaction is new, only then do we release assets.

### Algorand MultiSig Wallet

On the Algorand blockchain, the Aramid Protocol treasury is defined by the [multi-signature wallet](https://developer.algorand.org/docs/get-details/accounts/create/?from\_query=multisig#multisignature) who mints ASA.

### Event Triggering

As the user request to transfer an asset is submitted on the chain, an event is triggered on the Ethereum chain and similarly, any transactions on the Algorand chain is monitored with note on the transaction.

### Peer to Peer Network

The peer to peer network is described in details in the soldier nodes section validates all transactions off-chain before it is posted on chain.

Pictorial representation of different components of Aramid Protocol system is provided below:

![](../.gitbook/assets/2.bridge-arch.jpg)

### Process Flow

The detail steps and its interaction with individual components for an Ethereum to Algorand asset transfer is shown below:

![](../.gitbook/assets/2.bridge-arch-flow.jpg)

###
