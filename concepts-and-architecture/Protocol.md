---
description: Aramid Protocol
---

# Protocol

At a high level, this is how the protocol works:

- User sends tokens to the bridge contracts on one of the blockchains.
- The bridge, which consists of many automated nodes watching the blockchain for transactions, logs a new transaction.
- The nodes then communicate with eachother, and come to consensus as to whether or not the new transaction is `valid`.
- It is valid if the current node has also seen this transaction, independently of other nodes.
- If it is valid, they sign the message, and pass it on.
- If enough signatures are found, the transaction is executed on the secondary chain.

> Here are some diagrams which aim to explain the process visually:

![](../.gitbook/assets/2.bridge-arch-flow.jpg)

> A slightly more in depth diagram, including governance, is displayed below:

![](../.gitbook/assets/2.bridge-arch.jpg)

`On to the ins and outs of our on-chain assets ...`
