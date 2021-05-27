---
description: How does gas billing work in the Telos EVM?
---

# Gas fees

### Overview

The general formula for calculating the gas fee is:

$$
gasUsed * gasPrice = gasFee
$$

Telos EVM uses the TLOS token as the native currency, similar to ether \(ETH\) on Ethereum, which means TLOS is used to pay for gas fees.

Transactions will contain 2 gas related values, one is the gas price that the signer of the transaction is willing to pay, and the second is the gas limit which is the most gas they'll approve to be used for the transaction.

### Fee beneficiary

The fees collected as part of EVM gas billing are sent to a fees account as part of every transaction.  These fees will be added back to the network reserve which currently is where validator pay, REX rewards and other funding is sourced from.  This helps bring Telos to a more sustainable tokenomic model.

### RAM as gas

Gas used is based on the number and type of operations \(opcodes\) that are executed as part of the transaction.  The Telos EVM uses the same opcode gas amounts as Ethereum and other EVMs so the gas used will be similar.  
  
The one major difference however is that Telos EVM also charges for native Telos storage \(RAM\) as part of gas used.  Many transactions do not consume any storage, such as transferring a token between two accounts who both already have a balance for the given token, in this case there is already a number stored for both accounts and it's just increasing for one account and decreasing for the other.  But in the event of transferring to an account which does not yet have a balance, a small amount of storage is going to be used that was not used before.  So for example a standard token transfer will still use 21000 gas between two existing accounts, this will be a familiar number for users who transact often.  If that is sent to a new account, it will be 21000 plus the cost of the consumed RAM at that time.  The cost of RAM can be determined in various ways, but is easiest to see on a [block explorer](https://telos.bloks.io/).

### Configurable settings

The Telos validator nodes can configure 2 settings in the Telos EVM smart contract via a multisig transaction requiring 15/21 to approve.  Those settings can be seen at any time on chain via [block explorer](https://telos-test.bloks.io/account/eosio.evm?loadContract=true&tab=Tables&account=eosio.evm&scope=eosio.evm&limit=100&table=config) \(link points at testnet currently, will update with mainnet launch\) or directly querying the [RPC](../eosio-docs/references/nodeos-rpc-api-reference/).

#### Minimum transaction fee

Per the spec of the EVM, TLOS as a native currency in the EVM has 18 decimals of precision however the native TLOS token contract only has 4 decimals of precision.  For this reason, a configurable minimum transaction fee that is measured in 4 decimals is set, if a transaction's gas fee is less than this amount, then the minimum transaction fee will be used.

#### Gas price

The gas price is set in the contract, that is the only price that will ever be charged.  EVM transactions are signed and include a gas price that has been signed for.  That gas price from the transaction is respected, if the transaction has provided a gas price less than the configured gas price, the transaction will fail and no gas will be charged.  If the gas price signed for in the transaction is greater than the configured gas price in the contract, then the configured gas price is used.

Because of this fixed gas price and the inherent FIFO nature of Telos transaction processing, there is no means for [frontrunning](comparing-telos-to-other-evm-chains.md#frontrunning-protection) using a higher gas price than another transaction.

### Native Telos resource costs

As the Telos EVM runs as a smart contract on the Telos native network, there are still the resource costs associated with the Telos native transaction involved with every EVM transaction.  These resource costs are covered by the validator nodes who run the EVM RPC endpoints.  As CPU/NET resources are replenished over a daily average and are not actually "spent", it is only RAM which is a spent cost.  In the case of RAM, the EVM contract itself pays for the RAM and buys it as part of every transaction that uses it, thus constantly maintaining it's RAM supply and paying for it out of gas costs as noted above.

