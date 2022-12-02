# Truffle Deployment Guide

## Environment Setup

0\. Check whether you Mac has Homebrew installed:

If the command fails, then install Homebrew:

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

sudo apt install nodejs npm

3\. Install OpenZeppelin contracts. At the root of this project.

npm install openzeppelin-solidity

1.  1\.

    Replace the `mnemonic` variable content with YOUR secret words in `truffle.js`. (NOTE: your secret words should be held privately in your wallet)

var mnemonic = YOUR\_SECRET\_WORDS\_HERE;

Deploy the contract to the BSC testnet

truffle migrate --reset --network bsc\_testnet

OR, deploy the contract to the BSC mainnet

truffle migrate --reset --network bsc\_mainnet

4\. From the output of the above command, find the address of the `RubyETH` contract, suppose it is:

`0x05149A02DC230588964Dd6D6F196eF38d523c0Fa`

Update the Javascript code with the above address in `src/rubyClient.js`

rubyApp.contracts.rubyETHContract = new rubyApp.web3.eth.Contract(rubyETHabi, YOUR\_RUBYETH\_CONTRACT\_ADDRESS\_HERE);
