---
description: Why Telos is better than other Ethereum Virtual Machine (EVM) chains
---

# Benefits of Telos compared to EVM chains

Telos builds innovation on top of a Delegated Proof of Stake \(DPoS\) blockchain based on source code originally from Block.one's EOS blockchain. Unique selling points include maturity, decentralization of stakeholders and validators and a proven on-chain governance model.

In this document, we compare Telos and its EVM implementation to a few well-known EVM chains. Telos has native WebAssembly based smart contracts, but this documentation will focus on aspects that make Telos EVM an appealing blockchain to deploy your Solidity/Vyper decentralised application.

## Maturity

Telos has been continuously operating since 2018, showing the robustness of the underlying tech stack and block producer community.

| Blockchain | Continuously operating since | Blocks produced |
| :--- | :--- | :--- |
| Telos | 2018 | [145M](https://telos.bloks.io/) |
| Ethereum | 2015 | 1[2M](https://etherscan.io/) |
| Binance Smart Chain | 2020 | [6M](https://bscscan.com/) |
| Polygon | 2021 | [12M](https://explorer-mainnet.maticvigil.com/) |

The number of blocks produced was snapshotted as the writing of the content from the respective block explorers.

## Decentralization

Telos is a fair-distribution chain. The original TLOS token distribution was made as wide as possible to ensure that Telos blockchain stays conflict-free and community-led effort. [More information about the fair distribution model is in the original Telos whitepaper](https://telos.net/wp-content/uploads/2021/02/Telos-Whitepaper-master-20180717.pdf).

![How the Telos genesis block was formed from EOS genesis block by doing a haircut on whale investors](../.gitbook/assets/image%20%282%29.png)

Top 10 accounts own % of tokens

| Blockchain | Number of tokens held by the top 30 accounts | % of tokens held by the top 30 accounts | Max supply cap |
| :--- | :--- | :--- | :--- |
| Telos | 300M | 3% | 355M |
| Ethereum | 30M | 26% | - |
| Polygon | 8.8B | 88% | 10B |
| Binance Smart Chain | 15M | 92% | 16.5M |

The comparison above is a rough overview and does not differentiate between special accounts like centralised exchange wallets, reserves and bridges. A review of the top 30 individually-owned accounts on Telos \(April 2, 2021\), excluding chain- and exchange-owned acounts, reveals that the top accounts comprise &lt;15% of the total current token-supply of the chain.

Telos token holders can be found [on TELOSTRACKER](https://telostracker.io/topHolders). Telos has a maximum supply cap. The current Telos inflation parameters can be changed by TLOS token holders through governance, but the maximum supply cap cannot be changed. Currently Telos has no inflation set. TLOS ERC-20 token accounts were not considered in the top 30.

Ethereum token holders can be found from [EtherScan](https://etherscan.io/accounts). Ethereum has no supply cap currently and the max supply cap is based on the current supply.

[Matic token holders were taken from EtherScan](https://etherscan.io/token/0x7d1afa7b718fb893db30a3abc0cfc608aacfebb0#balances). No data analysis was done for Polygon network addresses.

[BNB token holders were taken from EtherScan](https://etherscan.io/token/0xB8c77482e45F1F44dE1745F52C74426C631bDD52#balances). No data analysis was done for Binance Chain or Binance Smart Chain.

## Block production and validation

Telos is based on EOSIO's Delegated Proof of Stake model. There are 21 active block producers at a time. An additional 21 block producers serve as standbys that are continually tested for readiness by regularly rotating one standby block producer into active production. Any Telos block producers that misses 15% of blocks in any schedule is kicked and the 22nd rank block producer is elevated from standby to active. In this way network resilience is maintained. [There are total of over 50 block producers](https://telos.bloks.io/). The reserve block producers are [cycled as described in the Telos whitepaper](https://telos.net/wp-content/uploads/2021/02/Telos-Whitepaper-master-20180717.pdf). The block producers are ranked and accepted by TLOS holder voting.

![](../.gitbook/assets/image%20%289%29.png)

Telos does not have minimum staking requirements for a block producer. The new block producers must accept the[ Regproducer Ricardian Contract](https://tbnoa.org/details.html?docid=4) and successfully run on a testnet for one week in addition to other minimum requirements [ Telos Block Producer Minimum Requirements Document](https://tbnoa.org/details.html?docid=1). These contracts also forbid collusion or using custodial TLOS tokens to participate in voting as well as dictating minimul levels of infrastructure that a block producer must operate. Block producers watch each other for misbehavior and can intervene based on the terms of these contracts. Observers hired through the chain's Telos Works work proposal and payment system can also identify violations of rules and propose remedies in the form of multi-sig contracts for the block producers to execute. \(For any block producer motion to carry, 15 of the 21 block producers in the current schedule must vote in favor of the multi-signature transaction which may then be executed by any Telos account to complete the action. The on-chain governance allows any holder of staked TLOS tokens \(staked for CPU, NET or REX\) to vote for block producers with the rank determined by the stake-weighted voting of all voters.

| Blockchain | Active block producers | Total block producers | Cost of becoming a block producer |
| :--- | :--- | :--- | :--- |
| Telos | 21 \(+21 standby\) | ≥50 | No minimum stake |
| Ethereum | [Top 4 mining pools control 60% of hashing power](https://etherscan.io/stat/miner?range=7&blocktype=blocks) | - | The capital cost of becoming a proof of work miner is in tens of millions of dollars |
| Binance Smart Chain | 21 | ? | [~250,000 BNB](https://bscscan.com/validators#) |
| Polygon | ? | ? | ? |

As the writing of this, data about Polygon block producers and auction prices to become one could not [be found in Polygon documentation](https://docs.matic.network/).

## Consensus mechanism

Telos and other modern blockchains are not based on proof of work that is an energy wasteful way to run a blockchain. [Ethereum has the carbon footprint of Tanzania](https://digiconomist.net/ethereum-energy-consumption/).

| Blockchain | Consensus |
| :--- | :--- |
| Telos | Delegated Proof of Stake \(DPoS\) |
| Ethereum | Proof of Work \(PoW\) |
| Binance Smart Chain | Proof of Authority \(PoA\) [Parlia](https://docs.binance.org/smart-chain/guides/concepts/consensus.html), inspired by Clique |
| Polygon | Proof of Authority \(PoA\) [Bor](https://docs.matic.network/docs/contribute/bor/consensus/), inspired by Clique |

## Block time

Block time, and consensus algorithm, affects how fast the transaction is finalised and how interactive decentralised applications can be.

| Blockchain | Block time |
| :--- | :--- |
| Telos | [500 ms](https://en.wikipedia.org/wiki/EOS.IO) / 2 txs per second |
| Ethereum | 12-15 seconds \(plus mempool and miner pick up delay of several minutes\) |
| Binance Smart Chain | [3.0-5.0 seconds](https://www.bscscan.com/chart/blocktime) |
| Polygon | [2.2 seconds](https://explorer-mainnet.maticvigil.com/) |

## Fees

Currently, native Telos transactions have no fees. Native Telos fees are set by block producers, voted in by token holders.

EVM transactions will have a fee model similar to [the native Ethereum gas model](https://ethereum.org/en/developers/docs/gas/). The Ethereum account needs to have TLOS token to pay for the transaction. [Telos EVM fees](gas-fees.md) are expected to be &lt; 0.1% of Ethereum gas fees for identical transactions.

| Blockchain | Fee model |
| :--- | :--- |
| Telos | Free on native & minimal on EVM, settable by governance |
| Ethereum | Very high \($30 for a token transfer\) |
| Binance Smart Chain | Dictated by Binance |
| Polygon | ? |

## EVM compatibility

Currently supported JSON RPC methods:

```text
web3_clientVersion
net_listening
eth_blockNumber
net_version
eth_chainId
eth_getTransactionCount
eth_getCode
eth_getStorageAt
eth_estimateGas
eth_gasPrice
eth_getBalance
eth_getBalanceHuman  <-- additional for Telos EVM, human readable balance
eth_call
eth_sendRawTransaction
eth_getTransactionReceipt
eth_getTransactionByHash
eth_getBlockByNumber
eth_getBlockByHash
eth_getBlockTransactionCountByHash
eth_getBlockTransactionCountByNumber
eth_getLogs
trace_filter
trace_transaction
```

## Governance

Telos has very advanced on-chain governance.

TLOS holders can participate in governance. Besides choosing the block producers, TLOS holders can draft and vote on proposals. The most common proposals include using Telos treasury to fund initiatives around the Telos ecosystem.

The underlying Telos blockchain rules are defined in [the system contracts](https://github.com/telosnetwork/telos.contracts), a smart contract suite defining the core of Telos network. Any change to the system contracts must go through code review, block producer acceptance and governance acceptance \(vetoable\). Telos Core Developers working on the system contract are chain-funded and can be paid or dismissed based on community voting. Additionally, Telos token holders are less concentrated than many similar chains.

![](../.gitbook/assets/image%20%284%29.png)

The most important proposals are setting the blockchain fees. Currently, there are no fees on TLOS native transactions.

| Blockchain | Governance model |
| :--- | :--- |
| Telos | On-chain token-holder voting |
| Ethereum | [Mixed model developer anarchy and miner wars](https://www.coindesk.com/ethermine-adds-front-running-software-to-help-miners-offset-eip-1559-revenue-losses) |
| Binance Smart Chain | Binance dictatorship |
| Polygon | Polygon team dictatorship |

## Conflict of interests

As explained in the decentralization paragraph above, Telos is highly free of conflict of interest due to wide token distribution. This makes it a good candidate for co-operation among large and small cryptocurrency ecosystem actors. Furthermore, centralisation increases regulatory risk, by a government takedown, and the risk of founders giving up on the project.

| Blockchain | Conflict of interest issues |
| :--- | :--- |
| Telos | No conflict due to fair distribution and neutral foundation |
| Ethereum | No conflict, except if you have your own competing chain \(Binance\) |
| Binance Smart Chain | Any centralized exchange has a conflict of interest to integrate BSC |
| Polygon | Highly centralized and depends on the Polygon founders |

## Scalability and state bloat

Blockchains have an issue [with state bloat](https://blocking.net/1417/blockchain-state-explosion-dilemma-hard-core-series/). If there is no way to reduce the cumulative state of all past transactions, the blockchain state grows out of the capabilities of commodity hardware. This, in turn, will increase the capital cost of running a node and leads to more centralization.

Below is how different chains tackle the state bloat at the moment. Native Telos transactions use a resource rent model where different resources \(CPU, network, storage\) are priced separately and can be exchanged and rented.  
  
Storage on Telos \(often described as RAM\) has a cost which is set via AMM type system \(using Bancor algorithm\).  The total amount of data stored on chain is what gives us the size of state, if a smart contract removes data from state, the RAM asset is returned to it's original owner \(the account which paid for the storage being recovered\), the state size shrinks and that account can then sell the RAM back to the system if it wishes.  Via this mechanism, responsible usage of storage is maintained.  Beyond state, the full blockchain history is also a necessary component of the overall blockchain functionality and can be scaled horizontally across a cluster of commodity hardware.  The [Hyperion](https://github.com/eosrio/hyperion-history-api) history solution addresses this for both Telos and the TelosEVM using elastic search and is ran by many Telos validator nodes around the world.

| Blockchain | State management model |
| :--- | :--- |
| Telos | [Resource exchange model \(REX\)](https://medium.com/telos-foundation/telos-users-guide-understanding-telos-rex-d94d081cd7bb) \(does not apply to EVM yet\) |
| Ethereum | No approved proposals |
| Binance Smart Chain | No approved proposals |
| Polygon | No approved proposals |

## Frontrunning protection

Frontrunning is a situation where miners or bots do a high-frequency trade against the transaction of a genuine buyer causing monetary loss to the buyer. Sandwich Trading is a common form of frontrunning on swap pools that consists of viewing a pending transaction in the mempool and issuing another transaction buying a large amount of the same transaction to increase the price prior to the genuine buyer's transaction execution followed by a sale afterwards. The net effect is that value is drawn from the genuine buyer. Frontrunning is accomplished either by bots scouring the mempool for transactions and issuing competing trades with much higher gas fees or, more insidiously, with the participation of miners on the Ethereum mainnet who perform the frontrunning with or paid by the bot operators. This may cause millions of dollars of losses for decentralized application users.

Telos has binding rules for block producers, as described above. Any block producer that is caught manipulating transaction order can be blacklisted through on-chain governance. The fast block speed makes it less likely anyone can frontrun transactions in a public mempool.  Telos native and more importantly Telos EVM have [fixed transaction costs](gas-fees.md), unlike other systems there is no opportunity for one account to pay a higher fee/gas price to get their transaction processed sooner than another user's transaction.  As a result, frontrunning is functionally eliminated from Telos and Telos EVM transactions.

| Blockchain | Frontrunning situation |
| :--- | :--- |
| Telos | Prevented through governance |
| Ethereum | High incidence - [multiple existing frontrun bots](https://www.theblockcrypto.com/genesis/79937/a-case-study-in-miner-extractable-value) |
| Binance Smart Chain | No mitigation against frontrunning |
| Polygon | No mitigation against frontrunning |
| Secret Network | [Mitigated through private transactions](https://scrt.network/blog/secretswap-is-live-on-mainnet) |

## Arbitration

Telos has an arbitration process through a body called Telos Arbitration Organization \(TAO\). There exist a board of arbitrators, elected members voted through TLOS governance. They act independently from block producers. The arbitrators can get involved in dispute cases between Telos users, block producers and deployed smart contracts. [More information about the arbitration process and arbitrators in Telos whitepaper](https://telos.net/wp-content/uploads/2021/02/Telos-Whitepaper-master-20180717.pdf).

Telos arbitration process has not yet been invoked but is planned for implementation by the end of 2021 or in any case where it proves critical to the network operations. The most common expected case of the invocation would be a large scale hack or a system failure. Eventually, Telos Arbitration will offer broad conflict resolution services on the Telos blockchain.

