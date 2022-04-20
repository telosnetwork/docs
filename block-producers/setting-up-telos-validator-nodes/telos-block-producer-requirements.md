---
description: What is required to become a Telos Block Producer node?
---

# Telos Block Producer Requirements

There are multiple phases of participation, with each level having more stringent requirements than the previous - this is intended to address the growing requirements of the network over time.

The specifications stated herein are subject to revision, as well as when the network will move from stage to stage - as determined by a vote of ⅔ + 1 of the current Block Producers at the time of the proposed revisions.

Regardless of their level of participation, to participate in the Telos Blockchain Network (TBN) at any phase - Block Producers candidates are required to provide, and abide by the following:

### **A. Disclosures**

* **Block Producer Account Name**
* **Block Producer Public Key**
*   **Block Producer Organization Info:**

    a. Candidate Name

    b. Candidate Website URL

    c. Candidate country of registration for registered entity or residence of primary owner if not  a registered entity as 2-letter ISO country coded.

    _d. Candidate server location(s)_

    &#x20;    i. Location name

    &#x20;    ii. Country as 2-letter country code

    &#x20;    iii. latitude

    &#x20;    iv. Longitude
*   **Network Emergency Contact(s)**

    a. Name

    b. Email address

    c. Phone number - in a non-public, password protected, repository commonly accessible to any of the 51 paid Block Producers and Standbys.
*   **Block Producer Entity Ownership**

    Disclosure of each beneficial owner of block producer entity along with percentage of ownership. \[enforced by smart contract]



    Disclosure of accepted third-party identification verification service and identification hash for each beneficial owner (\* to be implemented).

Make sure that the following is also available:&#x20;

* **A Mission** — What are you going to provide to the world as a Telos Validator? How will you spend your TLOS? Why should people vote for you?
* **Unique Telos block producer account** — This should not resemble the name of any current Telos Block producer Candidates. You can view all of the current Validators and Validator Candidates [here](https://telos.bloks.io).
* **A few servers running nodeos** — Virtual machines or even a desktop with a lot of RAM would be ok to start off. Some Telos Block producers are running on desktop hardware (i7 or i9 chips). You just need to provide the RAM that is required by Telos Mainnet and it increases at a rate of 1 KB/block currently. It is \~ 12.56 GB at the time of writing this guide.
* **Website** — Your website should have a `bp.json` ([example](https://www.alohaeos.com/bp.json)) at it's root, and links to an ownership disclosure ([example](https://www.alohaeos.com/ownership)), and a code of conduct ([example](https://www.alohaeos.com/conduct))).
* **Validator account creation for rewards** — Create a unique Telos Account that will be the name of your Block producer node. Telos Accounts are 12 characters long. For account creation, visit here:&#x20;
  * [Telos account creator](https://telos-account-creator.com)
  * [FREE Telos account via Sqrl Wallet](https://telosuk.io/how-to-create-a-free-telos-account/)

Please visit [https://www.telos.net/governance](https://www.telos.net/governance) and navigate towards Document: Block Producer Minimum Requirements for an up to date list of block producer hardware requirements per phase.

### B. Practises

1. &#x20;**Sync with an approved NTP server at least once per 24 hours.**
2. **Adoption of account blacklist maintained by the Elected Arbitrators.**

The next section will guide you through setting up a Telos Block Producer node.
