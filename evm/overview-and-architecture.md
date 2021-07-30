---
description: >-
  How EVM on Telos is structured and how it is related to the underlying Telos
  blockchain
---

# Overview and architecture

### Classical Ethereum setup

To understand how EVM works on Telos, we need to first look at how EVM based DApps usually work.

Below is an example of a classical EVM decentralised app design. Both DApp and user wallet connects to an Ethereum node that provides API services over JSON-RPC protocol. Ethereum node manages the state \(accounts and balances\) and logs \(queries of happened events\) for its API user in internal databases.

![](../.gitbook/assets/telos.png)

EVM has two different state databases

* **State** that is the current network state accessible to the smart contracts. Smart contracts can update and read these.
* **Logs** that are the past Solidity events. It is mainly used for token transfers, centralised exchange integration and DApp transaction histories. Smart contracts cannot access logs.

DApps communicate with the user wallet over [in-browser ](https://docs.metamask.io/guide/ethereum-provider.html)or [WalletConnect](https://walletconnect.org/) protocols. Both user wallet and DApps communicate with Ethereum JSON-RPC API to get the blockchain state and logs.

### Telos EVM design

EVM is implemented on Telos as a smart contract: all activities that would normally be run by the EVM on an Ethereum node are run by a smart contract on the Telos chain. An Ethereum compatibility JSON-RPC server provides the API Ethereum applications are expecting. It does this by translating the native Telos state from the EVM smart contract to Ethereum expected format.

![](../.gitbook/assets/telos-telos-evm-design.png)

There are some main differences

* Because the EVM is just another smart contract on the Telos chain, there can exist multiple EVMs on the same chain at the same time. They are differentiated by their Telos account name. 
* Telos does not have the concept of logs. Whereas Ethereum nodes provide the built-in eth\_getLogs call to query logs, Telos has logs query/streaming and history management as an external service called [Hyperion](https://eosrio.io/hyperion/).
* EVM transactions need to be able to pay native TLOS fees for transactions. This bit is managed by the Ethereum compatibility JSON-RPC server that has a native Telos account associated with it. This account is used for broadcasting transactions to the EVM contract.  Read more about gas fees [here](gas-fees.md).
* EVM smart contract uses native TLOS token as gas instead of ETH.

### Other similar projects

A similar approach is followed by the [Near blockchain](https://github.com/aurora-is-near/aurora-engine) to construct an EVM from smart contracts.

