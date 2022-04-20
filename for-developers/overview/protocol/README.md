---
description: >-
  Please note: All the details described below which is applicable to EOSIO,
  applies to Telos.
---

# Protocol

## Core

`EOSIO Core` provides the basic building blocks for the `system` layer and because they are not implemented as smart contracts they do not provide the same level of flexibility. Nevertheless, the `core` implementation is also open source and thus it can be modified as well to suit custom business requirements.

The core protocols are:

1. [Consensus Protocol](consensus\_protocol.md)
2. [Transactions Protocol](transactions\_protocol.md)
3. [Network or Peer to Peer Protocol](network\_peer\_protocol.md)
4. [Accounts and Permissions](accounts\_and\_permissions.md)

## System

The EOSIO blockchain platform is unique in that the features and characteristics of the blockchain built on it are flexible, that is, they can be changed, or be modified completely to suit each business case requirement. Core blockchain features such as consensus, fee schedules, account creation and modification, token economics, block producer registration, voting, multi-sig, etc., are implemented inside smart contracts which are deployed on the blockchain built on the EOSIO platform. These smart contracts are referred to as `system contracts` and the layer as the `EOSIO system` layer, or simply `system` layer.

Block.one implements and maintains these `system contracts`, as samples only, encapsulating the base functionality for an EOSIO based blockchain and they are listed below:

1. [eosio.bios](https://developers.eos.io/manuals/eosio.contracts/latest/action-reference/eosio.bios)
2. [eosio.system](https://developers.eos.io/manuals/eosio.contracts/latest/action-reference/eosio.system)
3. [eosio.msig](https://developers.eos.io/manuals/eosio.contracts/latest/action-reference/eosio.msig)
4. [eosio.token](https://developers.eos.io/manuals/eosio.contracts/latest/action-reference/eosio.token)
5. [eosio.wrap](https://developers.eos.io/manuals/eosio.contracts/latest/action-reference/eosio.wrap)

Also part of the `system` layer are the following concepts:

1. [System accounts](https://developers.eos.io/manuals/eosio.contracts/latest/index/#system-contracts-system-accounts-priviledged-accounts)
2. [RAM](https://developers.eos.io/manuals/eosio.contracts/latest/index/#ram)
3. [CPU](https://developers.eos.io/manuals/eosio.contracts/latest/index/#cpu)
4. [NET](https://developers.eos.io/manuals/eosio.contracts/latest/index/#net)
5. [Stake](https://developers.eos.io/manuals/eosio.contracts/latest/index/#stake)
6. [Vote](https://developers.eos.io/manuals/eosio.contracts/latest/index/#vote)
