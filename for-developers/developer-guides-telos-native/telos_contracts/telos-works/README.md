---
description: A Worker Proposal System for the Telos Blockchain Network
---

# Telos Works

## How It Works

At its core Telos Works is a mechanism for funding community projects. The following is a high-level guide to making a simple proposal and how to navigate the platform along the way.

{% hint style="info" %}
Telos Works receives 1,000,000 TLOS per month for funding proposals, as per the [TEDP amendment.](https://medium.com/@goodblock_info/understanding-the-telos-economic-development-plan-bd42d4666374) 
{% endhint %}

### 1. Draft a Proposal ✍

Any Telos Blockchain Network account holder may publish a project proposal with a designated amount of total required funding, earned across a set number of milestones. Each milestone included in a proposal will run an open ballot that lasts 29 days, and TLOS token holders can vote on these proposals through the [Telos Decide](https://github.com/telosnetwork/telos-decide) contract.

### 2. Define Milestones 📋

Each proposal is broken up into one or more milestones, configured during the proposal drafting stage. Every milestone included in a proposal will contain a vote that lasts 29 days, and each milestone can request an amount of funding for deliverables unique to that milestone.

### 3. Launch Proposal 🚀

Once a proposal has been set up it can be launched for a vote by the Telos Community! If the proposal passes, the first milestone will have been completed and the first round of funding granted. If the vote fails, the proposal is cancelled.

### 4. Complete Milestones ✅

If a proposal contains more milestones beyond the first, they will continue to be launched and voted on in order. Every milestone that passes will reward the predefined amount to the proposer. Note that only 1 milestone will be active at a time.

## Deposit into Telos Works

Telos Works uses a simple deposit/withdraw system for handling funds within the contract and charging payment for service fees.

To make a deposit to cover service fees, simply transfer TLOS to the `works.decide` account. Telos Works will catch the transfer and automatically create a deposit balance, if one doesn't already exist. Further deposits and withdrawals will automatically flow from this deposit balance.

#### Service Fees

| Name | Amount | Description |
| :--- | :--- | :--- |
| Proposal Fee | 5% of total requested funds | The proposal fee required to submit a proposal. |

{% hint style="warning" %}
The proposal fee will be refunded at the conclusion of the voting period if the proposal received enough participation and positive support from the community.
{% endhint %}

## Withdraw from Telos Works

To make a withdrawal from Telos Amend, call the `withdraw` action on the `works.decide` contract.

{% hint style="info" %}
Note that claiming funds from a successful proposal credits your Telos Works balance with the awarded TLOS tokens. These tokens must be withdrawn to your personal account to be fully claimed.
{% endhint %}

