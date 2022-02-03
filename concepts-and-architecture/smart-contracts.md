# Smart Contracts

<mark style="color:red;">List networks and respective smart contract</mark>

## Current implimentation

The on-chain component of zero bridge consists of two parts.

### Ethereum contracts

To use an ERC20 token for bridging assets, it must be whitelisted by the bridge.

For your address to be a accepted as a validator, it must be whitelisted by the bridge.

The core of the bridge is the `releaseTokens` method. It's sole purpose is to decide whether or not to release tokens held by the bridge.

In `releaseTokens`, we expect to get a validator encoded array of bytes submitted to the bridge, along with corresponding transaction parameters. The array of bytes is decoded and is compared to the transaction parameters. Along with this, the decoded array of bytes is checked for uniqueness against the list of confirmed validators. 

If all decoded addresses are unique, and there are enough of them (> bridge defined threshold), and they match with the proposed transaction parameters, and the transaction is new, only then do we release assets.

### Algorand Multi-sig wallet

On the Algorand blockchain, the zero bridge treasury behaviour is defined by the [multi-signature wallet](https://developer.algorand.org/docs/get-details/accounts/create/?from_query=multisig#multisignature) who minted our ASA. 

This wallet is the custodian for the zero-bridge token, and can only be accessed by the validator nodes in unison.

The behaviour of the validator network in described in the later section.
