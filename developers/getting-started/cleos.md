---
description: Interacting with the Network from Your Terminal
---

# cleos

1.\) The simplest way for us to interact with the Telos blockchain is by using the `cleos` \("command-line EOS"\) software from the [EOS repository](https://github.com/EOSIO/eos). Follow their [installation instructions](https://github.com/EOSIO/eos#mac-os-x).

2.\) Once installed, you can confirm that `cleos` has been installed correctly by simply typing `cleos --help` from the command line. If `cleos` is properly installed, then you will see helpful information on how to call the program from the terminal.

3.\) In order to obtain useful and up-to-date information about the state of the blockchain, we will need to request the data from a Block Producer's node. In this case we'll be using the following base URL: [https://testnet.telos.caleos.io](https://testnet.telos.caleos.io)

Execute the following command from your terminal, with `myAccountName` replaced by your actual Telos Testnet account name: `cleos -u https://testnet.telos.caleos.io get account myAccountName` . If your endpoint is up-to-date and your account is activated then you should see output like the following in your terminal:

```text
created: 2020-01-24T02:34:56.500
permissions: 
     owner     1:    1 EOS7rmxcb5RDGUvUTtF9iJotoY7M24RQtZ6sLaHiJNe1zYQSEujgf
        active     1:    1 EOS7rmxcb5RDGUvUTtF9iJotoY7M24RQtZ6sLaHiJNe1zYQSEujgf
memory: 
     quota:     126.4 KiB    used:     3.373 KiB  

net bandwidth: 
     staked:        20.0000 TLOS           (total stake delegated from account to self)
     delegated:      0.0000 TLOS           (total staked delegated to account from others)
     used:                 0 bytes
     available:        105.3 MiB  
     limit:            105.3 MiB  

cpu bandwidth:
     staked:        20.0000 TLOS           (total stake delegated from account to self)
     delegated:      0.0000 TLOS           (total staked delegated to account from others)
     used:                 0 us   
     available:        20.65 sec  
     limit:            20.65 sec  

TLOS balances: 
     liquid:        2000.0000 TLOS
     staked:          40.0000 TLOS
     unstaking:        0.0000 TLOS
     total:         2040.0000 TLOS

producers:     <not voted>
```

Congrats, the blockchain is showing your account information. Next, we are going to inspect our account's history, which should show some transactions related to our account activation and the TLOS tokens that we received from the testnet faucet.

First, let's take a moment to understand the "action" and "transaction" terminology utilized by the Telos blockchain, as well as cryptocurrency as a whole. First generation cryptocurrencies like Bitcoin were focused on the storage and transfer of the chain's native tokens \(BTC\), with the blockchain primarily being used as a ledger storing addresses and transaction inputs + outputs. With the rise of Ethereum and other general-purpose blockchains the type of data that can be stored has opened up to store many more types of data including **strings, vectors, maps, enums, timestamps, and custom types**. The types of "transactions" that can be executed on the Telos blockchain is nearly limitless. "**Actions**" refer to the atomic procedures that can be executed through a smart contract on the blockchain, and "**transactions**" refers to a grouping of multiple actions that can be executed atomically \(all completed successfully or none completed at all, no partial execution\).

As an example, the account creation transaction consists of three different actions:

1. **eosio::newaccount**: creates the account by executing the `newaccount` action on the `eosio` account smart contract
2. **eosio::buyram**: buys some ram for the account by executing the `buyram` action on the `eosio` account smart contract
3. **eosio::delegatebw** - stakes some CPU/NET for the account by executing the `delegatebw` action on the `eosio` account smart contract

So don't let the `transaction` vs `action` terminology get you mixed up. Now, let's find the most recent actions related to our account.

4.\) Execute the following code from your terminal to get a list of the most recent actions that have involved your account `cleos -u https://testnet.telosusa.io get actions myAccountName`

```text
#  seq  when                              contract::action => receiver      trx id...   args
================================================================================================================
#1009495   2020-01-24T02:53:39.500     eosio.token::transfer => eosio.token   775d9c54... {"from":"faucet.tf","to":"captaincrypt","amount":1000,"symbo...
#1009490   2020-01-24T02:34:56.500     eosio.token::transfer => eosio.token   bd8df62b... {"from":"faucet.tf","to":"captaincrypt","amount":1000,"symbo...
```

Here you can see that my `captaincrypt` account has received testnet faucet TLOS tokens on two occasions. This result is helpful but not as useful as if it were returned to us in JSON format. Let's enable the JSON option by executing the following from our terminal `cleos -u https://testnet.telosusa.io get actions` **`--json`** `myAccountName`

```text
{
  "last_irreversible_block": 28290346,
  "actions": [{
      "account_action_seq": 1009495,
      "global_action_seq": 34542235,
      "block_num": 27749144,
      "block_time": "2020-01-24T02:53:39.500",
      "action_trace": {
        "action_ordinal": 1,
        "creator_action_ordinal": 0,
        "receipt": {
          "receiver": "eosio.token",
          "global_sequence": 34542235,
          "recv_sequence": 1009495,
          "auth_sequence": [{
              "account": "faucet.tf",
              "sequence": 2228
            }
          ]
        },
        "receiver": "eosio.token",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [{
              "actor": "faucet.tf",
              "permission": "active"
            }
          ],
          "data": {
            "from": "faucet.tf",
            "to": "captaincrypt",
            "amount": 1000,
            "symbol": "TLOS",
            "memo": "Testnet faucet"
          },
          "hex_data": "7b2266726f6d223a226661756365742e7466222c22746f223a226361707461696e6372797074222c22616d6f756e74223a313030302c2273796d626f6c223a22544c4f53222c226d656d6f223a22546573746e657420666175636574227d"
        },
        "trx_id": "775d9c545b17bdff3042b8c8a27d52215e2fb660ff52c5484f68cfd4e228f91e",
        "block_num": 27749144,
        "block_time": "2020-01-24T02:53:39.500"
      }
    }
```

That's _much_ better! Now we have a format that shows all of the information and in a format that can be consumed by most software.

Now that we've seen what the data for a transaction looks like, it's time to try executing a transaction from our account. In this case we will try to send some Testnet TLOS tokens back to the `faucet.tf` account from which we received them, with a note "Thanks for the free TLOS". Try executing the following commands from your terminal: `cleos -u https://testnet.telosusa.io transfer myAccountName faucet.tf "1.0000 TLOS" "Thanks for the free TLOS!"`

You may have ended up with the following error, a reminder that we have not yet established `cleos` as the wallet for our TLOS account:

```text
Error 3120006: No available wallet
Ensure that you have created a wallet and have it open
Error Details:
You don't have any wallet!
```

Fear not, we would be more concerned if `cleos` _were_ able to control our tokens without the private key! So let's create the wallet for controlling our testnet account.

5.\) To link our `cleos` software we will want to create a wallet, unlock it with the password, and import our private key \(which we should be able to export from Scatter or SQRL\). To create the wallet, execute the following from the command line: `cleos wallet create --name telos-testnet-myAccountName --file telos-testnet-myaccountName.txt`

This command tells `cleos` to create a wallet called `telos-testnet-myAccountName` and save the **wallet password** to the file `telos-testnet-myAccountName.txt` in the current working directory. **Please make sure that you do not lose this password because you will need it in order to execute token transfers in `cleos` , and it will be inconvenient to have to create a new wallet if you lose the password.**

If the command executes successfully, the file that you specified \(`telos-testnet-myAccountName.txt`\) should now contain a password that is about 53-characters long and starting with `PW.....`. Go ahead and copy that password as we will be using it in our next command: `cleos wallet unlock -n telos-testnet-myAccountName --password PWmy53CharacterWalletPasswordasdfasasdfljpouewrlscad2342asf`

This command unlocks the wallet and sets is as the currently active wallet \(in the event that you have multiple wallets in `cleos`\). Next, we want to import the private key for your testnet account \(which you should be able to export from Scatter or SQRL\) to give this wallet control over our Telos Testnet account. Execute the following command into your terminal: `cleos wallet import --name=telos-testnet-myAccountName --private-key 5KbSome51CharacterPrivateKey`

You should see output in your console that looks something like the following: `imported private key for: EOSsome53CharacterPublicKey`, signifying that your private key has been properly imported.

6.\) Next, let's attempt to re-execute the token transfer that failed earlier, keep in mind that you may have to re-unlock your wallet if too much time has passed since you last used the wallet. If so, just re-execute the `cleos wallet unlock` command from earlier: `cleos -u https://testnet.telosusa.io transfer --json myAccountName faucet.tf "1.0000 TLOS"`

If you have properly linked your private key and wallet then you should see JSON output that looks something like the following:

```text
{
  "transaction_id": "3d8f89c356c173f20383e0ae4611425f837026c51357ff2979a530b26d221f4f",
  "processed": {
    "id": "3d8f89c356c173f20383e0ae4611425f837026c51357ff2979a530b26d221f4f",
    "block_num": 28379445,
    "block_time": "2020-01-27T18:36:25.000",
    "producer_block_id": null,
    "receipt": {
      ...
    },
    "elapsed": 260,
    "net_usage": 128,
    "scheduled": false,
    "action_traces": [{
        "action_ordinal": 1,
        "creator_action_ordinal": 0,
        "closest_unnotified_ancestor_action_ordinal": 0,
        ...
        ,
        "receiver": "eosio.token",
        "act": {
          "account": "eosio.token",
          "name": "transfer",
          "authorization": [{
              "actor": "captaincrypt",
              "permission": "active"
            }
          ],
          "data": {
            "from": "captaincrypt",
            "to": "faucet.tf",
            "quantity": "1.0000 TLOS",
            "memo": ""
          },
          "hex_data": "90abbf683a93ab41000058196485b459102700000000000004544c4f5300000000"
        },
        ...
      }
```

Congrats, you have properly executed a token transfer from your account back to the `faucet.tf` account!

