# Smartcontract Caller [![License](https://img.shields.io/github/license/aliceincryptoland/smartcontract-caller)](https://github.com/aliceincryptoland/smartcontract-caller/blob/master/LICENSE) [![Smartcontract Caller Build & Deploy](https://img.shields.io/github/workflow/status/aliceincryptoland/smartcontract-caller/Build%20&%20Release)](https://github.com/aliceincryptoland/smartcontract-caller/actions/workflows/main.yml) [![GitHub release](https://img.shields.io/github/v/release/aliceincryptoland/smartcontract-caller)](https://github.com/aliceincryptoland/smartcontract-caller/releases)

The **Smartcontract Caller** is a standalone node-webkit app, that enables users to call a contract method on an EVM-compatible blockchain by uploading input configuration files in `JSON` format.

> Disclaimer : This is a badly and quickly written project, with uneccesary machinery, and a **very** client-heavy distribution.

## Supported Blockchains:

- Binance Smart Chain - Mainnet
- Binance Smart Chain - Testnet

## Instructions

1. Download the latest release. Choose version accordingly.
1. Unzip the downloaded app folder.
1. Download the configuration template files (Release > config-template.zip).
1. Edit the configuration templates. References for parameter format are given below.
1. Launch the .exe in the app folder.
1. Upload the edited configuration files in the launched app.
1. Execute and wait for your call result or transaction hash.

## Configuration files format

All files should be in `JSON` format.

### Secrets

`PRIVATE_KEY` : the private key that you wish to sign transactions with.

> This parameter is of type `string`.

### Parameters

- `BLOCKCHAIN`: Choose the blockchain you wish to connect to. For now the only options are: _bsc-mainnet_ or _bsc-testnet_.
- `PUBLIC_ADDRESS`: Your public address, associated with your private key.
- `CONTRACT_ADDRESS`: The address of the contract you wish to call.
- `METHOD_NAME`: Name of method you wish to call. You should include it's solidity parameter types, _e.g. transfer(address,uint256)_.
- `METHOD_TYPE`: Either _read_ or _write_ . _Read_ methods do not alter contract state (don't need to sign anything or pay fee) whereas _write_ methods do.
- `METHOD_PARAMETERS`: All the parameters that are needed to call the fucntion. They should be placed in an array. All parameters of solidity type `address` should be a placed in the array as a `string`, all number types should be written as `int` or `float` and be in **ethers** (the program will multiply by 10^18 to convert it in **wei**).\
  _e.g. for the method_ transfer(address,uint256) _parameters could be_ ["0x437C2AD9E62e3f9Ef8d76Dd6Bb1A5deF35B37Cc7", 123].

> Except for `METHOD_PARAMETERS` which is an `Array`, all other parameters are of type `string`.

### ABI

- Copy-paste the ABI of the contract you wish to call from a blockscanner (e.g. Etherscan, BSCScan, ...). in the templateABI.json file.
