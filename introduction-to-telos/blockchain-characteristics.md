# Blockchain characteristics

## M**odels of Understanding**

Telos can be described by the following models of understanding:&#x20;

1. A distributed computing model.&#x20;
2. An event sourcing solution.&#x20;
3. A virtual state machine, and A smart contract platform.

#### A distributed computing model&#x20;

Telos as a distributed computing model brings resilience, anti-fragility, censorship resistance and efficiency to the network. Through resilience, Telos prevents technical failure of individual members of the network through the delegate proof of stake block producer model. The Telos network is physically distributed which makes it resistant to censorship.

#### An event sourcing solution&#x20;

Telos has built-in replayability of the state of the system. The current system state can be reconstructed from an event log created by actions initiated by users or smart contracts. This is done through Hyperion which stores a history of event logs and system state snapshots. Telos make provision for system snapshots. These system snapshots are used in the same way accounting firms create a summary of a company's financial statements at the end of a financial year.&#x20;

These “end-of-year” statements act as the new starting point for a company instead of dragging along all the transactions of a previous year. Telos create a system snapshot and use it as their new starting point after a predetermined interval, which helps with network resource management. Furthermore entries recorded to the event log are immutable and cannot be changed. Telos enables command query responsibility separation and allows for read-only and read/write permissions.

#### A virtual state machine&#x20;

Telos, as a virtual state machine, models all applications as a “current state” and “changes to state”. Since Telos makes use of the tEVM, variations in the underlying infrastructure does not undermine the performance of the network (since it is virtual).

#### A smart contract platform

Telos as a smart contract platform makes it easy to update and patch smart contracts. Smart contracts written for Telos (using familiar programming languages like C++) makes it easy to deploy new contracts. Telos compiles C++ code into WebAssembly code (WASM), which is efficient bytecode that can be executed in many different environments. Solidity and Viper based smart contracts need only be redeployed on tEVM to work.

## Telos's defining characteristics

The list of characteristics that define the Telos blockchain network changes over time as the project matures as a result of new circumstances and updated features sets.&#x20;

Currently, some of Telos's defining characteristics include the following:

* [**Worker Proposal System**](https://medium.com/telos-foundation/telos-user-guide-tutorial-worker-proposals-b9b5f422ef08) **(WPS)**: The network allocates a fixed number of TLOS tokens to be awarded to accounts that submit proposals for work to be done to increase the value of the network. Proposals that meet a threshold of votes by TLOS token holders receive their requested funds. Reserves are replenished every month from the Exchange Reserve Fund (per [TEDP](https://medium.com/@goodblock\_info/understanding-the-telos-economic-development-plan-bd42d4666374)), with extra tokens carrying over into the next monthly period. This system currently contributes nothing towards inflation.
* **Sufficient Block Producer (BP) Rewards**: Telos prides itself on properly compensating block producers, who are responsible for providing the backbone of the network. BP's who are voted to the top 21 spots are all compensated evenly, and each of 30 standby BPs are compensated half the amount of a top-21 BP. Although originally set at 1% of total supply per annum, the BP payout is now being sourced from the Exchange Reserve Fund (per [TEDP](https://medium.com/@goodblock\_info/understanding-the-telos-economic-development-plan-bd42d4666374)) at a rate closer to 5% of supply, therefore contributing nothing towards inflation.
* **Initial Token Balance Equity:** Since Telos token balances were initiated based off existing EOS balances (snapshot), this gave the project the opportunity to adjust TLOS balances to level the playing field. Specifically, a maximum of 40,000 initial TLOS tokens per account was enforced, meaning that no account would start off with more than 40,000 TLOS tokens. This was enacted to reduce influence of big token holders ("whales") on the network.
* **Prohibition of Voting by Exchanges**: The custodial nature of online exchanges gives them the ability to stake and vote with users' funds, thereby given themselves untoward influence over the network. On Telos exchanges are prohibited from voting with users' funds, giving them less influence.
* **Block Producer Accountability:** Standby Block Producers are periodically cycled into active block production, giving them a chance to prove that their infrastructure is working correctly. Standby Block Producers who fail this test will be penalized, preventing bad actors from launching poor-performing Block Producer nodes.
