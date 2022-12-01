# Roadmap

2020 Q3 - Project Establishment

2020 Q4 - Draft of Whitepaper

2021 Q1 - Official Whitepaper Release

2021 Q1 - Official Website Launch

2021 Q1 - Core and zkSNARKS Implementation Release

2021 Q2 - Token and Dapp source code Release

2021 Q2 - Liquidity Reward Program

2021 Q3 - Protocol and Product Launch

2021 Q4 - Implementing the Bridge to DeFi Protocols

2021 Q4 - Integrating More Customized Functions

#### Milestone 1: Ruby Substrate Modules and Cross-chain Bridge Implementation <a href="#milestone-1-ruby-substrate-modules-and-cross-chain-bridge-implementation" id="milestone-1-ruby-substrate-modules-and-cross-chain-bridge-implementation"></a>

The main deliverable of this milestone is Ruby substrate pallet that supports: mint, transfer, redeem, lock and unlock functionalities. The substrate modules will support both the mainstream tokens issued in the Polkadot ecosystem such as DOT and Kusama and the cross-chain payment of ERC-20 tokens.

|                                                        |                                                                                                                                                                                                                                        |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ruby Substrate module for private payment**          | We will implement the zero-knowledge proof schemes and create a Substrate module that incorporates the verification logic for the aforementioned modules. It will support the verification of mint, transfer, redeem, lock and unlock. |
| **A cross-chain bridge between Ethereum and Polkadot** | The bridge will map ERC-20 tokens to the Polkadot ecosystem and facilitate their private payment in the Polkadot ecosystem.                                                                                                            |
| **Benchmark**                                          | Benchmark on the throughput and gas cost of the proposed modules                                                                                                                                                                       |
| **Docker**                                             | We will provide a dockerfile to demonstrate the usage of our modules                                                                                                                                                                   |

#### **Milestone 2: Ruby Client Implementation and Integration** <a href="#milestone-2-ruby-client-implementation-and-integration" id="milestone-2-ruby-client-implementation-and-integration"></a>

The main deliverable of this milestone is the client that can generate the transactions that can trigger the aforementioned contracts.

|                      |                                                                                                                                                                                                                                                                      |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ruby client**      | We will implement the client that supports the Register, CreateMintTx, CreateTransferTx, CreateRedeemTx, CreateLockTx, and CreateUnlockTx algorithms. The client will be able to generate the necessary transactions to trigger the corresponding substrate modules. |
| **Anonymity mining** | Through combining the lock and mint, and unlock and redeem modules, we will implement anonymity mining functionality, which allows the users to mine the private tokens and unlock the private tokens after a certain period of time.                                |
| **Benchmark**        | Benchmark on the usability and latency of the proposed client functionalities.                                                                                                                                                                                       |
| **Docker**           | We will deploy the client on Kusama or Rococo and engage our community on the testing of our product.                                                                                                                                                                |
