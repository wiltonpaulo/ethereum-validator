# Ethereum 2.0 Validator Deployment Documentation

## Table of Contents

- [Ethereum 2.0 Validator Deployment Documentation](#ethereum-20-validator-deployment-documentation)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
    - [Overview](#overview)
    - [Purpose of the Document](#purpose-of-the-document)
  - [Prerequisites](#prerequisites)
    - [Hardware Requirements](#hardware-requirements)
    - [Software Requirements](#software-requirements)
  - [Installation](#installation)
    - [Initializing the Validator](#initializing-the-validator)
    - [Download and Install (Geth)](#download-and-install-geth)
      - [The following command enables the launchpad repository:](#the-following-command-enables-the-launchpad-repository)
      - [These commands install the core Geth software](#these-commands-install-the-core-geth-software)
    - [Installing the Client (Prysm)](#installing-the-client-prysm)
      - [Download and Install](#download-and-install)
      - [Generate JWT Secret](#generate-jwt-secret)
      - [Run an execution client](#run-an-execution-client)
  - [Validator Configuration](#validator-configuration)
    - [Key Generation](#key-generation)
    - [Obtaining Goerli ETH](#obtaining-goerli-eth)
    - [Initializing the Validator](#initializing-the-validator-1)
  - [Deposit and Registration](#deposit-and-registration)
  - [Validator Activation](#validator-activation)
  - [References](#references)

## Introduction
### Overview
Ethereum 2.0 is an upgrade to the Ethereum blockchain that introduces a new consensus mechanism called Proof-of-Stake (PoS). This documentation provides detailed instructions for deploying an Ethereum 2.0 validator on the Goerli Testnet.

### Purpose of the Document
The purpose of this document is to guide DevOps/SRE engineers in configuring an Ethereum 2.0 validator on the Goerli Testnet. It aims to provide clear and concise instructions to ensure a smooth deployment process.

## Prerequisites
### Hardware Requirements
Before deploying the Ethereum 2.0 validator, ensure that your system meets the following hardware requirements:
- A computer with at least 8GB of RAM
- Sufficient storage space for the Ethereum 2.0 client and validator data

### Software Requirements
Ensure that the following software is installed on your system:
- Ubuntu 22.04: Operating System tested to work with Ethereum 2.0 client.
- Prysm v4.0.5: Ethereum 2.0 client implementation. (latest)

## Installation

### Initializing the Validator

### Download and Install (Geth)

#### The following command enables the launchpad repository:
sudo add-apt-repository -y ppa:ethereum/ethereum

#### These commands install the core Geth software
sudo apt-get update
sudo apt-get upgrade geth

### Installing the Client (Prysm)

Prysm is an implementation of the Ethereum proof-of-stake consensus specification. In this quickstart, you’ll use Prysm to run an Ethereum node and optionally a validator. This will let you stake 32 ETH using hardware that you manage.

#### Download and Install

   ```shell
   $ mkdir prysm && cd prysm
   $ curl https://raw.githubusercontent.com/prysmaticlabs/prysm/master/prysm.sh --output prysm.sh && chmod +x prysm.sh
   ```

#### Generate JWT Secret

   ```shell
   $ USE_PRYSM_VERSION=v4.0.5
   $ ./prysm.sh beacon-chain generate-auth-secret
   ```
Prysm will output a jwt.hex file path. 

#### Run an execution client
   ```shell
   $ geth --goerli --http --http.api eth,net,engine,admin --authrpc.jwtsecret /path/to/jwt.hex 
   $ [client-command] --version
   ```

## Validator Configuration
### Key Generation
1. Generate your validator keys by following the instructions provided by your chosen Ethereum 2.0 client.
2. Safely store the validator keys, including the public and private key, in a secure location.

### Obtaining Goerli ETH
1. Visit the Goerli Testnet faucet website (e.g., [example-faucet-url]) and provide your Ethereum address to receive Goerli ETH.
2. Complete the necessary steps to obtain Goerli ETH, following the instructions provided on the faucet website.

### Initializing the Validator
1. Open a terminal and navigate to the directory where the Ethereum 2.0 client is installed.
2. Initialize the Ethereum 2.0 client with the following command:
   ```shell
   $ [client-command] init --datadir [validator-data-dir]
   ```
3. Configure the Ethereum 2.0 client to connect to the Goerli Testnet with the appropriate network settings.

## Deposit and Registration
1. Submit a deposit transaction to the Ethereum

 2.0 deposit contract using the following steps:
   - Transfer the required amount of Goerli ETH to the deposit contract address.
   - Include the validator public key during the deposit transaction.
2. Wait for the deposit transaction to be confirmed, which may take some time.

$ https://github.com/ethereum/staking-deposit-cli#for-linux-or-macos-users

## Validator Activation
1. Once the deposit transaction is confirmed, monitor the Ethereum 2.0 network for the activation of your validator.
2. The activation process may take some time, as it requires sufficient validators and time to reach the activation threshold.

## References
- [Ethereum 2.0 Documentation](https://ethereum.org/eth2/)
- [Installing Geth](https://geth.ethereum.org/docs/getting-started/installing-geth)
- [Quickstart: Run a node and (optionally) stake ETH using Prysm](https://docs.prylabs.network/docs/install/install-with-script)
