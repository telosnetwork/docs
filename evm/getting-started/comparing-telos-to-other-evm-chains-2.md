---
description: Why Telos is leading the race against other chains
---

# On-chain Governance and other advance features

## Introduction

Dive into the inner workings of Telos' Network governance documentation. Governance is a huge strength to the Telos network. Powered by the [Telos Decide](https://docs.telos.net/developers/telos\_contracts/telos-decide) engine, Telos' governance structure puts network operations in the hands of token holders.

For a full list of Telos on-chain governance documentation, please visit [telos.net/governance](https://www.telos.net/governance).&#x20;

## Governance

Telos has a very advanced on-chain governance model. TLOS holders can participate in governance. Besides choosing the block producers, TLOS holders can draft and vote on proposals. The most common proposals include using Telos treasury to fund initiatives around the Telos ecosystem.

The underlying Telos blockchain rules are defined in [the system contracts](https://github.com/telosnetwork/telos.contracts), a smart contract suite defining the core of Telos network. Any change to the system contracts must go through code review, block producer acceptance and governance acceptance (vetoable). Telos Core Developers working on the system contract are chain-funded and can be paid or dismissed based on community voting. Additionally, Telos token holders are less concentrated than many similar chains.

Telos does not have whales and therefore block producers need only convince the broad collective of TLOS token holders of their strong candidacy. Additionally, Telos block producer voting is "inverse weighted" meaning that if you only vote for one or two block producers your votes have less weight than if you vote for 30. This encourages the majority of Telos members to become more educated about block producer candidates and discourages those who seek to vote only for themselves and their affiliates.

Telos maintains minimum standards for block producers to be eligible candidates. These standards are based on security, server capacity, information disclosure, and participation in the public and private testnet. Block producers are required to run two weeks without error on the testnet before going to the mainnet.

These standards will be enforced by smart contract from the time of mainnet activation and any block producer candidate that is not in compliant compliance will not be capable of serving, regardless of votes. All other block producer candidates will automatically rise up the block producer ranks to fill in until the minimum requirements are met.

Below is an example of active ballots being voted on. TLOS holder can review each of these proposal and subsequently vote on them.

![](<../../.gitbook/assets/image (9).png>)

The most important proposals are setting the blockchain fees. Currently, there are no fees on TLOS native transactions. The table provides a summary of four mainstream blockchains with its respective governance model.

| Blockchain          | Governance model                                                                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Telos               | On-chain token-holder voting                                                                                                                                 |
| Ethereum            | [Mixed model developer anarchy and miner wars](https://www.coindesk.com/ethermine-adds-front-running-software-to-help-miners-offset-eip-1559-revenue-losses) |
| Binance Smart Chain | Binance dictatorship                                                                                                                                         |
| Polygon             | Polygon team dictatorship                                                                                                                                    |

## Conflict of interests

As mentioned in the [decentralization](comparing-telos-to-other-evm-chains-2.md#decentralization)

| Blockchain          | Conflict of interest issues                                          |
| ------------------- | -------------------------------------------------------------------- |
| Telos               | No conflict due to fair distribution and neutral foundation          |
| Ethereum            | No conflict, except if you have your own competing chain (Binance)   |
| Binance Smart Chain | Any centralized exchange has a conflict of interest to integrate BSC |
| Polygon             | Highly centralized and depends on the Polygon founders               |

## Scalability and state bloat

Blockchains have an issue [with state bloat](https://blocking.net/1417/blockchain-state-explosion-dilemma-hard-core-series/). If there is no way to reduce the cumulative state of all past transactions, the blockchain state grows out of the capabilities of commodity hardware. This in turn will increase the capital cost of running a node and leads to more centralization.

Below is a summary of different blockchains' approach towards state bloat at the moment. Native Telos transactions use a resource rent model where different resources (CPU, network, storage) are priced separately and can be exchanged or rented.\
\
Storage on Telos (often described as RAM) has a cost, which is set via AMM type system (using Bancor algorithm). The total amount of data stored on chain gives the size of the state. If a smart contract removes data from state, the RAM asset is returned to it's original owner (the account which paid for the storage being recovered), the state size shrinks and that account can then sell the RAM back to the system if it wishes. Via this mechanism, responsible usage of storage is maintained.

Beyond state, the full blockchain history is also a necessary component of the overall blockchain functionality and can be scaled horizontally across a cluster of commodity hardware. The [Hyperion](https://github.com/eosrio/hyperion-history-api) history solution addresses this for both Telos and the tEVM using elastic search and is ran by many Telos validator nodes around the world.

| Blockchain          | State management model                                                                                                                                  |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Telos               | [Resource exchange model (REX)](https://medium.com/telos-foundation/telos-users-guide-understanding-telos-rex-d94d081cd7bb) (does not apply to EVM yet) |
| Ethereum            | No approved proposals                                                                                                                                   |
| Binance Smart Chain | No approved proposals                                                                                                                                   |
| Polygon             | No approved proposals                                                                                                                                   |

## Frontrunning protection

Frontrunning is a situation where miners or bots do a high-frequency trade against the transaction of a genuine buyer causing monetary loss to the buyer. Sandwich Trading is a common form of frontrunning on swap pools that consists of viewing a pending transaction in the mempool and issuing another transaction, buying a large amount of the same transaction to increase the price prior to the genuine buyer's transaction execution followed by a sale afterwards.

The net effect is that value is drawn from the genuine buyer. Frontrunning is accomplished either by bots scouring the mempool for transactions and issuing competing trades with much higher gas fees, or more insidiously, with the participation of miners on the Ethereum mainnet who perform the frontrunning with or paid by the bot operators. This may cause millions of dollars of losses for dapp users.

Telos has binding rules for block producers, as described earlier. Any block producer that is caught manipulating transaction order can be blacklisted through on-chain governance. The fast block speed makes it less likely anyone can frontrun transactions in a public mempool. Telos native, and more importantly Telos EVM, have [fixed transaction costs](../about-ethereum-virtual-machine/gas-fees.md). Unlike other systems there is no opportunity for one account to pay a higher fee/gas price to get their transaction processed sooner than another user's transaction. As a result, frontrunning is functionally eliminated from Telos and Telos EVM transactions.

| Blockchain          | Frontrunning situation                                                                                                                   |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Telos               | Prevented through governance                                                                                                             |
| Ethereum            | High incidence - [multiple existing frontrun bots](https://www.theblockcrypto.com/genesis/79937/a-case-study-in-miner-extractable-value) |
| Binance Smart Chain | No mitigation against frontrunning                                                                                                       |
| Polygon             | No mitigation against frontrunning                                                                                                       |
| Secret Network      | [Mitigated through private transactions](https://scrt.network/blog/secretswap-is-live-on-mainnet)                                        |

## Arbitration

Telos has an arbitration process through a body called Telos Arbitration Organization (TAO). There exist a board of arbitrators, elected members voted through TLOS governance. They act independently from block producers. The arbitrators can get involved in dispute cases between Telos users, block producers and deployed smart contracts. [More information about the arbitration process and arbitrators in Telos whitepaper](https://telos.net/wp-content/uploads/2021/02/Telos-Whitepaper-master-20180717.pdf).

Telos arbitration process has not yet been invoked but is planned for implementation by the end of 2021 or in any case where it proves critical to the network operations. The most common expected case of the invocation would be a large scale hack or a system failure. Eventually, Telos Arbitration will offer broad conflict resolution services on the Telos blockchain.

To read more about Telos on-chain governance, click [here](https://www.telos.net/governance).
