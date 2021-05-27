---
description: 'This is the roadmap for Telos EVM:'
---

# Roadmap

### Milestone 1: Testnet trials 

This milestone contains some of the first user testable features of Telos EVM.

* Runs on a testnet
* Limited EVM and JSON-RPC compatibility

<table>
  <thead>
    <tr>
      <th style="text-align:left">Task</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">EVM as Telos smart contract</td>
      <td style="text-align:left">Initial work to make EVM smart contract runnable on Telos blockchain</td>
      <td
      style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Ethereum JSON-RPC API compatibility server</td>
      <td style="text-align:left">Initial work for Express.js application that offers Ethereum JSON-RPC
        compatible API to access Telos EVM</td>
      <td style="text-align:left">
        <p>&#x2705;</p>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Architecture documentation</td>
      <td style="text-align:left">Developer documentation how Telos EVM is structured and how it works</td>
      <td
      style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Unique selling point documentation</td>
      <td style="text-align:left">What makes Telos EVM better than other EVM based chains</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">EVM test suite</td>
      <td style="text-align:left">An automated test suite that executes EVM compatibility tests against
        Telos EVM smart contract</td>
      <td style="text-align:left">&#x1F7E1;</td>
    </tr>
    <tr>
      <td style="text-align:left">MetaMask connectivity</td>
      <td style="text-align:left">Users can connect their MetaMask and see token balances</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Developer community chat</td>
      <td style="text-align:left">Public chat for Ethereum focused developers</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">How to connect to the testnet</td>
      <td style="text-align:left">How the developers can connect to a public EVM JSON-RPC endpoint</td>
      <td
      style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">An open-source demo app</td>
      <td style="text-align:left">An ERC-20 token faucet running on testnet EVM</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
    <tr>
      <td style="text-align:left">Testnet token faucet</td>
      <td style="text-align:left">Get EVM TLOS and ERC-20 tokens into your MetaMask</td>
      <td style="text-align:left">&#x2705;</td>
    </tr>
  </tbody>
</table>

### Milestone 2: EVM and JSON-RPC compatibility on testnet

* Runs on a testnet
* Developers can deploy their own Telos EVM instances for local development
* Runs automated test suites of popular EVM projects \(SushiSwap, OpenZeppelin, MakerDAO\)

| Task | Description | Status |
| :--- | :--- | :--- |
| Gas fee price list | Documentation how Telos EVM consumes gas and what developers should expect | ✅ |
| getLogs compatibility | Solve how to make eth\_getLogs API for Telos | ✅ |
| Incompatibility documentation | How Telos EVM differs from Ethereun mainnet EVM | ✅ |
| Developer instance automation | Automated set up and tear down of local Telos EVM test instances | ✅ |
| JSON-RPC test methods | Implementation of time travel, account reset and other test suite specific JSON-RPC methods | 🛑 |
| JSON-RPC test wrapper | Allow running a test suite against Telos EVM from popular Solidity development frameworks like Truffle, Hardhat and OpenZeppelin | ✅ |
| Developer tutorial | A simple Solidity Hello World application on Telos EVM for developers | ✅ |
| Blockchain explorer | A basic open-source blockchain explorer that allows you to see EVM transactions on testnet | 🟡 |
| Complex Dapp example | An example of complex Dapp ported to the testnet \(Uniswap, Aave, others\) | 🛑 |

### Milestone 3: First mainnet release

EVM readiness for real-word Dapps and decentralised finance.

* Mainnet launch with an alpha state

| Task  | Description | Status |
| :--- | :--- | :--- |
| EVM deployment on mainnet | The first deployment of EVM contract on the mainnet | 🛑 |
| Advanced blockchain explorer | A SaaS blockchain explorer that can do verified contracts, token transfer maps and all features DeFi users expect | 🛑 |
| Public JSON-RPC endpoint | Developer friendly JSON-RPC endpoints for testnet and mainnet | 🛑 |
| TheGraph integration | TheGraph backend for the Telos EVM chains | 🛑 |

### Milestone 4: Additional ecosystem improvements

First DeFi applications running on Telos EVM on mainnet

| Task | Description | Status |
| :--- | :--- | :--- |
| ERC-20 bridge | Easily moving tokens between Telos EVM mainnet and other EVM based  blockchains | 🛑 |
| Telos native and EVM smart contract integration | SDK for integrating between native Telos smart contracts and EVM based contracts | 🛑 |
| Block producer modifications | Any modifications needed for block producers or system contracts to make Telos EVM more attractive than other EVM based chains as a Dapp execution environment | 🛑 |



