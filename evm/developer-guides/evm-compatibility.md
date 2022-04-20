# EVM Compatibility

## Overview

The tEVM is generally compatible with any smart contract written in Solidity. Care must be taken to validate throughout the smart contract development life cycle that the contract is functioning as expected. It is always recommended to thoroughly test any contract on the Telos testnet before deploying to the Telos mainnet.

## Solidity Versions

Due to the nature of the Telos EVM's implementation, certain versions of Solidity may not always be supported. Currently all versions should be supported, but version > 0.7.0 is recommended.

## Supported EIPs

As verified by [Sentnl's Audit](https://s3.eu-central-1.wasabisys.com/audit-certificates/Smart%20Contract%20Audit%20Certificate%20-%20Telos%20EVM.pdf) all gas values are consistent with gETH. Explicit effort was made to align the tEVM with EIP-2929 in order to conform with Gas costs. In addition with the Audit verification all [Open-Zeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts) tests have been run ensuring EVM compatibility.

## RPC methods

Currently supported JSON RPC methods:

```
rpc_modules

net_listening
net_version
parity_pendingTransactions // No-op

web3_clientVersion

eth_blockNumber
eth_chainId
eth_accounts
eth_getTransactionCount
eth_getCode
eth_getStorageAt
eth_estimateGas
eth_gasPrice
eth_getBalance
eth_getBalanceHuman // custom, returns the float balance instead of wei
eth_call
eth_sendRawTransaction
eth_sendTransaction
eth_getTransactionReceipt
eth_getTransactionByHash
eth_getBlockByNumber
eth_getBlockByHash
eth_getBlockTransactionCountByHash
eth_getBlockTransactionCountByNumber
eth_getUncleCountByBlockHash
eth_getUncleCountByBlockNumber
eth_getLogs

// trace APIs only support the 'trace' type and not 'vmTrace' or 'stateDiff'
trace_filter
trace_transaction
trace_replayTransaction
trace_replayBlockTransactions
trace_block
trace_get
```

For more on EVM compatibility, click [here](https://help.telos.net/evm/how-to-verify-a-contract-on-telos-evm?from\_search=86541452).
