---
description: Write a Simple Script to Send Tokens
---

# Building Your DApp with Javascript

Now that you have created your testnet account, it's time for you to view the transaction on the blockchain. The simplest way for us to achieve this is by creating a simple NodeJS script that utilizes [EOS-JS](https://github.com/EOSIO/eosjs) library to communicate with a Block Producer's API for the data. The code for this tutorial will be kept in [this repo](https://github.com/kylanhurt/telos-tutorial), for reference. Keep in mind that you will need [Git](https://git-scm.com/), [NodeJS](https://nodejs.org/en/), and [NPM](https://www.npmjs.com/get-npm) installed on your operating system.

### Account Info

1.\) Create a new folder on your computer, I will name mine `telos-tutorial`.

2.\) Navigate into the `telos-tutorial` folder and initialize the npm project with `npm init` . You can enter your information, or simply just press enter for each step. Once done, you should see a `package.json` file within the folder

3.\) Inside of this folder install eosjs and node-fetch by entering `npm install eosjs node-fetch`. Node-fetch will give us the ability to execute HTTP requests from within our script.

4.\) Create the entrypoint file for the project either through the command line or by doing it through your IDE / text editor. The file's name should be `getAccount.js` 

5.\) Inside of `getAccount.js` insert the following code:

```text
const fetch = require('node-fetch')
const eosjs = require('eosjs')
const JsonRpc = eosjs.JsonRpc

const ENDPOINT = `https://testnet.telos.caleos.io`
const rpc = new JsonRpc(ENDPOINT, { fetch })

const getAccount = async (accountName) => {
  const accountInfo = await rpc.get_account(accountName)
  console.log('account info: ', accountInfo)
}

getAccount('myAccount')
```

Notes have been included in the file explaining how the code works. The script imports two libraries, `fetch` and `eosjs`, sets an Telos Testnet endpoint \(typically operated by a Block Producer, you can find some options [here](https://github.com/eostoolkit/eos-networks/blob/37de020991c3d6c7e2a0933c232181d7866ed7bb/networks.json#L223)\), defined a `getAccount` routine that takes an account name as an input and executes the `get_account` procedure on the endpoint. 

6.\) Go ahead and run the script from the terminal with the `node getAccount.js` command. The result in your terminal _should_ look something like the following \(note that `captaincrypt` is my account name:

```text
account info:  { account_name: 'captaincrypt',
  head_block_num: 28074886,
  head_block_time: '2020-01-26T00:14:45.000',
  ...
  ram_quota: 129399,
  net_weight: 200000,
  cpu_weight: 200000,
  net_limit: { used: 0, available: 110385499, max: 110385499 },
  cpu_limit: { used: 0, available: 20647737, max: 20647737 },
  ram_usage: 3454,
  permissions:
   [ { perm_name: 'active', parent: 'owner', required_auth: [Object] },
     { perm_name: 'owner', parent: '', required_auth: [Object] } ],
  total_resources:
   { owner: 'captaincrypt',
     net_weight: '20.0000 TLOS',
     cpu_weight: '20.0000 TLOS',
     ram_bytes: 127999 },
  self_delegated_bandwidth:
   { from: 'captaincrypt',
     to: 'captaincrypt',
     net_weight: '20.0000 TLOS',
     cpu_weight: '20.0000 TLOS' },
  refund_request: null,
  voter_info:
  ...
```

Congratulations, we have proven that your account has been registered by the network. If your results don't look anything like the above then make sure you have already gone through the account activation process, and that the endpoint you used is really online \(and specifically for Telos Testnet\).

Now that we've established that our account is activated, it's time for us to take a closer look into transactions. 

### Transaction Info

Much the same as our RPC method for getting account info, there also exists an endpoint for getting information about transactions.

