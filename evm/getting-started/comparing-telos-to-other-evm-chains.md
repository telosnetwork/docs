---
description: Why Telos is better than other Ethereum Virtual Machine (EVM) chains
---

# Benefits of Telos

Telos is highly free of conflict of interest due to wide token distribution. This makes it a good candidate for co-operation among large and small cryptocurrency ecosystem actors. Furthermore, centralization increases regulatory risk by a government take down, and the risk of founders abandoning the project. Telos builds innovation on top of a Delegated Proof of Stake (DPoS) consensus mechanism. This mechanism is based on source code originally from Block.one's EOS blockchain. Their unique selling points include maturity, decentralization of stakeholders and validators, and a proven on-chain governance model.

In this document, a comparison between Telos and its EVM implementation and a few other well-known EVM chains are presented. One of Telos distinguishing features include the use of native WebAssembly based smart contracts, but in this section our focus will be on other aspects that make Telos EVM an appealing blockchain to deploy your Solidity/Vyper decentralized application.

## Maturity

Telos has been continuously operating since 2018, illustrating the robustness of the underlying technology stack and block producer community.

| Blockchain          | Continuously operating since | Blocks produced                                |
| ------------------- | ---------------------------- | ---------------------------------------------- |
| Telos               | 2018                         | >[145M](https://telos.bloks.io)                |
| Ethereum            | 2015                         | [12M](https://etherscan.io)                    |
| Binance Smart Chain | 2020                         | [6M](https://bscscan.com)                      |
| Polygon             | 2021                         | [12M](https://explorer-mainnet.maticvigil.com) |

* The number of blocks produced are based on the available information at the time of writing this document.

## Decentralization

Telos is a fair-distribution chain. The original TLOS token distribution was made as wide as possible to ensure that Telos blockchain stays conflict-free and a community-led effort.[ More information about the fair distribution model can be found in the original Telos Whitepaper.](https://drive.google.com/file/d/1WpBUD9xWaaTk8X9t73uShgsCUfH\_-3cJ/view)

![How the Telos genesis block was formed from EOS genesis block by doing a haircut on whale investors](<../../.gitbook/assets/image (7).png>)

Top 10 accounts own % of tokens

A review of the top 30 individually-owned accounts on Telos (April 2, 2021), excluding chain- and exchange-owned acounts, reveals that the top accounts comprise <15% of the total current token-supply of the chain.

Telos token holders can be found [on TELOSTRACKER](https://telostracker.io/topHolders). Telos has a maximum supply cap. The current Telos inflation parameters can be changed by TLOS token holders through governance, but the maximum supply cap cannot be changed. Currently Telos has no inflation set. TLOS ERC-20 token accounts were not considered in the top 30.

Ethereum token holders can be found on [EtherScan](https://etherscan.io/accounts). Ethereum has no supply cap currently and the maximum supply cap is based on the current supply.

[Matic token holders were taken from EtherScan](https://etherscan.io/token/0x7d1afa7b718fb893db30a3abc0cfc608aacfebb0#balances). No data analysis was done for Polygon network addresses.

[BNB token holders were taken from EtherScan](https://etherscan.io/token/0xB8c77482e45F1F44dE1745F52C74426C631bDD52#balances). No data analysis was done for Binance Chain or Binance Smart Chain.



Telos does not have minimum staking requirements for a block producer. The new block producers must accept the[ Regproducer Ricardian Contract](https://tbnoa.org/details.html?docid=4) and successfully run on a testnet for one week in addition to other minimum requirements (see the[ Telos Block Producer Minimum Requirements Document](https://tbnoa.org/details.html?docid=1)). These contracts also forbid collusion or using custodial TLOS tokens to participate in voting as well as dictating minimul levels of infrastructure that a block producer must operate. Block producers watch each other for misbehavior and can intervene based on the terms stipulated in the contracts.

Observers, hired through the Telos Works work proposal and payment system, can also identify violation of rules and propose remedies in the form of multi-signiture contracts for the block producers to execute.

For any block producer motion to propagate, 15 of the 21 block producers in the current schedule must vote in favor of the multi-signature transaction, which may then be executed by any Telos account to complete the action.

The on-chain governance allows any holder of staked TLOS tokens (staked for CPU, NET or REX) to vote for block producers with the rank determined by the stake-weighted voting of all voters.

| Blockchain          | Active block producers                                                                                       | Total block producers | Cost of becoming a block producer                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------- | ------------------------------------------------------------------------------------ |
| Telos               | 21 (+21 standby)                                                                                             | ≥50                   | No minimum stake                                                                     |
| Ethereum            | [Top 4 mining pools control 60% of hashing power](https://etherscan.io/stat/miner?range=7\&blocktype=blocks) | -                     | The capital cost of becoming a proof of work miner is in tens of millions of dollars |
| Binance Smart Chain | 21                                                                                                           | ?                     | [\~250,000 BNB](https://bscscan.com/validators#)                                     |
| Polygon             | ?                                                                                                            | ?                     | ?                                                                                    |

Data about Polygon block producers and auction prices to become a block producer could not [be found in Polygon documentation](https://docs.matic.network), at the time of writing this document.



