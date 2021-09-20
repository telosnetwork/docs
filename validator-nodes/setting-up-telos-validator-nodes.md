# Setting up Telos Validator Nodes

* A validator needs to know it's role & fulfill the requirements.
* Having more validators is healthier and better for the Telos ecosystem, especially validators that are committed to transparency, and being in a state of giving continuous contribution.
* Validators are a core component of Telos network built on EOSIO protocol.
* Below is the guide to get a node up and running as a Validator on Telos.

## What is the role of a Telos Validator

* Validators are decentralized entities that govern the Telos blockchain. Validators will produce the blocks of the Telos blockchain.
* Telos Validators play a key role in the operation of the network.
* They provide stability, reliability, security and extensive infrastructure coverage for Telos network.
* Contribute to Telos development toolkits, so as to get noticed by the voters & stay in BP list eligible for incentives \(in TLOS tokens\).
* Telos Validators verify transactions on the Telos network by collecting transaction data and storing that information in blocks. 
* Once a block is prepared, validators broadcast the block to the network for verification.
* Validators will earn block rewards in the form of TLOS tokens produced by token inflation.
* Validators are responsible for Telos infrastructure growth, community support and education, and financial support for development of Telos DApps.
* Validators need to participate in on-chain governance. For more, refer to [this](https://telos.net/governance-documentation/).
* Validators can have a look at the [Telos rules](https://telos.net/governance-documentation/).

### Telos Validator Requirements

* **A Mission** — what are you going to provide to the world as a Telos Validator? How will you spend your TLOS? Why should people vote for you?
* **Unique Telos producer account** — This should not resemble the name of any current Telos Validator Candidates. You can view all of the current Validators and Validator Candidates [here](https://telos.bloks.io/).
* **A few servers running nodeos** — virtual machines or even a desktop with a lot of RAM would be ok to start off. Some Telos Validators are running on desktop hardware \(i7 or i9 chips\). You just need to provide the RAM that is required by Telos Mainnet and it increases at a rate of 1 KB/block currently. It is ~ 12.56 GB at the time of writing this guide.
* **Website** — your website should have a `bp.json` \([example](https://www.alohaeos.com/bp.json)\) at it's root, and links to an ownership disclosure \([example](https://www.alohaeos.com/ownership)\), and a code of conduct \([example](https://www.alohaeos.com/conduct)\)\).
* **Validator account creation for rewards** — Create a unique Telos Account that will be the name of your Validator. Telos Accounts are 12 characters long. For account creation, visit here: 
  * [Telos account creator](https://telos-account-creator.com/)
  * [FREE Telos account via Sqrl Wallet](https://telosuk.io/how-to-create-a-free-telos-account/)

## What is a Telos validator node

* In the Telos network, block production and block validation are performed by special nodes called "Telos validator node". Validator nodes are elected by Telos stakeholders via DPoS Consensus Algorithm. Each validator node runs an instance of a Telos node using the `nodeos` service. For this reason, validators that are on the active schedule to produce blocks are also called "active" or "producing" validator nodes.

## Types of nodes

* In the Telos blockchain network, you might find the slightly different naming of nodes, such as a API node, Producer node, History-API node, Seed node. All nodes keep updating an internal database by applying the transactions as they arrive in incoming blocks. The difference between the node types lies in the amount of history they keep track of, and in the functionality they provide.
* After proper installation of released EOSIO core software, each type of node is implemented by the same executable, however, each node would need to set up different configurations to start the node. For example: although a block producing node can have full history, that would be a waste of resources. Block producing validator nodes should run with minimal plugins \(i.e., only witness\_plugin\). Also, producing validator nodes should not have open network ports. We strongly recommend all node service providers to run and maintain their own nodes for reliability and security reasons.

### API

API nodes provide network services to client applications. They usually have account transaction histories accessible though API calls, but can vary in the amount of available history.

### History API

History-API nodes are API nodes with a complete transaction history of all accounts.

### Seed

* A seed node is a special node that allows the incorporation of new nodes to the network and maintains the strength of the network at all times, by allowing them to synchronize and obtain a copy of the data from the blockchain, replicating it and adding resistance and security to it.
* Seed nodes are nodes that accept incoming P2P connections. They are the first nodes contacted by a freshly started node. In that sense they serve as an entry point into the network. Once a node has entered the network it will receive additional node addresses from its peers, so all nodes can connect to each other. A seed node can also be an API node. The Telos core software i.e. EOSIO comes with a preconfigured list of seed nodes for easy bootstrapping.
* The seed nodes are used only to locate or find complete nodes that are running the Telos Blockchain client.
* So, when a new node wants to gain access to the network, it must connect with a seed node, which is a Telos client that is always active and has a static IP address. This client operates as a gateway to the Telos network, being one of the first connections that Telos clients make at the beginning.
* Thus, seed nodes play an important role within the network, operating from highly trusted servers. Allowing new clients to connect to the Telos network automatically and without the need for manual intervention by a user. Although it may be the case that some of these nodes can become dishonest, causing a negative impact within the network. So it is not recommended to place trust in a single seed node.

### Producer

* A producer node is a node run by a Block Producer \(BP\). Each producer node \(active/producing/top-21 only\) validates all blocks and transactions it receives. The nodes of elected \(active/producing/top-21 only\) producers take turns in bundling new transactions into blocks and broadcasting them to the network.
* Producer nodes generally runs in two modes using `nodeos` EOSIO component:

#### A. Producing Node

* **Producing Nodes** are configured for block production.
* They connect to the peer-to-peer network and actively produce new blocks.
* Loose transactions are also validated and relayed.
* On mainnet, they only produce blocks if their assigned block producer is part of an active schedule. 

#### B. Non-Producing Node

* **Non-Producing** Nodes connect to the peer-to-peer \(p2p\) network but do not actively produce new blocks.
* They are useful for acting as proxy nodes, relaying API calls, validating transactions, broadcasting information to other nodes, etc. 
* They are also useful for monitoring the blockchain state.

## Installation Methods

* EOSIO currently supports the following operating systems:
  * Amazon Linux 2
  * CentOS 7
  * Ubuntu 16.04
  * Ubuntu 18.04
  * MacOS 10.14 \(Mojave\)

> NOTE: If you are new to EOSIO, it is recommended that you install the EOSIO Prebuilt Binaries. If you are an advanced developer, a block producer, or no binaries are available for your platform, you may need to Build EOSIO from source depending on your OS.

### Ubuntu package method

```text
$ wget https://github.com/eosio/eos/releases/download/v2.0.11/eosio_2.0.11-1-ubuntu-18.04_amd64.deb
$ sudo apt install ./eosio_2.0.11-1-ubuntu-18.04_amd64.deb
```

### Compile source code method

1. (Skip to step 2 if already cloned) Clone the `EOSIO/EOS` repository from Github like this:

   ```text
   $ git clone https://github.com/EOSIO/eos.git --recursive 
   ```

2. Go to the `eos` folder 

   ```text
   $ cd eos
   ```

2. Go to required version

   ```text
   $ git checkout tags/v2.0.11
   ```

3. update the submodules

   ```text
   $ git submodule update --init --recursive
   ```

## Run Nodeos

`nodeos` generally runs in 2 modes:

### A. Producing/Active mode

`Producing Validator Nodes` are configured for block production. They connect to the peer-to-peer \(p2p\) network and actively produce new blocks. Loose transactions are also validated and relayed. On mainnet, Producing Validator Nodes only produce blocks if their assigned block producer is part of an active schedule.

> NOTE: System contracts required - These instructions assume you want to launch a producing validator node on a network with system contracts loaded. These instructions will not work on a default development node using native functionality, or one without system contracts loaded.

#### Goal

This section describes how to set up a producing node within the EOSIO network. A producing node, as its name implies, is a node that is configured to produce blocks in an EOSIO based blockchain. This functionality if provided through the producer\_plugin as well as other Nodeos Plugins.

**nodeos plugins**

* Plugins extend the core functionality implemented in `nodeos`. Some plugins are mandatory, such as `chain_plugin`, `net_plugin`, and `producer_plugin`, which reflect the modular design of `nodeos`. The other plugins are optional as they provide nice to have features, but non-essential for the nodes operation.
* The list of specific plugins are as follows:
  * `blockvault_client_plugin`
  * `chain_api_plugin`
  * `chain_plugin`
  * `db_size_api_plugin`
  * `history_api_plugin`
  * `history_plugin`
  * `http_client_plugin`
  * `http_plugin`
  * `login_plugin`
  * `net_api_plugin`
  * `net_plugin`
  * `producer_plugin`
  * `state_history_plugin`
  * `trace_api_plugin`
  * `txn_test_gen_plugin`

> Nodeos is modular: Plugins add incremental functionality to `nodeos`. Unlike runtime plugins, nodeos plugins are built at compile-time.

#### Pre-requisites

* Install the [EOSIO software](https://github.com/EOSIO/eos) before starting this section.
* It is assumed that `nodeos`, `cleos`, and `keosd` are accessible through the path. If you built EOSIO using shell scripts, make sure to run the Install Script.
* Know how to pass Nodeos options to enable or disable functionality.

#### Steps

Please follow the steps below to set up a producing node:

1. Local Wallet
2. Create your `bp.json` for your Telos validator
3. Register your account as a producing validator
4. Set Producer Name
5. Set the Producer's signature-provider
6. Define a peers list
7. Load the Required Plugins

**1. Local Wallet**

**a. Create Telos Wallet locally. Record the password and keep secure.**

```text
cleos wallet create -n <wallet_name> --to-console
<!-- OR -->
cleos wallet create -n <wallet_name> --file <filename_with_extension>
```

**b. Unlock EOS Wallet. Paste your wallet password**

```text
cleos wallet unlock -n <wallet_name> --password <wallet_password>
```

**c. Account creation:**

* M-1: Use services like [Telos account creator](https://telos-account-creator.com/) or [FREE Telos account via Sqrl Wallet](https://telosuk.io/how-to-create-a-free-telos-account/) to create your account.
* M-2: Using CLI

```text
cleos -u <api_endpoint> system newaccount --stake-net <telos_net_amount> --stake-cpu <telos_cpu_amount> --buy-ram-kbytes <telos_ram_amount> <telos_existing_account_name> <telos_existing_account_name> <owner-publickey> <active-publickey>
```

**d. Load new account private key into your wallet**

```text
cleos wallet import -n <wallet_name> <privkey>
```

**2. Create your bp.json for your Telos validator**

This will be used by voting portals and websites to identify validators. The `bp.json` contains location info for your Block Validator, nodes, and also contains other identifiable information such as your Block Producer public key.

For instance, [http://yourwebsite.com/bp.json](http://yourwebsite.com/bp.json) When you register your validator, the URL field should be filled with [http://yourwebsite.com](http://yourwebsite.com). Do not put the `bp.json` file in the URL.

For instance, for Aloha, the `bp.json` is located at [https://www.alohaeos.com/bp.json](https://www.alohaeos.com/bp.json), the URL to locate this will be [https://www.alohaeos.com](https://www.alohaeos.com).

* [Template for the standard bp\_info.json format for the EOS Mainnet.](https://github.com/eosrio/bp-info-standard)
* You can find most Validator's bp.json at their websites.
* Please conform to the [JSON format standard](https://www.w3schools.com/js/js_json_syntax.asp).
* Here is an excellent [JSON validator](https://jsonformatter.org/).

**3. Register your account as a producing validator**

In order for your account to be eligible as a producing validator, you will need to register the account as a producing validator:

```text
<!-- cleos -u <api_endpoint> system regproducer <producer_account_name> <producer_signature_public_key> <producer_website> <producer-geo-location> -->
cleos -u http://api.main.alohaeos.com system regproducer alohaeosprod EOS87wJkSDXLDVVoJUaBYd4tjg8F8chMWY5nPo8Mb5F919TpbjJvz https://www.alohaeos.com Honolulu
```

> NOTE: separate key pair used only for signing blocks and can not perform any other operation.
>
> If you currently have your active key listed in your `config.ini` for signing blocks — you need to stop it and replace it with a separate Signature key

Just follow this in order to replace the existing active \(or insecure key\) with separate signature key

* Create new key pair using `cleos create key --to-console`
* Replace signature provider record in your `config.ini` with the new key: `signature-provider = EOS-SIGNATURE-PUBLIC-KEY=KEY:SIGNATURE-PRIVATE-KEY`
* Call regproducer command with the new signature key: `cleos system regproducer [PRODUCER-NAME] [EOS-SIGNATURE-PUBLIC-KEY] {PRODUCER_URL] [COUNTRY_CODE]`

**4. Set Producer Name**

Set the `validator_name` option in `config.ini` to your account, as follows:

```text
# config.ini:

# ID of producer controlled by this node (e.g. inita; may specify multiple times) (eosio::producer_plugin)
producer-name = alohaeosprod
```

**5. Set the Producer's signature-provider**

You will need to set the separate private key for your validator. The public key should have an authority for the validator account defined above.

`signature-provider` is defined with a 3-field tuple:

* `public-key` - A valid EOSIO public key in form of a string.
* `provider-spec` - It's a string formatted like :
* `provider-type` - KEY or KEOSD

**Using a Key:**

```text
# config.ini:

signature-provider = PUBLIC_SIGNING_KEY=KEY:PRIVATE_SIGNING_KEY

//Example
//signature-provider = EOS51PsUQXRKphEBPBP8iH8ZRGNvyqJ13hbR8yXGSPKEf5TQH27TF=KEY:5KgV1HsxEm3qKYdLaUgpdZvJcAV2AA7zVDJYBL7nVoE4mdcqQR1
```

**Using Keosd:**

```text
# config.ini:

signature-provider = KEOSD:<data>   

//Example
//EOS51PsUQXRKphEBPBP8iH8ZRGNvyqJ13hbR8yXGSPKEf5TQH27TF=KEOSD:https://127.0.0.1:88888
```

**6. Define a peers list**

```text
# config.ini:

# Default p2p port is 9876
p2p-peer-address = 195.201.82.181:9876
p2p-peer-address = 47.52.71.18:9876
p2p-peer-address = 207.180.220.203:9876
p2p-peer-address = 149.28.254.141:9876
p2p-peer-address = p2p-telos.blckchnd.com:19876
p2p-peer-address = p2p.blindblocart.io:9877
p2p-peer-address = telos.caleos.io:9880
p2p-peer-address = p2p.telos.cryptosuvi.io:2222
```

For more, visit here for [Telos Mainnet](https://github.com/telosnetwork/api-p2p-nodes/blob/master/TelosMainNet.csv) & [Telos Testnet](https://github.com/telosnetwork/api-p2p-nodes/blob/master/TelosTestnet.csv)

**7. Load the Required Plugins**

In your `config.ini`, confirm the following plugins are loading or append them if necessary.

```text
# config.ini:

plugin = eosio::chain_plugin
plugin = eosio::producer_plugin
```

### B. Non-Producing or Standby mode

`Non-Producing Validator Nodes` connect to the peer-to-peer \(p2p\) network but do not actively produce new blocks; they are useful for acting as proxy nodes, relaying API calls, validating transactions, broadcasting information to other nodes, etc. `Non-Producing Validator Nodes` are also useful for monitoring the blockchain state.

#### Goal

This section describes how to set up a non-producing validator node within the Telos network. A non-producing validator node is a node that is not configured to produce blocks, instead it is connected and synchronized with other peers from an EOSIO based blockchain, exposing one or more services publicly or privately by enabling one or more Nodeos Plugins, except the producer\_plugin.

#### Pre-requisites

* Install the [EOSIO software](https://github.com/EOSIO/eos) before starting this section.
* It is assumed that `nodeos`, `cleos`, and `keosd` are accessible through the path. If you built EOSIO using shell scripts, make sure to run the Install Script.
* Know how to pass Nodeos options to enable or disable functionality.

#### Steps

Please follow the steps below to set up a non-producing node:

1. Set Peers
2. Enable one or more available plugins

**1. Set Peers**

You need to set some peers in your config ini, for example:

```text
# config.ini:

# Default p2p port is 9876
p2p-peer-address = 195.201.82.181:9876
p2p-peer-address = 47.52.71.18:9876
p2p-peer-address = 207.180.220.203:9876
p2p-peer-address = 149.28.254.141:9876
p2p-peer-address = p2p-telos.blckchnd.com:19876
p2p-peer-address = p2p.blindblocart.io:9877
p2p-peer-address = telos.caleos.io:9880
p2p-peer-address = p2p.telos.cryptosuvi.io:2222
```

For more, visit here for [Telos Mainnet](https://github.com/telosnetwork/api-p2p-nodes/blob/master/TelosMainNet.csv) & [Telos Testnet](https://github.com/telosnetwork/api-p2p-nodes/blob/master/TelosTestnet.csv)

Or you can include the peer in as a boot flag when running `nodeos`, as follows:

```text
nodeos ... --p2p-peer-address=106.10.42.238:9876
```

**2. Enable one or more available plugins**

Each available plugin is listed and detailed in the Nodeos Plugins section. When `nodeos` starts, it will expose the functionality provided by the enabled plugins it was started with. For example, if you start `nodeos` with `state_history_plugin` enabled, you will have a non-producing node that offers full blockchain history. If you start `nodeos` with `http_plugin` enabled, you will have a non-producing node which exposes the Telos RPC API. Therefore, you can extend the basic functionality provided by a non-producing node by enabling any number of existing plugins on top of it. Another aspect to consider is that some plugins have dependencies to other plugins. Therefore, you need to satisfy all dependencies for a plugin in order to enable it.

## Configuration Files

### Mainnet

#### genesis.json

```javascript
{
 "initial_key": "EOS52vfcN43YHHU8Akh7VyfBdnDiMg15dPTELosWG9SR86ssBoU1T",
 "initial_configuration": {
   "max_transaction_delay": 3888000,
   "min_transaction_cpu_usage": 100,
   "net_usage_leeway": 500,
   "context_free_discount_net_usage_den": 100,
   "max_transaction_net_usage": 524288,
   "context_free_discount_net_usage_num": 20,
   "max_transaction_lifetime": 3600,
   "deferred_trx_expiration_window": 600,
   "max_authority_depth": 6,
   "max_transaction_cpu_usage": 5000000,
   "max_block_net_usage": 1048576,
   "target_block_net_usage_pct": 1000,
   "max_generated_transaction_count": 16,
   "max_inline_action_size": 4096,
   "target_block_cpu_usage_pct": 1000,
   "base_per_transaction_net_usage": 12,
   "max_block_cpu_usage": 50000000,
   "max_inline_action_depth": 4
 },
 "initial_timestamp": "2018-12-12T10:29:00.000"
}
```

#### config.ini

```text
###### producer plugin options - enable if running producer node
plugin = eosio::producer_plugin
## sig provider keys should match the key on your producer-name
signature-provider = <pubkey>=KEY:<privkey>
producer-name = <your unique telos account name>

## additional producer plugin options can be left default
max-transaction-time = 10000
max-irreversible-block-age = -1
abi-serializer-max-time-ms = 2000
enable-stale-production = true
pause-on-startup = false

###### chain plugin options
plugin = eosio::chain_plugin
wasm-runtime = wabt
reversible-blocks-db-size-mb = 340
contracts-console = false
## set chain-state-db-size-mb to equal the size of your RAM
chain-state-db-size-mb = 98304

###### http plugin options
plugin = eosio::http_plugin
http-server-address = 0.0.0.0:1880
access-control-allow-origin = *
access-control-allow-credentials = false
https-client-validate-peers = 1 
verbose-http-errors = true
http-validate-host = 0
## enable if using https
# https-server-address = 0.0.0.0:443
# https-certificate-chain-file

# nodeos general config
p2p-server-address = 0.0.0.0:9876
p2p-listen-endpoint = 0.0.0.0:9876
p2p-max-nodes-per-host = 1
max-clients = 250
connection-cleanup-period = 30
sync-fetch-span = 100
txn-reference-block-lag = 0
allowed-connection = any
agent-name = bensigcoolconfig

###### additional plugins
plugin = eosio::chain_api_plugin
plugin = eosio::history_plugin

###### p2p peer address
p2p-peer-address = 159.69.63.222:7776
p2p-peer-address = 109.237.25.217:3876
p2p-peer-address = testnet.telos.caleos.io:9879
p2p-peer-address = p2p.testnet.telos.eosdetroit.io:1337
p2p-peer-address = telosafrique.eosnairobi.io:9376
p2p-peer-address = telos.eosbcn.com:9876
p2p-peer-address = testnet.telos.eosindex.io:9876
```

### Testnet

#### genesis.json

```javascript
{
"initial_key": "EOS7xyPWfh6743fhZ46zQQcXSctddoqG65d44YsyRnCJCs54mJLrH",
"initial_configuration": {
   "max_block_net_usage": 1048576,
   "target_block_net_usage_pct": 1000,
   "max_transaction_net_usage": 524288,
   "base_per_transaction_net_usage": 12,
   "net_usage_leeway": 500,
   "context_free_discount_net_usage_num": 20,
   "context_free_discount_net_usage_den": 100,
   "max_block_cpu_usage": 5000000,
   "target_block_cpu_usage_pct": 1000,
   "max_transaction_cpu_usage": 150000,
   "min_transaction_cpu_usage": 100,
   "max_transaction_lifetime": 3600,
   "deferred_trx_expiration_window": 600,
   "max_transaction_delay": 3888000,
   "max_inline_action_size": 4096,
   "max_inline_action_depth": 4,
   "max_authority_depth": 6
 },
"initial_timestamp": "2019–08–07T12:00:00.000"
}
```

#### config.ini

```text
###### producer plugin options - enable if running producer node
plugin = eosio::producer_plugin
## sig provider keys should match the key on your producer-name
signature-provider = <pubkey>=KEY:<privkey>
producer-name = <your unique telos account name>

## additional producer plugin options can be left default
max-transaction-time = 10000
max-irreversible-block-age = -1
abi-serializer-max-time-ms = 2000
enable-stale-production = true
pause-on-startup = false

###### chain plugin options
plugin = eosio::chain_plugin
wasm-runtime = wabt
reversible-blocks-db-size-mb = 340
contracts-console = false
## set chain-state-db-size-mb to equal the size of your RAM
chain-state-db-size-mb = 98304

###### http plugin options
plugin = eosio::http_plugin
http-server-address = 0.0.0.0:1880
access-control-allow-origin = *
access-control-allow-credentials = false
https-client-validate-peers = 1 
verbose-http-errors = true
http-validate-host = 0
## enable if using https
# https-server-address = 0.0.0.0:443
# https-certificate-chain-file

# nodeos general config
p2p-server-address = 0.0.0.0:9876
p2p-listen-endpoint = 0.0.0.0:9876
p2p-max-nodes-per-host = 1
max-clients = 250
connection-cleanup-period = 30
sync-fetch-span = 100
txn-reference-block-lag = 0
allowed-connection = any
agent-name = bensigcoolconfig

###### additional plugins
plugin = eosio::chain_api_plugin
plugin = eosio::history_plugin

###### p2p peer address
p2p-peer-address=testnet2.telos.eosusa.news:59877
p2p-peer-address=node1.testnet2.telosglobal.io:9876
p2p-peer-address=node2.testnet2.telosglobal.io:9876
p2p-peer-address=basho.eos.barcelona:9899
p2p-peer-address=sslapi.teloscentral.com:9875
p2p-peer-address=145.239.133.188:5566
p2p-peer-address=testnet.telos.eclipse24.io:6789
p2p-peer-address=testnet2.telos.eosdetroit.io:1337
p2p-peer-address=basho-p2p.telosuk.io:19876
p2p-peer-address=telos-testnet.atticlab.net:7876
p2p-peer-address=testnet.eossweden.eu:8022
p2p-peer-address=testnet.telos.cryptosuvi.io:2223
p2p-peer-address=nickfury.tlos.goodblock.io:9876
p2p-peer-address=telosapi.eosmetal.io:59877
p2p-peer-address=207.148.6.75:9877
p2p-peer-address=p2p.testnet.telosgermany.io
p2p-peer-address=176.9.86.214:9877
p2p-peer-address=telos-testnet-b.eosphere.io:9876
p2p-peer-address=testnet.telos.africa:9875
p2p-peer-address=p2p.testnet.telosgreen.com:9876
p2p-peer-address=testnet2p2p.telosarabia.net:9876
p2p-peer-address=peer.tlostest.alohaeos.com:9876
p2p-peer-address=157.230.29.117:9876
```

## Frequently Asked Questions \(FAQs\)

#### Q. How does a Validator create a new account on Telos Blockchain?

#### A. There are 2 ways to create an account on Telos Blockchain:

a. [Using Card payment](https://telos-account-creator.com/) b. [Create for FREE](https://telosuk.io/how-to-create-a-free-telos-account/)

#### Q. What is the difference between Telos Mainnet and Testnet?

#### A. The differences are as follows:

a. The mainnet of a blockchain launches when the protocol is fully developed and is the network where the project's functionalities, such as transactions with the native tokens, are carried out. Here is where transactions are being broadcasted, verified, and recorded on a distributed ledger technology. Whereas the testnet is a safe, separate network where developers carry out tests in the code without risking the main blockchain. The Telos Testnets are a sandbox for testing newly implemented features, finding bugs within the network and developing DApps. a. Testnet is for testing code updates, other functionalities, bug identification, new projects and program development, among many other uses. b. People associate a testnet with the initial developing of a blockchain where all the codes run, and we test everything before the final deployment of the protocol to the mainnet. c. the Telos testnets have one prominent advantage over the other testnets: it is a duplicate of the mainnet so it includes all its smart contracts and functionalities in the testnets. Because of this, developers and BPs obtain complete, accurate results when they run their tests, while reducing the work they have to do before running them. e. Testnet is designed to be as close to the code/features of the Telos Mainnet, with exception to any new innovations being tested in preparation for deployment on Mainnet.

#### Q. When a new upgrade or anything different will be tested before launch, what test strategies the Telos Validators follow?

#### A. Telos Validators follow a 4-tier test strategy, as it allows “to properly test/vet things at each respective level, and as it progresses through the tiers, additional testing/testers stress-test the system until its final deployment to the Telos Mainnet.” The stages are:

* Internal Dev Testing: closed-loop testing of all code changes before presenting to any public tier.
* Stagenet Testing: initial selected access, testing ran dedicated nodes.
* Testnet Testing: this is where most public testing of features will occur before completing deployment to Mainnet. Code changes/activation at this level require 15/21 approval of the Testnet BPs.
* Mainnet Deployment: once all testing has been completed, a deployment date agreed upon, a 15/21 BP approval is needed to activate all code changes/features on the Mainnet.

