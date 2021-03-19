---
description: >-
  How EVM on Telos is structured and how it is related to the underlying EOS
  blockchain
---

# Overview and architecture

### Classical Ethereum setup

To understand how EVM works on Telos, we need to first look at how EVM based Dapps usually work.

Below is an example of a classical EVM decentralised app design. Both DApp and user wallet connects to an Ethereum node that provides API services over JSON-RPC protocol. Ethereum node manages the state \(accounts and balances\) and logs \(queries of happened events\) for its API user in internal databases.

![](../.gitbook/assets/telos.png)

EVM has two different state databases

* **State** that is the current network state accessible to the smart contracts. Smart contracts can update and read theese.
* **Logs** that are are the past Solidity events, mainly used for token transfer, centralised exchange integration and DApp transaction histories. Smart contracts cannot access logs.

Dapp communicates with the user wallet over [in-browser ](https://docs.metamask.io/guide/ethereum-provider.html)or [WalletConnect](https://walletconnect.org/) protocol. Both user wallet and Dapp communicate with Ethereum JSON-RPC API to get the blockchain state and logs.

### Telos EVM design

EVM is implemented on Telos as a smart contract: all activities that would normally be run by the EVM virtual machine component on an Ethereum node are run by a smart contract on the Telos chain. An Ethereum compatibility JSON-RPC server provides the API Ethereum applications are expecting. It does this by translating the native EOS state from the EVM smart contract to Ethereum expected format.

![](../.gitbook/assets/telos-telos-evm-design.png)

There are some main differences

* Because the EVM is just another smart contract on the Telos chain, there can exist multiple EVMs on the same chain at the same time. They are differentiated by their EOS account name. 
* EOS does not have the concept of logs. Whereas Ethereum nodes provide the built-in eth\_getLogs call to query logs, Telos have logs query and history management as an external service called [Hyperion](https://eosrio.io/hyperion/).
* EVM transactions need to be able to pay native EOS fees for transactions. This bit is managed by the Ethereum compatibility JSON-RPC server that has a native EOS account associated with it. This account is used for broadcasting transactions and the EVM contract credits the spent gas to this account at the end of the transaction.
* EVM smart contract uses native TLOS token as a gas instead of ETH.

### Other similar projects

A similar EVM as a smart contract approach is also by [the Near blockchain](https://github.com/near/near-evm).

