# Soldier Nodes

<mark style="color:red;">Explain soldier nodes concept. The communication, security, incentivization and any other relevant information - Governance might be explained in the governance section</mark>

## Current implimentation

Zero bridge solider nodes are build using custom [libp2p](https://libp2p.io/) configurations.

Each solider watches a contract/ASA address, and is expecting to see a transaction

When a soldier sees a transaction, it records it, signs it, and then passes the p2p-message to the other sodiers.

When a soldier sees a p2p-message, it queries the blockchain to see if the transaction is valid, and it makes sure it has not yet signed the message. If these are both true, it then adds it's signature to the message and sends the new message to the network.

If a threshold number of soldiers have signed, the transaction will be submitted on-chain.
