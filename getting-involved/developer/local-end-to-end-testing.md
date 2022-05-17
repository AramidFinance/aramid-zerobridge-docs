# Overview

> The goal here is to develop a walkthrough so that new devs at aramid can build the entire system for 'local' testing

## Environment SetUp

- As a blockchain app developer, you need some basics

> You need a way to interact with your chosen network: a wallet, and it's credentials will allow for this

> You will need a blockchain network node to connect to, to make network interactions with smart contracts. While it is possible to run your own, the reality is that it requires huge amounts of storage, and is not a way to develop quickly. Instead you will use a IAAS (infrastructure as a service) provider to do this, such as purestake or infura

> You will need a good dev environment. If you are not running a `UNIX based OS`, then [WSL](https://docs.microsoft.com/en-us/windows/wsl/setup/environment) is your best bet. If you dont know what a UNIX based OS is, then WSL is your best bet

- For the bridge specifically, these are your first port of call

> You will need access to 3 ethereum accounts, and 3 algorand accounts, you can create these using [metamask](https://metamask.io/) and [purestake](https://www.purestake.com/technology/algosigner/). Note down the `private keys and mneumonics`. 

> You will need to fund these accounts with testnet Ether, Matic and Algo, using the relevant faucets: `e.g.` [rinkeby testnet faucet](https://rinkebyfaucet.com/), [matic faucet](https://faucet.polygon.technology/) or [algorand testnet faucet](https://testnet.algoexplorer.io/dispenser)

> You will need access to 3 ethereum testnet endpoints, and 6 algorand testnet endpoints (3 for `indexer` and 3 for `algod`). For this it is recommended to get familiar with [infura](https://infura.io/) or [alchemy](https://www.alchemy.com/), and again [purestake](https://developer.purestake.io/), or [tatum](https://dashboard.tatum.io/)

> > All of the above can be done programatically, if you want, but we will not go into it here

> > > what follows is in dev still

# The following should be done in this order! (access open on main-net launch)

## Ethereum Asset Creation and Contract Deployment and Governance

> install, and follow readme

```
git clone git@github.com:AramidFinance/bridge-ethereum-assets.git
git checkout localTesting
```

## Algorand Asset Creation and Contract Deployment and Governance

> install, and follow readme

```
git clone git@github.com:AramidFinance/bridge-algorand-assets.git
git checkout localTesting
```

## Soldier Node Initialisation and Monitoring 

> install, and follow readme

```
git clone git@github.com:AramidFinance/bridge-soldier-nodejs-app.git
git checkout localTesting
```
