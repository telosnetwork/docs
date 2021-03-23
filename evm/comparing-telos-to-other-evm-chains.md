---
description: Why Telos is better than other Ethereum Virtual Machine (EVM) chains
---

# Benefits of Telos compared to EVM chains

Telos is a Delegated Proof of Stake \(DPoS\) blockchain based on the source code originally from the EOS blockchain. 

### Maturity

Telos has been continuously operating for three years, showing the robustness of the underlying tech stack and block producer community. 

| Blockchain | Continuously operating since | Blocks produced |
| :--- | :--- | :--- |
| Telos | 2019 | [143M](https://telos.bloks.io/) |
| Ethereum | 2015 | 1[2M](https://etherscan.io/) |
| Binance Smart Chain | 2020 | [6M](https://bscscan.com/) |
| Polygon | 2021 | [12M](https://explorer-mainnet.maticvigil.com/) |

The number of blocks produced was snapshotted as the writing of the content from the respective block explorers.

### Decentralisation

Telos is a fair distribution chain. The original TLOS token distribution was made as wide as possible to ensure that Telos blockchain stays conflict-free and community-led effort. More information about fair distribution model \[TODO add links\]

Top 10 accounts own % of tokens

| Blockchain | Number of tokens held by the top 30 accounts | % of tokens held by the top 30 accounts | Max supply cap |
| :--- | :--- | :--- | :--- |
| Telos | 300M | 3% | 10B |
| Ethereum | 30M | 26% | - |
| Polygon | 8.8B | 88% | 10B |
| Binance Smart Chain | 15M | 92% | 16.5M |

The comparison above is a rough overview and does not differentiate between special accounts like centralised exchange wallets, reserves and bridges. 

Telos token holders can be found [on TELOSTRACKER](https://telostracker.io/topHolders).  Telos has a maximum supply cap. The current Telos inflation parameters can be changed by TLOS token holders through governance, but the maximum supply cap cannot be changed. TLOS ERC-20 token accounts were not considered.

Ethereum token holders can be found from [EtherScan](https://etherscan.io/accounts). Ethereum has no supply cap currently and the max supply cap is based on the current supply.

[Matic token holders were taken from EtherScan](https://etherscan.io/token/0x7d1afa7b718fb893db30a3abc0cfc608aacfebb0#balances). No data analysis was done for Polygon network addresses.

[BNB token holders were taken from EtherScan](https://etherscan.io/token/0xB8c77482e45F1F44dE1745F52C74426C631bDD52#balances). No data ana was done for Binance Chain or Binance Smart Chain.

### Block production and validators

Telos is based on Delegated Proof of Stake model. There are 21 active block products at the time. There are total X block producers. The block producers are cycled as Y.

| Blockchain | Active block producers | Reserve block producers | Cost of becoming a block producer |
| :--- | :--- | :--- | :--- |
| Telos | 21 | 40 |  |
| Ethereum | [Top 4 mining pools control 60% of hashing power](https://etherscan.io/stat/miner?range=7&blocktype=blocks) | - | The capital cost of becoming a proof of work miner is in tens of millions of dollars |
| Binance Smart Chain | 21 | ? | [~250,000 BNB](https://bscscan.com/validators#) |
| Polygon | ? | ? | ? |

As the writing of this, data about Polygon block producers and auction prices to become one could not [be found in Poylgon documentation](https://docs.matic.network/). 

### Consensus mechanism

Telos and other modern blockchains are not based on proof of work that is energy wasteful way to run a blockchain. [Ethereum has the carbon footprint of Tanzania](https://digiconomist.net/ethereum-energy-consumption/).

| Blockchain | Consensus |
| :--- | :--- |
| Telos | Delegated Proof of Stake \(DPoS\) |
| Ethereum | Proof of Work \(PoW\) |
| Binance Smart Chain | [Parlia](https://docs.binance.org/smart-chain/guides/concepts/consensus.html), inspired by Clique |
| Polygon | [Bor](https://docs.matic.network/docs/contribute/bor/consensus/), inspired by Clique |

### Block time

Block time, and consensus algorithm, affects how fast the transaction is finalised and how interactive decentralised applications can be.

| Blockchain | Block time |
| :--- | :--- |
| Telos | ~500 ms |
| Ethereum | 15 seconds \(plus mempool delay of several minutes\) |
| Binance Smart Chain |  |
| Polygon | [2.2 seconds](https://explorer-mainnet.maticvigil.com/) |

### Transaction throughput

TODO

TODO

### EVM compatibility

TODO

### Governance

Telos has an on-chain governance. Telos token holders can vote on proposals through SQRL wallet. There are XXX passed proposals. The most important proposal that passed was YYY.

### Conflict of interest and regulatory choke points

As explained in the decentralisation paragraph above, Telos is highly free of conflict of interest due to wide token distribution. This makes it a good candidate for co-operation among large and small cryptocurrency ecosystem actors. Furthermore, centralisation increases regulatory risk and risk of founders giving up on the project.

| Blockchain | Conflict of interest issues |
| :--- | :--- |
| Telos | No conflict |
| Ethereum | No conflict, except if you have your own chain \(Binance\) |
| Binance Smart Chain | Conflict of interest for any centralised exchange to integrate with |
| Polygon | Highly centralised and depends on the Polygon founders |

### Scaleability and state bloat

Blockchains have an issue [with state bloat](https://blocking.net/1417/blockchain-state-explosion-dilemma-hard-core-series/). If there is no way to reduce the cumulative state of all past transactions, the blockchain state grows out of the capabilities of commodity hardware. This, in turn, will increase the capital cost of running a node and leads to more centralisation.

Below is how different chains tackle the state bloat at the moment.

| Blockchain | State management model |
| :--- | :--- |
| Telos | State rent \(does not apply to EVM yet\) |
| Ethereum  | No approved proposals |
| Polygon | No approved proposals |
| Binance Smart Chain | No approved proposals |

### Frontrunning protection

Frontrunning is a situation where miners or bots trade against your transaction causing monetary loss to you. Especially miners on Ethereum mainnet are suspectible for this. This may cause millions of dollars of losses for decentralised application users. 

Telos has binding rules for block producers. Any block producer that is caught manipulation can be blacklisted through on-chain governance. The fast block speed makes it less likely anyone can frontrun transactions in a public mempool.

| Blockchain | Frontrunning situation |
| :--- | :--- |
| Ethereum | Very bad - multiple existing frontrun bots |
| Telos | Prevented through governance |
| Binance Smart Chain | No mitigation against frontrunning |
| Polygon | No mitigation against frontrunning |
| Secret Network | Prevented through private transactions |

### Arbitration

TODO





