# Smart Contracts and Multi-Sig account

On each chain Aramid has one escrow account. On algorand it is basic multisig address, and on other chains the smart contract that mimics algorand multisig features.

## Multi-Sig account

On the algorand blockchain, we own a [multi-signature account](https://developer.algorand.org/docs/get-details/transactions/signatures/?from_query=multi%20sig#multisignatures), which is controlled by the soldiers.

When soldiers reach a consensus on whether or not to release a transfer, they create a algorand asset transfer or algo payment transaction and submit it to the blockchain.

## Smart Contracts

On the EVM blockchains, we have an identical architecture. 

The difference here, is that ethereum has slightly more flexibility language wise, than algorand allows, and so we have developed an optimised multi-sig wallet on ethereum, which incorporates governance into the internal methods.

## Adding new blockchain - Compliant smart contract

To add new blockchain we require to have compliant smart contract. Compliant smart contract has following features.

If the chain is capable of handling the network fees paid by the smart contract and not the executioner of the smart contract, it should be implemented. 

Signatures are always made offchain, and delivered as a whole.

Escrow account has N signators and threshold (M) of signators to be required to process the transaction.

Each of the following requires M soldiers to sign the transaction.

- Multisig release native token - The payment in native tokens is released. (Algo) (payment tx algo feature)
- Multisig release sub token - The payment in sub tokens is released. (USDc, USDt)  (asset tx algo feature)
- Adding the token - The escrow account can accept the token  (asset opt in algo feature)
- Removing the token - The escrow account should not accept the token. (asset opt out algo feature)
- Adding the soldier - N is increase by 1, new soldier can sign the transactions. (rekey algo feature)
- Removing the soldier - N is decreased by 1, soldier signature is not counted. (rekey algo feature)
- Round check - If transaction is requested to be released, the round must be checked (algo params first round & last round) 
- Upgrading the smart contract - Changing the logic behind without requirement of address change. (rekey algo feature, proxy eth feature) If this feature is not possible on specific chain, it may be skipped, and migration from old smart contract to new smart contract will lead to all funds to be moved and addresses updated.

Smart contract must be able to store data on the blockchain with public availability (note field or event). When requesting a transfer following fields are required:
- feeToken : blockchain token id
- feeAmount : uint64 - uint256 base units
- sourceToken : blockchain token id. for native 0x0
- sourceAmount : uint64 - uint256 base units. source amount must be equal to tx amount. if fee is paid with the same token, it should be clear that sourceAmount + feeAmount = tx.amount
- destinationChain : uint32
- destinationToken : string
- destinationAmount : uint64 - uint256 | string (in base units of destination token)
- destinationAddress : string
- note : string (max 50 bytes)

Additional data must be readable:
- sourceAddress
- tx.amount
- round

The fee payment amount is verified by the soldier app. 

With release of the tokens following data must be stored (note field or event): 
- sourceTransaction: string (original tx hash/id)
- sourceChain : uint32 
- sourceToken : string
- sourceAmount : string - in base units
- sourceAddress : string
- destinationChain : uint32
- destinationToken : string
- destinationAmount : string - in base units
- destinationAddress : string
- note : string (max 50 bytes)

To addopt smart contract we require high test coverage, ideally in javascipt or typescript.

## Governance

Management of the token list and management of the soldiers list for each blockchain is the Aramid DAO decision done trhough the public onchain voting using [Vote Coin DAO management solution](https://www.vote-coin.com).

Algorand soldiers execute the decision publishing the aramid-config message to the blockchain. Frontend application as well as soldier middleware periodically checks for the aramid-config message and addopt to new configuration.

{% hint style="info" %}
[mainnet assets public information](https://docs.aramid.finance/getting-involved/addresses)
{% endhint %}
