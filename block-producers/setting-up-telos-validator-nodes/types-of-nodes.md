# Types of nodes

In the Telos blockchain network, you might find the slightly different naming of nodes, such as an API node, Producer node, History-API node, and Seed node.&#x20;

All nodes keep updating an internal database by applying the transactions as they arrive in incoming blocks. The difference between the node types lies in the amount of history they keep track of, and in the functionality they provide.

After proper installation of released EOSIO core software, each type of node is implemented by the same executable, however, each node would need to set up different configurations to start the node. For example: although a block producing node can have full history, that would be a waste of resources.&#x20;

Block producing validator nodes should run with minimal plugins (i.e., only witness\_plugin). Also, producing validator nodes should not have open network ports. We strongly recommend all node service providers to run and maintain their own nodes for reliability and security reasons.

### An API-node

API nodes provide network services to client applications. They usually have account transaction histories accessible though API calls, but can vary in the amount of available history.

### A History API-node

History-API nodes are API nodes with a complete transaction history of all accounts.

### A Seed-node

* A seed node is a special node that allows the incorporation of new nodes to the network and maintains the strength of the network at all times, by allowing them to synchronize and obtain a copy of the data from the blockchain, replicating it and adding resistance and security to it.
* Seed nodes are nodes that accept incoming P2P connections. They are the first nodes contacted by a freshly started node. In that sense they serve as an entry point into the network. Once a node has entered the network it will receive additional node addresses from its peers, so all nodes can connect to each other. A seed node can also be an API node. The Telos core software i.e. EOSIO comes with a preconfigured list of seed nodes for easy bootstrapping.
* The seed nodes are used only to locate or find complete nodes that are running the Telos Blockchain client.
* So, when a new node wants to gain access to the network, it must connect with a seed node, which is a Telos client that is always active and has a static IP address. This client operates as a gateway to the Telos network, being one of the first connections that Telos clients make at the beginning.
* Thus, seed nodes play an important role within the network, operating from highly trusted servers. Allowing new clients to connect to the Telos network automatically and without the need for manual intervention by a user. Although it may be the case that some of these nodes can become dishonest, causing a negative impact within the network. So it is not recommended to place trust in a single seed node.

### Producer-nodes

* A producer node is a node run by a Block Producer (BP). Each producer node (active/producing/top-21 only) validates all blocks and transactions it receives. The nodes of elected (active/producing/top-21 only) producers take turns in bundling new transactions into blocks and broadcasting them to the network.
* Producer nodes generally runs in two modes using `nodeos` EOSIO component:

#### A. Producing Node

* **Producing Nodes** are configured for block production.
* They connect to the peer-to-peer network and actively produce new blocks.
* Loose transactions are also validated and relayed.
* On mainnet, they only produce blocks if their assigned block producer is part of an active schedule.&#x20;

#### B. Non-Producing Node

* **Non-Producing** Nodes connect to the peer-to-peer (p2p) network but do not actively produce new blocks.
* They are useful for acting as proxy nodes, relaying API calls, validating transactions, broadcasting information to other nodes, etc.&#x20;
* They are also useful for monitoring the blockchain state.

The next section will cover the requirements needed to become a Telos Block Producer.
