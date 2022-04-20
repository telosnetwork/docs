---
description: Follow along for an example contract built with Telos Decide™ Integration
---

# Contract Integration

## Building An External Contract

For this Example Guide we will walk through building a simple external contract to act on Telos Decide™ ballot results after ballot closure. Developers can use this example as a starting point for designing their own contracts.

In our contract, we will launch a new election ballot and then **contractually** act on the results received by Telos Decide's `broadcast()` action. Upon hearing the broadcast, our contract will read the final results, determine the winning candidate, and then send an inline action back to Telos Decide to update a committee with the election winner.

## Example Guide

For this example, we will assume we have control of the `testaccounta` account on Telos Testnet and own a balance of `1200 TLOS`. These funds will be used to pay the setup fees for a new treasury, new committee, and new ballot, with some left over.

### 1. Deposit Funds

To pay for the necessary registration fees our example requires we will deposit `1200 TLOS` into Telos Decide by simply sending a `transfer()` with `telos.decide` as the recipient.

```text
cleos push action eosio.token transfer '["testaccounta", "telos.decide", "1200.0000 TLOS", "deposit"]' -p testaccounta
```

Telos Decide will catch this transfer and automatically create an account with your funds. From there, certain actions on the platform will require a fee that will be drawn from this balance \(currently limited to creating a treasury, committee, or ballot\).

{% hint style="info" %}
Note there is no TLOS fee for depositing or withdrawing on Telos Decide, and both can be done freely at any time.
{% endhint %}

### 2. Treasury Creation

To create the example treasury we simply call the `newtreasury()` action on the `telos.decide` contract. We will supply the following arguments:

* **manager:** `testaccounta`

  We will make ourself the manager, since we want to have control over the treasury operations for now.

* **max\_supply:** `500.0 EXMPL`

  We will limit the supply to 500.0 EXMPL, but we can adjust this later.

* **access:** `public`

  We will choose public, since we want anyone to be able to register themselves and join as a voter.

```text
cleos push action telos.decide newtreasury '["testaccounta", "500.0 EXMPL", "public"]' -p testaccounta
```

This will create a new public treasury with a max supply of 500.0 EXMPL tokens. Note that the treasury symbol is `1,EXMPL` since we chose to use 1 decimal place of precision and the EXMPL ticker.

Cost: `1000 TLOS`

### 3. Committee Registration

To create the example committee we will call the `regcommittee()` action on the `telos.decide` contract. We will supply the following arguments:

* **committee\_name:** `examplecmte`

  This will be the committee identifier used to locate the committee in the contract table.

* **committee\_title:** "Example Committee"

  This is the human readable title of the committee.

* **treasury\_symbol:** `1,EXMPL`

  The treasury symbol we created with the `newtreasury()` action. Don't forget the precision.

* **initial\_seats:** `["seat1", "seat2", "seat3"]`

  The seat names initially available after successful committee creation. More can be added later.

* **registree:** `testaccounta`

  The account registering the committee. This account will be billed for the committee creation.

```text
cleos push action telos.decide regcommittee '["examplecmte", "Example Committee", "1,EXMPL", ["seat1", "seat2", "seat3"], "testaccounta"]' -p testaccounta
```

Cost: `100 TLOS`

### 4. Ballot Creation

To create the example ballot we will call the `newballot()` action on the `telos.decide` contract. We will supply the following arguments:

* **ballot\_name:** `examplebal`

  The name identifier for our ballot. This must be unique.

* **category:** `election`

  The category the ballot falls under. Since the winning candidate on our ballot is going to be the first member of our committee, the election category is most appropriate.

* **publisher:** `testaccounta`

  The account who will set up and launch the ballot, and has the ability to cancel or delete if desired.

* **treasury\_symbol:** `1,EXMPL`

  The treasury that the ballot will be ran under. We will use the treasury we made earlier, and this means any `EXMPL` holder, including ourselves, will be able to cast a vote on this ballot.

* **voting\_method:** `1token1vote`

  We will choose 1token1vote, since we want votes for multiple candidates to have the voter's weight cast evenly between the selections. This is a design choice, and any other voting method could have been selected.

* **initial\_options:** `["testaccountx", "testaccounty", "testaccountz"]`

  We will place test accounts x, y, and z to be placed as options on the ballot. We could add more before opening up the ballot for voting, but won't for simplicity's sake.

```text
cleos push action telos.decide newballot '["examplebal", "election", "testaccounta", "1,EXMPL", "1token1vote", ["testaccountx", "testaccounty", "testaccountz"]]' -p testaccounta
```

Once the ballot has been registered, don't forget to actually begin voting be calling `openvoting()`. This can be done at any time, so we will wait until we finish setting up our example contract.

Cost: `30 TLOS`

### 5. Example Contract Build and Deployment

To build the example contract we will use the `build.sh` provided in this repository's contracts folder, but you can build with the `eosio-cpp` tool in the `eosio.cdt` if that is preferable.

```text
mkdir build && mkdir build/example

chmod +x build.sh

./build.sh example
```

To deploy the example contract to our `testaccounta` account, we will use the provided `deploy.sh` script, but you can deploy manually with the `cleos set contract` command as well.

```text
chmod +x deploy.sh

./deploy.sh example testnet
```

Once the contract is deployed we need to tell it to watch our new ballot and listen for the `broadcast()` action. To do this we simply call the `watchballot()` action. We will be pushing this transaction to the `testaccounta` account, since that's where we deployed our example contract. We'll give it the following arguments:

* **ballot\_name:** `examplebal`

  Tells our example contract to watch the `examplebal` ballot on Telos Decide.

* **treasury\_symbol:** `1,EXMPL`

  The treasury symbol used on the ballot.

* **committee\_name:** `examplecmte`

  The committee to update with the ballot winner.

* **seat\_name:** `seat1`

  The name of the seat to assign the winner to.

```text
cleos push action testaccounta watchballot '["examplebal", "1,EXMPL", "examplecmte", "seat1"]' -p testaccounta
```

Next, after telling our contract to watch our ballot, we need to give it permission to execute an inline action to the `assignseat()` action so we can immediately elect our winning candidate. To do this we want to add the virtual `eosio.code` permission to our contract's active authority with the `cleos set account permission` command, like so:

```text
cleos set account permission testaccounta active --add-code -p testaccounta
```

### 6. Open Ballot Voting

Now that we have our example contract set up and watching our ballot, we can finally open up our ballot for voting. This is done by simply sending an `openvoting()` action to Telos Decide.

Be aware that once voting has begun **no further changes to the ballot may be performed**. This is to preserve the integrity of the ballot and ensure voters can't be deceived by altering ballot information mid-vote. Ballots may still be cancelled, however.

We will supply the following arguments to our `openvoting()` action:

* **ballot\_name:** `examplebal`

  This is the name of the ballot to open for voting. Only the ballot publisher will be able to open ballots for voting.

* **end\_time:** `2019-11-14T13:00:00`

  This is the time that voting will close in UTC time. Format is `YYYY-MM-DDTHH:MM:SS`

```text
cleos push action telos.decide openvoting '["examplebal", "2019-11-14T13:00:00"]' -p testaccounta
```

Now that voting has been opened on our ballot, all that's left to do is wait for votes to roll in. Results can be seen in real time, as the ballot tracks the live vote count for each ballot option.

### 7. Closing Out The Ballot

Once the end time on the ballot has been reached, it will immediately stop accepting votes. The ballot can be properly closed out and the results broadcasted by calling the `closevoting()` action. We will supply the following arguments:

* **ballot\_name:** `examplebal`

  The name of the ballot to close.

* **broadcast:** `true`

  Since we want to broadcast the results back to our example contract, we will give true here.

Once complete, the ballot status will be changed to `closed` to show the ballot has been properly ended.

Since we chose to broadcast our results, an inline action has automatically been launched by Telos Decide to its own `broadcast()` action that then notifies the ballot publisher account.

The example contract we deployed earlier to the `testaccounta` account catches this `broadcast()` notification from Telos Decide and interprets the final ballot results to determine the winner. Once determined, our contract automatically executes an inline action to Trail's `assignseat()` action, which emplaces the winner into `seat1` on the example committee.

