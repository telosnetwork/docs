---
description: How to execute transactions and deploy smart contracts on the Telos EVM
---

# Developing Smart Contracts on Telos EVM

This section is aimed at jumpstarting new Telos EVM (tEVM) users. If you are totally new to developing on an EVM, we recommend reading the official [Ethereum docs](https://ethereum.org/en/developers/docs/) to get started.

### Telos testnet and mainnet development

Transitioning from other EVMs to the Telos EVM is a seamless experience. You can use any of your favorite tools during development ([Hardhat](https://hardhat.org/getting-started/), [Remix](https://remix.ethereum.org), [Truffle](https://www.trufflesuite.com/docs/truffle/overview), etc.) and simply configure the correct network settings when you are ready to deploy. The table below provides the necessary information for the mainnet and testnet.

| **Setting**        | **Mainnet**                                                                  | **Testnet**                                                                  |
| ------------------ | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| RPC URL            | [https://mainnet.telos.net/evm](https://mainnet.telos.net/evm)               | [https://testnet.telos.net/evm](https://testnet.telos.net/evm)               |
| Chain ID           | 40                                                                           | 41                                                                           |
| Block explorer URL | [https://mainnet.telos.net/v2/explore](https://testnet.telos.net/v2/explore) | [https://testnet.telos.net/v2/explore](https://testnet.telos.net/v2/explore) |

{% hint style="warning" %}
Websocket support is coming soon!
{% endhint %}

#### Example contract deployment

This example demonstrates how to deploy a simple Solidity contract on the Telos EVM testnet using Remix.&#x20;

1. [Add the Telos EVM network](../getting-started/creating-an-evm-address.md#connecting-metamask) as a custom RPC network in Metamask.![](<../../.gitbook/assets/image (12).png>)
2. **Open** [Remix](https://remix.ethereum.org). An example project with the following structure will be created for you. (We will only be working with the `1_Storage.sol` contract.)
3.  **Compile** the `1_Storage.sol` contract. Click on the `1_Storage.sol` contract to open it in the editor. Navigate to the Solidity compiler_ _tab and click on the "Compile 1\_Storage.sol" button.

    ![](<../../.gitbook/assets/Selection\_147 (2).png>)
4. **Deploy** the compiled contract. Navigate to the "Deploy & Run Transactions" tab and change the environment to "Injected Web3". Make sure that you have selected the Telos EVM testnet in your Metamask and press the "Deploy" button. A page refresh might be required after enabling Metamask in order to select the "Injected Web3" option. A more in-depth description of how to deploy smart contracts using Remix can be found [here](https://remix-ide.readthedocs.io/en/latest/create\_deploy.html).

![](../../.gitbook/assets/Selection\_148.png)



