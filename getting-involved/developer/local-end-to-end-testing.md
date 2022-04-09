# Overview (WIP)

- The goal here is to develop a walkthrough so that new devs at aramid can build the entire system for 'local' testing

## Environment SetUp

- As a blockchain developer, you need some basics

1. You need a way to interact with your chosen network: a wallet, and it's credentials will allow for this
2. You will need a node to connect to. While it is possible to run your own, the reality is that it requires huge amounts of storage, and is not a way to develop quickly. Instead you will use a IAAS (infrastructure as a service) provider to do this, such as purestake or infura
3. You will need a good dev environment. If you are not running a UNIX based OS, then WSL is your best bet

- For the bridge specifically, these are your first port of call

> You will need access to 3 ethereum accounts, and 3 algorand accounts, you can create these using [metamask](https://metamask.io/) and [purestake](https://www.purestake.com/technology/algosigner/). Note down the `private keys and mneumonics`

> You will need to fund these accounts with testnet Ether and Algo, using the relevant faucets: `e.g.` [rinkeby testnet faucet](https://rinkebyfaucet.com/) or [algorand testnet faucet](https://testnet.algoexplorer.io/dispenser)

> You will need access to 3 ethereum testnet endpoints, and 6 algorand testnet endpoints (3 for `indexer` and 3 for `algod`): `we will provide some, but it is recommended that you create your own`

## Ethereum Contract Deployment

> install

```
git@github.com:AramidFinance/bridge-ethereum-smart-contracts.git
```


## Algorand Asset Creation

> install

```
git@github.com:AramidFinance/bridge-algorand-assets.git
```

## Soldier Node Initialisation and Monitoring

> install

```
git clone git@github.com:AramidFinance/bridge-soldier-nodejs-app.git
```

## System Interaction 

```
```
