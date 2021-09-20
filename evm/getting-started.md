---
description: How to do transactions and deploy smart contracts on the Telos EVM
---

# Developing Smart Contracts on Telos-EVM

This page is intended to jumpstart new Telos EVM users. If you are new to developing on an Ethereum virtual machine, we recommend reading the official [Ethereum docs](https://ethereum.org/en/developers/docs/).

### Connecting Metamask

Telos EVM fully supports [Metamask](https://metamask.io/), a leading wallet for Ethereum based blockchains. In order to interact with the Telos EVM using Metamask, you need to add the network to Metamask. The most convenient way to do this is via [Chainlist](https://chainlist.org/), which curates a list of EVM networks. The Telos EVM mainnet and testnet are listed on Chainlist with chain IDs 40 and 41, respectively. To add a chain to Metamask, connect your wallet and press the "Add To Metamask" button.

![The Telos EVM mainnet and testnet listed on Chainlist.](../.gitbook/assets/image%20%288%29.png)

### Account creation

Once your wallet is connected to the Telos EVM, existing EVM accounts can be used without additional steps. Users are also able to create an EVM account from the Telos side by calling one of the following actions on the eosio.evm contract:

* `create` - Generates a new EVM address given arbitrary data and links it to the provided Telos account.
* `openwallet` - Creates the provided address, without linking it to a Telos account, and fails if it already exists.

A Telos account is required to call these actions. Instructions for creating a Telos account can be found in the [Wallets & Accounts](../users/wallets.md) section. 

### Deposit and withdraw TLOS

The Telos EVM uses native TLOS to pay for gas, so you need TLOS on your EVM account to do transactions. To deposit TLOS to your EVM address, you need to transfer it from a Telos native account. TLOS can be bought through one of the official portals listed on [telos.net](https://telos.net/).

After acquiring TLOS, deposit the funds to an EVM address by transferring the desired amount to the eosio.evm contract with the EVM address as the memo \(starting with "0x" \). If the memo does not follow this format, the funds are transferred to the EVM address associated with the sender's Telos account and if no linked address is found, the transaction fails.

To topup an EVM testnet account, enter the address on the [Telos testnet faucet](https://app.telos.net/testnet/developers) and press the "Send Testnet EVM TLOS" button. 100 TLOS will be sent to that address.

Withdrawals are handled by the `withdraw` action on the eosio.evm contract. Pass your native Telos account name and amount of TLOS to withdraw as parameters. The funds will be withdrawn from your associated EVM address and transferred to your Telos account.

### Telos testnet and mainnet development

Transitioning from other EVMs to the Telos EVM is a seamless experience. You can use any of your favourite tools during development \([Hardhat](https://hardhat.org/getting-started/), [Remix](https://remix.ethereum.org/), [Truffle](https://www.trufflesuite.com/docs/truffle/overview) etc.\) and simply configure the correct network settings when you are ready to deploy. The table below gives the necessary information for the mainnet and testnet.

| Setting | Mainnet | Testnet |
| :--- | :--- | :--- |
| RPC URL |  | [https://testnet.telos.net/evm](https://testnet.telos.net/evm) |
| Chain ID | 40 | 41 |
| Block explorer URL |  | [https://testnet.telos.net/v2/explore](https://testnet.telos.net/v2/explore) |

#### Example

This example demonstrates how to deploy a simple solidity contract on the Telos EVM testnet using Remix. It assumes that you use Metamask and already added the testnet to the list of configured chains. 

1. **Open** [Remix](https://remix.ethereum.org/). An example project with the following structure will be created for you. \(We will only be working with the `1_Storage.sol` contract.\)
2. **Compile** the `1_Storage.sol` contract. Click on the `1_Storage.sol` contract to open it in the editor, navigate to the Solidity compiler __tab and click on the "Compile 1\_Storage.sol" button.
3. **Deploy** the compiled contract. Navigate to the "Deploy & Run Transactions" tab and change the environment to "Injected Web3". Make sure that you selected the Telos EVM testnet in your Metamask and press the "Deploy" button. 

### Local development

_Upcoming content_



