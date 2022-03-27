# Smart Contracts and Multi-Sig Wallets

## Multi-Sig Wallets

On the algorand blockchain, we own a [multi-signature wallet](https://developer.algorand.org/docs/get-details/transactions/signatures/?from_query=multi%20sig#multisignatures), which is controlled by the validators.

When validators reach a consensus on whether or not to release a transfer, they ping the wallet, which releases a users assets.

## Smart Contracts

On the EVM blockchains, we have an identical architecture. 

The difference here, is that ethereum has slightly more flexibility language wise, than algorand allows, and so we have developed an optimised multi-sig wallet on ethereum, which incorporates governance into the internal methods.

## Governance

When we talk about governance of a bridge, what we mean is that there are only certain validators allowed to sign transactions, and there are only certain tokens allowed to be transfered cross-chain.

These are decided by our governance members, who, in turn, will decide based on factors, such as stable-coin distributor relations, and crypto partnerships.

Of course, governance is entirely done on-chain.
