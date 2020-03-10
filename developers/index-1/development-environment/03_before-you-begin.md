---
content_title: '1.2: Before You Begin'
link_text: '1.2: Before You Begin'
---

# Before You Begin

## Step 1: Install binaries

To get started as quickly as possible we recommend using pre-built binaries. Building from source is a more advanced option but will set you back an hour or more and you may encounter build errors.

\[\[info\]\] \| You can find how to build EOSIO from source [here](https://developers.eos.io/manuals/eos/latest/install/build-from-source/).

The below commands will download binaries for respective operating systems.

### Mac OS X Brew Install:

```text
brew tap eosio/eosio
brew install eosio
```

\[\[info\]\] \| If you don't have Brew installed, follow the installation instructions on the [official Brew website](https://brew.sh/).

### Ubuntu 18.04 Debian Package Install:

```text
wget https://github.com/EOSIO/eos/releases/download/v2.0.0/eosio_2.0.0-1-ubuntu-18.04_amd64.deb
sudo apt install ./eosio_2.0.0-1-ubuntu-18.04_amd64.deb
```

### Ubuntu 16.04 Debian Package Install:

```text
wget https://github.com/EOSIO/eos/releases/download/v2.0.0/eosio_2.0.0-1-ubuntu-16.04_amd64.deb
sudo apt install ./eosio_2.0.0-1-ubuntu-16.04_amd64.deb
```

### CentOS RPM Package Install:

```text
wget https://github.com/EOSIO/eos/releases/download/v2.0.0/eosio-2.0.0-1.el7.x86_64.rpm
sudo yum install ./eosio-2.0.0-1.el7.x86_64.rpm
```

\[\[warning\]\] \| If you have previous versions of eosio installed on your system, please uninstall before proceeding. For detailed instructions, see [here](https://github.com/EOSIO/eos/blob/master/README.md).

## Step 2: Setup a development directory, stick to it.

You're going to need to pick a directory to work from, it's suggested to create a `contracts` directory somewhere on your local drive.

```text
mkdir contracts
cd contracts
```

## What's Next?

* [Install the CDT](https://github.com/telosnetwork/docs/tree/6ab1055a149d12ea9ad55d46f0ca92a2ac1b5e98/developers/platform/getting-started/02_development-environment/04_install-the-CDT.md): Steps to install the EOSIO Contract Development Toolkit \(CDT\) on your system.

