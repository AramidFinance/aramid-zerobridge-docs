# Soldier Nodes

## Current Implementation

Zero Bridge Soldier Network is a peer-to-peer network where the nodes communicate with one another directly. It leverages the libp2p protocol for messaging and communication. This network is the Transport layer that transmits messages from one peer to another. It uses public key cryptography as the basis of peer identity. Each node have their unique Peer ID, which allows them to identify each other and communicate among themselves.

When nodes want to communicate with each other, they need to discover other nodes and use their Peer ID to send message. The network uses libp2p MulticastDNS, Bootstrap, PubsubPeerDiscovery mechanism to discover peer Ids.

The network has two topics defined, "validateEth" and "validateAlgo". It uses pubsub interface to verify, sign and send messages to all the peers for defined topics using the extensible gossip protocol "gossipsub".

Messages are encrypted with TLS 1.3 and Noise, so that no third party can read the message exchanged among the nodes.

Each solider watches a contract/ASA address, and is expecting to see a transaction. For this we use [ethereum event watchers](https://web3js.readthedocs.io/en/v1.3.4/web3-eth-contract.html#contract-events) and the [algorand indexer](https://developer.algorand.org/docs/rest-apis/indexer/).

When a soldier sees a transaction, it records it, signs it, and then passes the p2p-message to the other soldiers.

When a soldier sees a p2p-message, it queries the blockchain to see if the transaction is valid, and it makes sure it has not yet signed the message.

If these conditions are met, it then adds it's signature to the message and propagates the new message to the other peers in the network.

If a threshold number of soldiers have signed, the transaction will be submitted on-chain.

![](../.gitbook/assets/8.soldier-network.jpg)

### Disaster Recovery

Each of the soldiers in the network maintain their state in a database. In case of any unforeseen shutdown, they can come online by reading data from their storage medium.

### Incentivization

Soldiers in the system are incentivized to validate the transactions and keep the system safe and secure.
