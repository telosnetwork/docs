---
content_title: '2.1: Hello World Contract'
link_text: '2.1: Hello World Contract'
---

# Hello World Contract

Create a new directory called "hello" in the contracts directory you previously created, or through your system GUI or with cli and enter the directory.

```text
cd CONTRACTS_DIR
mkdir hello
cd hello
```

Create a new file, "hello.cpp" and open it in your favourite editor.

```text
touch hello.cpp
```

Below the `eosio.hpp` header file is included. The `eosio.hpp` file includes a few classes required to write a smart contract.

```cpp
#include <eosio/eosio.hpp>
```

Using the `eosio` namespace will reduce clutter in your code. For example, by setting `using namespace eosio;`, `eosio::print("foo")` can be written `print("foo")`

```cpp
using namespace eosio;
```

Create a standard C++11 class. The contract class needs to extend `eosio::contract` class which is included earlier from the eosio.hpp header

```cpp
#include <eosio/eosio.hpp>

using namespace eosio;

class [[eosio::contract]] hello : public contract {};
```

An empty contract doesn't do much good. Add a public access specifier and a using-declaration. The `using` declaration will allow us to write more concise code.

```cpp
#include <eosio/eosio.hpp>

using namespace eosio;

class [[eosio::contract]] hello : public contract {
  public:
       using contract::contract;
};
```

This contract needs to do something. In the spirit of **hello world** write an action that accepts a "name" parameter, and then prints that parameter out.

[Actions](https://github.com/telosnetwork/docs/tree/6ab1055a149d12ea9ad55d46f0ca92a2ac1b5e98/developers/platform/glossary/index/README.md#action) implement the behaviour of a contract

```cpp
#include <eosio/eosio.hpp>

using namespace eosio;

class [[eosio::contract]] hello : public contract {
  public:
      using contract::contract;

      [[eosio::action]]
      void hi( name user ) {
         print( "Hello, ", user);
      }
};
```

The above action accepts a parameter called `user` that's a [`name`](https://developers.eos.io/manuals/eosio.cdt/latest/structeosio_1_1name) type. EOSIO comes with a number of typedefs, one of the most common typedefs you'll encounter is `name`. Using the `eosio::print` library previously included, concatenate a string and print the `user` parameter. Use the braced initialization of `name{user}` to make the `user` parameter printable.

As is, the ABI &lt;&gt; generator in `eosio.cdt` won't know about the `hi()` action without an attribute. Add a C++11 style attribute above the action, this way the abi generator can produce more reliable output.

```cpp
#include <eosio/eosio.hpp>

using namespace eosio;

class [[eosio::contract]] hello : public contract {
  public:
      using contract::contract;

      [[eosio::action]]
      void hi( name user ) {
         print( "Hello, ", user);
      }
};
```

Everything together, here's the completed hello world contract

```cpp
#include <eosio/eosio.hpp>

using namespace eosio;

class [[eosio::contract]] hello : public contract {
  public:
      using contract::contract;

      [[eosio::action]]
      void hi( name user ) {
         print( "Hello, ", user);
      }
};
```

The ABI Generator in eosio.cdt supports several different style of attributes, see the ABI usage guide [here](https://github.com/telosnetwork/docs/tree/6ab1055a149d12ea9ad55d46f0ca92a2ac1b5e98/developers/platform/getting-started/03_smart-contract-development/03_understanding-ABI-files.md) You can compile your code to web assembly \(.wasm\) as follows:

```text
eosio-cpp hello.cpp -o hello.wasm
```

When a contract is deployed, it is deployed to an account, and the account becomes the interface for the contract. As mentioned earlier these tutorials use the same public key for all of the accounts to keep things simple.

```text
cleos wallet keys
```

Create an account for the contract using [cleos create account](https://developers.eos.io/manuals/eos/latest/cleos/command-reference/create/account), with the command provided below.

```text
cleos create account eosio hello YOUR_PUBLIC_KEY -p eosio@active
```

Deploy the compiled `wasm` to the blockchain with [cleos set contract](https://developers.eos.io/manuals/eos/latest/cleos/command-reference/set/set-contract).

**Get an error?** Check if your wallet needs to be unlocked.

In previous steps you should have created a \`contracts\` directory and obtained the absolute path and then saved it into a cookie. Replace "CONTRACTS\_DIR" in the command below with the absolute path to your \`contracts\` directory.

```text
cleos set contract hello CONTRACTS_DIR/hello -p hello@active
```

Great! Now the contract is set, push an action to it.

```text
cleos push action hello hi '["bob"]' -p bob@active
```

```text
executed transaction: 4c10c1426c16b1656e802f3302677594731b380b18a44851d38e8b5275072857  244 bytes  1000 cycles
#    hello.code <= hello.code::hi               {"user":"bob"}
>> Hello, bob
```

As written, the contract will allow any account to say hi to any user

```text
cleos push action hello hi '["bob"]' -p alice@active
```

```text
executed transaction: 28d92256c8ffd8b0255be324e4596b7c745f50f85722d0c4400471bc184b9a16  244 bytes  1000 cycles
#    hello.code <= hello.code::hi               {"user":"bob"}
>> Hello, bob
```

As expected, the console output is "Hello, bob"

In this case "alice" is the one who authorized it and `user` is just an argument. Modify the contract so that the authorizing user, "alice" in this case, must be the same as the user the contract is responding "hi" to. Use the `require_auth` method. This method takes a `name` as a parameter, and will check if the user executing the action matches the provided parameter.

```cpp
void hi( name user ) {
   require_auth( user );
   print( "Hello, ", name{user} );
}
```

Recompile the contract

```text
eosio-cpp -abigen -o hello.wasm hello.cpp
```

And then update it

```text
cleos set contract hello CONTRACTS_DIR/hello -p hello@active
```

Try to execute the action again, but this time with mismatched authorization.

```text
cleos push action hello hi '["bob"]' -p alice@active
```

As expected, `require_auth` halted the transaction and threw an error.

```text
Error 3090004: Missing required authority
Ensure that you have the related authority inside your transaction!;
If you are currently using 'cleos push action' command, try to add the relevant authority using -p option.
```

Now, with our change, the contract verifies the provided `name user` is the same as the authorising user. Try it again, but this time, with the authority of the "alice" account.

```text
cleos push action hello hi '["alice"]' -p alice@active
```

```text
executed transaction: 235bd766c2097f4a698cfb948eb2e709532df8d18458b92c9c6aae74ed8e4518  244 bytes  1000 cycles
#    hello <= hello::hi               {"user":"alice"}
>> Hello, alice
```

## What's Next?

* [Deploy, Issue and Transfer Tokens](02_deploy-issue-and-transfer-tokens.md): Learn how to deploy, issue and transfer tokens.

