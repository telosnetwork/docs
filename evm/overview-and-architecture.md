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

