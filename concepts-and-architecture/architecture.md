---
description: Zero Bridge
---

# Architecture

<mark style="color:red;">How do we want to display the architecture in a structured and visual way to cover all scenarios.</mark>

<mark style="color:red;">Explain bridging concepts, current bridging technology, why this technology over others, future plans on using state proofs.</mark>

<mark style="color:red;">Explain concept of generic chain connector</mark>

<mark style="color:red;">Explain Disaster Recovery</mark>

Zero Bridge architecture ensures secure and reliable asset transfer between the chains. The system has Bridge Smart Contract and Zero Bridge tokens deployed in the Ethereum and Polygon chain and a multisig account owning the ASA created in the Algorand chain. As part of boostrapping the system, the Contract is deployed with a set of trusted soldiers. There is an ERC20 to ASA mapping defined in the system. As the user request to transfer an asset is submitted on theh chain, it is monitored by respective processes. The peer-to-peer soldier network that generates a sryptographic proof by verifying threshold message signatures off chain and submits on the chain. The multisig is further verified on chain before the asset is released. System throughput can be improved by bundling the transactions.

![](../.gitbook/assets/2.bridge-arch.jpg)

The detail steps and its interaction with individual components for an Ethereum to Algorand asset transfer is shown below:

![](../.gitbook/assets/2.bridge-arch-flow.jpg)
