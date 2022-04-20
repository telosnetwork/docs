---
description: Build Your First (Minimal) DApp
---

# Hello World Contract

Now that we have gotten our testnet account and familiarized ourselves with executing commands from the command line with `cleos`, it is now time for us to build our first Telos smart contract!

1.) Install the [Contract Development Toolkit](https://github.com/EOSIO/eosio.cdt) (CDT) by following [the instructions](../platform/development-environment/install-the-contract-dev-toolkit.md). Once installed, you should be able to check the version number from the command line by typing in `eosio-init -version`, which should output the version number of the software

2.) Create a new folder on your computer that we will name `helloWorld` , then `cd helloWorld` into the folder.

3.) Enter `eosio-init -project helloWorld`. This will create the basic source code needed to create a simple "hello world" smart contract that we will be able to publish onto the blockchain. The name of the contract is determined by the term following the `-project` text, so our contract will be entitled `helloWorld`. The basic folder structure should look something like the following:

* `build`: this is where the compiled final files will be generated that we will push to the blockchain. The folder should start off empty
* `include`: the header files that will be referenced in the C++ source code
* `ricardian`: this folder is for _Ricardian Contracts_, which are outside of the scope of this tutorial, but are typically used in parallel with smart contracts to help clarify the contract's **intent.** We will ignore this folder for now.
* `src`: the source C++ files that will dictate the behavior (actions) of our smart contract. It also starts off with a `CMakeLists.txt` file which helps to configure the compilation process (this file can be ignored for now)
* `README.txt`: directions on how to build and publish the smart contract

We are going to look two main files here: `include/helloWorld.hpp` and `src/helloWorld.cpp` . Let's start with the header file:

```
#include <eosio/eosio.hpp>
using namespace eosio;

CONTRACT helloWorld : public contract {
   public:
      using contract::contract;

      ACTION hi( name nm );

      using hi_action = action_wrapper<"hi"_n, &helloWorld::hi>;
};
```

This header file starts off by importing the `eosio/eosio.hpp` header file that includes many tools that will make our lives easier. It then uses the `eosio` namespace to make our syntax cleaner. The contract `helloWorld` is a class extending the `eosio::contract` class. Inside of the class we use the `eosio::contract::contract` namespace and then declare the action `hi` which will take in a parameter `nm` of type `name`. Note that the `ACTION` syntax is a [macro](http://www.cplusplus.com/doc/tutorial/preprocessor/) imported from the `eosio/eosio.hpp` and represents a type of function.

Now we will take a look at the source file `src/helloWorld.cpp` :

```
#include <helloWorld.hpp>
ACTION helloWorld::hi( name nm ) {
   /* fill in action body */
   print_f("Name : %\n",nm);
}
```

In this file we are simply defining the method `hi` on the `helloWorld` class. Again, the `ACTION` syntax is a macro for a function. The method takes in `nm` which is of type `name` . Inside of the method, a simple string `Name : someName` is printed to the console output for any full node that processes this smart contract action.

4.) In order to compile the source code into usable code that we can publish to the blockchain, we will need to make sure that we have [cmake](https://cmake.org) and [make](http://www.cplusplus.com/articles/jTbCpfjN/) installed. Execute `brew install make && brew install cmake` for MacOS and `sudo apt-get -y install cmake` for [Ubuntu](https://ubuntu.com). Once they are installed, navigate to the `build` directory with `cd build` and then `cmake .. && make ..`. You should then see the following folders created within the `build` directory: `CMakeFiles` , `helloWorld` , and `helloWorld_project-prefix`.

5.) Now that we have generated the output files we can try publishing them to the blockchain! The command that we want to use is `cleos set contract` and the documentation we have for it is the following:

```
Usage: cleos set contract [OPTIONS] account [contract-dir] [wasm-file] [abi-file]

Positionals:
  account TEXT                The account to publish a contract for (required)
  contract-dir TEXT           The path containing the .wasm and .abi
  wasm-file TEXT              The file containing the contract WASM relative to contract-dir
  abi-file TEXT               The ABI for the contract relative to contract-dir
```

In order to upload a smart contract, we need an account to "own" the smart contract. It is advisable to keep you personal Telos account separate from any smart contracts accounts since a.) naming the account something relevant to its purpose will be useful to you and anyone interacting with that account and b.) we can give your personal account owner permission anyway. So... let's create an account for this contract!
