---
description: Read below for a summary of Telos Decide
---

# Telos Decide

## Telos Decide™ Governance Engine

Telos Decide™ is an on-chain governance engine exclusively for the Telos® Blockchain Network that offers an extensive suite of voting services and DAC/DAO tools for both users and developers.

### Features

#### Secure Ballot Hosting 🔐

Any user on the Telos Blockchain Network may create and publish a public ballot hosted through Telos Decide. During ballot creation, the ballot publisher selects a token to use for counting votes. The default is the standard `VOTE` token - usable in all Telos Core Governance ballots, but Telos Decide offers additional services for creating tokens that can be selected instead.

#### Advanced Voting Methods 🗳

The Telos Decide Governance Engine boasts an extensive set of voting methods that transform how votes are applied to ballot options. With these voting methods, ballot publishers are able to customize how they want to handle differences in voters' token balances and how those tokens should be cast among multiple choices on the ballot.

#### Custom Token Treasuries 💎

Any user on the Telos Blockchain Network may create a custom token treasury that automatically inherits Telos Decide's entire suite of voting services. These treasuries govern the minting and distribution of tokens and can also be customized to allow or disallow specific token behaviors like `transferring`, `burning`, `staking`, or `reclaiming`. Once a treasury has been created, any voter with a balance of its tokens may publish public ballots accessible to all other holders of that same token.

#### Committee Management Tools 👥

Telos Decide offers a suite of committee creation and management actions that are available to any active token treasury and its voters. Developers can also hook their external smart contracts into Telos Decide's committee tools to enable complete on-chain committee management.

#### Traceable Vote Integrity ✅

Telos Decide's custom rebalance system allows workers to recalculate vote weights when a voter's token balance changes. Workers who perform this service are eligible for payment rewards in proportion to the amount of work they have performed compared to all other workers in the treasury. Future updates will allow for optional identity services to further enhance voting and platform features.

#### Integrated Payroll System 💵

All treasuries created on the platform have access to Telos Decide's payroll system, allowing managers to continuously fund operations within their own treasury. Multiple payrolls can be created under a single treasury, each with their own bucket of funds that are released to designated recipients at a customizable rate.

#### Optional Light Ballots ☁

Light ballots disable the on-chain vote tracking portion of the voting process - this allows for developers to track votes in an off-chain database that is built by an [Iris](https://github.com/CALEOS/iris-client), [Demux](https://github.com/EOSIO/demux-js), or Spectrum style service instead.

This option enables Telos Decide to power vastly more voting services by saving RAM costs for both the platform and voters, while at the same time retaining the complete traceability and audit-ability benefits offered by the Telos blockchain.

#### Profitable Worker Services 👷♂

Telos Decide has several janitorial actions that incentivize workers on the network to maintain an optimized voting system. Workers are paid proportionally for their work in keeping the platform clean and balanced for all users.

### Understanding Telos Decide's Role

Telos Decide's primary purpose is to consolidate all the common boilerplate functions of voting contracts into a secure and transparent chain-wide service available to organizations, developers, and general users.

For **developers**, this means they can leave the user registration, token management, and vote tracking up to Telos Decide, and instead design contracts to interact with Telos Decide for drafting, launching, and reacting to ballot results. This way, external Smart Contracts can _contractually_ interpret and act on these results according to their intended use cases.

For **organizations**, this means they can confidently track crucial ownership and participation in dBusiness activities, and Telos Decide's robust toolset offers fine granularity of control over token distribution and behavior allowing businesses to adjust for their personal regulatory needs.

#### Services

| Service | Description | Setup Fee |
| :--- | :--- | :--- |
| **Voting** | Voter registration, token balances, voting, un-voting, staking, and unstaking. | Free |
| **Ballots** | Ballot hosting, customization, and results broadcasting. | 10 TLOS per ballot |
| **Treasuries** | Treasury creation, locking/unlocking, verbose settings, worker fund, token minting, transferring, reclaiming, and burning. | 500 TLOS per treasury |
| **Committees** | Committee creation, management, security, and seat control. | 100 TLOS per committee |
| **Archival** | Archive important ballots to preserve results. | 1 TLOS per day |
| **Workers** | Participation, progress tracking, and profit incentives. | Free |

{% hint style="info" %}
Note that the above fees are fully customizable and can be adjusted by the Block Producers or by a Referendum from the Telos Community at any time.
{% endhint %}

Further information about each service can be found in the relevant documentation below.

### Services Documentation

{% page-ref page="treasuries.md" %}

{% page-ref page="ballots.md" %}

{% page-ref page="voting.md" %}

{% page-ref page="payrolls.md" %}

{% page-ref page="workers.md" %}

### Roadmap

#### Q2 2020

* Additional Worker Services
* Additional Voting Methods

#### Q3 2020

* Delegates, Delegate Voting
* External Token Registration

#### Q4 2020

* Platform Optimization

#### Down Yonder

* Optional Identity Services

### References

1. [Voting Methods by Eric Pacuit - Stanford Encyclopedia of Philosophy](https://plato.stanford.edu/entries/voting-methods/#CritForCompVotiMeth)

### Contributing to Telos Decide

Telos Decide is an open-source engine where contributions and improvements are welcomed by the community.

To make a contribution, simply fork the repo and submit a PR for your changes. In order to avoid duplication of work, it's best to engage with the community and Telos Core Developers first to determine what would be an acceptable addition to the platform.

Discussion happens mostly on Telegram, so feel free to join the [Telos Dapp Development](https://t.me/dappstelos) chat and pitch your idea!

Telos® in respect to any blockchain usage is a registered trademark and Decide™ and Telos Decide™ in respect to decentralized and/or blockchain governance and voting systems are trademarks. All rights are reserved by their respective owners.

