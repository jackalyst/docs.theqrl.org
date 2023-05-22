---
title: QRL Node
categories: node
description: The QRL Node documentation
tags: node
---

Running a QRL node strengthens the network, supports the decentralization and further verifies transactions on the network. This is an essential function of the decentralized architecture QRL relies on.

This allows you to run a private secure node to communicate with the QRL blockchain. 

You can use the node to connect the explorer, wallet, and ephemeral messaging features to the gRPC QRL functions. 

> There are various options available for connecting to the API and setup options for the node can be configured through a user set configuration file.
{: .info}


## Requirements

You can run QRL on most operating systems, though Ubuntu 18.04 is recommended.
{: .info}

- Support for AES-NI
- Support for avx2 (Used by keccak library for hashing functions)
- HDD with enough storage for the blockchain as it grows
- Reliable network connection 
- Python3.6
- 64 bit processor


## tl;dr

Abridged instructions for installing QRL on Ubuntu:

```bash
# Update and Upgrade packages
sudo apt update && sudo apt upgrade -y

# Install Required dependencies
{{ layout.v.qrlCommands.qrlRequirementsUbuntu }}

# Make sure setuptools is the latest
pip3 install -U setuptools

# Install latest service identity package
pip3 install service-identity==21.1.0


# Install QRL
{{ layout.v.qrlCommands.qrlInstall }}
```


If things worked correctly you will now find the `{{ layout.v.qrlCommands.startQRL }}
` package and the `qrl` package. Adding the `--help` flag to each will print the various function details.


## Getting Started


Installing QRL is simple, and is possible on most modern operating systems. The install relies on `python3.5` or newer and the `pip3` python package install system. 

__Update and Dependencies__

You will need to start with a fully updated system. You will also need a few additional packages depending on your setup. See the correct section for your OS and install all of the requirements.

## Ubuntu

### Install Ubuntu Node

Update your system ensuring you have the latest packages:

```bash
# Issue the following command to update software
sudo apt update && sudo apt upgrade -y
```

Now install all the required dependencies:

```bash
# Install the required packages for QRL
{{ layout.v.qrlCommands.qrlRequirementsUbuntu }}
pip3 install -U setuptools
pip3 install service-identity==21.1.0
```

Start the QRL ndoe

```bash
start_qrl
```

### Update Ubuntu Node

First, stop your node with ctrl+c.

Then double check you have the required dependencies installed

```bash
{{ layout.v.qrlCommands.qrlRequirementsUbuntu }}
pip3 install -U setuptools
```

After that, update your node with pip3

```bash
pip3 install -U qrl
```

When you're done updating, don't forget to start your node again!

```bash
start_qrl
```

## Redhat/fedora

Update:

```bash
# Update
dnf update 
```

Dependencies: 

```bash
# Install required packages
{{ layout.v.qrlCommands.qrlRequirementsRedhat }}
```

### MacOS

To build in OSX Please install `brew` if you have not already.

```bash
# Install brew with
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

This will prompt you through a few questions while it installs.

Having Issues? Please follow the instructions found at the brew main page: [https://brew.sh/](https://brew.sh/)

```bash
# Update brew
brew update
brew install python3 swig boost hwloc
```

You will need to install `cmake v3.10.3` manually.

[Please follow the guide from the cmake documantation](https://cmake.org/install/)

### Windows 10

Windows support in the current version is limited. An alternative is to install Ubuntu using the Linux Subsystem for Windows.

#### Ubuntu on Linux Subsystem for Windows (WSL)

You can run a full node in Windows utilizing the Windows Subsystem for Linux. There are a ton of guides out there on setting this up. Here are a few links to get you going.

The Windows Subsystem for Linux (WSL) is a new Windows 10 feature that enables you to run native Linux command-line tools directly on Windows, alongside your traditional Windows desktop and modern store apps.

You can follow [these instructions](https://msdn.microsoft.com/en-us/commandline/wsl/install-win10) to install Ubuntu using Linux Subsystem, 


#### Links - Installing Ubuntu in Windows 10

* [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/about)
* [Google Is Your Friend (install+ubuntu+in+windows+10)](https://www.google.com/search?hl=en&as_q=install+ubuntu+in+windows+10&as_epq=)
* [WSL Blog](https://blogs.msdn.microsoft.com/wsl/)



## Install QRL 

Now that we have a freshly updated system, the installation of QRL is a breeze, QRL uses python3 to install. The install is the same for all operating systems after you have installed the requirements. Using the Python3 package installer *pip3* we will install QRL.

Before we install QRL make sure setupTools is the latest. 

```bash
pip3 install -U setupTools
```
After this completes install QRL with:

```bash
{{ layout.v.qrlCommands.qrlInstall }}
```
This will install the QRL package and any required dependencies. 



## Start QRL Node

Now that we have QRL installed we can `start_qrl` and begin syncing the node. This will begin the node in the foreground of the shell. If you would like to continue using the shell you can either pass the `--quiet` flag or run the command in a `screen` session ( you will need screen installed ).


```bash
{{ layout.v.qrlCommands.startQRL }}
```

This will print out the details of the running QRL processes. For a more verbose output you can pass the `-l` option with `DEBUG, INFO,WARNING,ERROR,CRITICAL` depending on the level of information you need.

```bash 
{{ layout.v.qrlCommands.startQRL }} -l DEBUG
```

The node will sync the entire blockchain to your computer, make sure you have enough space. after syncing the chain you will begin seeing blocks added. Congrats, your QRL node is working. 


#### Help

If you would like to see all of the options you can pass along the command line simply add `--help` to the end of the command above.

```bash
{{ layout.v.qrlCommands.startQRL }} --help
```

This will print all of the various options available. 

```bash
usage: start_qrl [-h] [--mining_thread_count MINING_THREAD_COUNT] [--quiet]
                 [--qrldir QRL_DIR] [--no-colors]
                 [-l {DEBUG,INFO,WARNING,ERROR,CRITICAL}]
                 [--network-type {mainnet,testnet}]
                 [--miningAddress MINING_ADDRESS]
                 [--mockGetMeasurement MEASUREMENT] [--debug] [--mocknet]

QRL node

optional arguments:
  -h, --help            show this help message and exit
  --mining_thread_count MINING_THREAD_COUNT, -m MINING_THREAD_COUNT
                        Number of threads for mining
  --quiet, -q           Avoid writing data to the console
  --qrldir QRL_DIR, -d QRL_DIR
                        Use a different directory for node data/configuration
  --no-colors           Disables color output
  -l {DEBUG,INFO,WARNING,ERROR,CRITICAL}, --loglevel {DEBUG,INFO,WARNING,ERROR,CRITICAL}
                        Set the logging level
  --network-type {mainnet,testnet}
                        Runs QRL Testnet Node
  --miningAddress MINING_ADDRESS
                        QRL Wallet address on which mining reward has to be
                        credited.
  --mockGetMeasurement MEASUREMENT
                        Warning: Only for integration test, to mock
                        get_measurement
  --debug               Enables fault handler
  --mocknet             Enables default mocknet settings
```

## Configuration 

By default when the node is started it will **NOT** mine any coins. You will have to enable using a configuration file in the `{{ layout.v.qrlConf.qrlDir }}` directory. 

The configuration file is where you will change any options you want QRL to observe. You can grab a copy of the file and details about all of the settings in our [Configuration Guide](/node/configuration/)

The defaults can be used to run a QRL node, though you may need to change some of the directives for your use.


## Mining QRL

> If you want to mine using a QRL node, see the guide for [Mining QRL Solo](/mining/full-node) or the [pool guide](/mining/pool-mining) to get started.
{: .info}