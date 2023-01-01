# Roadmap

### Timeline

2020 Q3

* ~~Project Establishment~~ <mark style="color:green;">**\[COMPLETED]**</mark>

2020 Q4

* ~~Research on functional encryption~~ <mark style="color:green;">**\[COMPLETED]**</mark>

2021 Q1-Q2

* ~~Official Whitepaper Release~~ <mark style="color:green;">**\[COMPLETED]**</mark>
* ~~Official Website Launch~~ <mark style="color:green;">**\[COMPLETED]**</mark>
* ~~Official Ruby community Launch~~ <mark style="color:green;">**\[COMPLETED]**</mark>

2021 Q3

* ~~Functional encryption library V1.0 released~~ <mark style="color:green;">**\[COMPLETED]**</mark>
* ~~Web3 Foundation Grant milestone 1 approved~~ <mark style="color:green;">**\[COMPLETED]**</mark>

Q4 2021

* ~~Micropayment Scheme and Relevant Substrate Module Released~~ <mark style="color:green;">**\[COMPLETED]**</mark>

Q1-Q2 2022

* ~~Web3 Foundation Grant milestone 2 approved~~ <mark style="color:green;">**\[COMPLETED]**</mark>

Q3 2022

* Substrate Builders Program application accepted
* Testnet V1.0 Launch
* Bug Bounty Program

Q4 2022

* Substrate Builders Program milestone 1 approved
* Mainnet V1.0 Launch

Q1 2023

* Access control for NFT-gated event V1.0 Launch

### Web3 Foundation Grant Milestones

~~**Milestone 1: Implement Cryptographic Modules**~~**  **<mark style="color:green;">**\[COMPLETED]**</mark>

The main deliverable of this milestone includes:&#x20;

* A cryptographic library written in Rust that implements the inner product functional encryption and quadratic polynomial functional encryption.&#x20;
* A substrate pallet that integrates the verification logic of the associated zero-knowledge proof for the legitimacy of the encrypted functional key.

| **Number** | **Deliverable**       | **Specification**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.         | Cryptographic modules | We will implement the cryptographic modules including inner product functional encryption and quadratic polynomial functional encryption \[MSHBM2019] and the associated zero-knowledge proof \[ZeroPool]. The cryptographic modules will be written in Rust and modified from the rust version of CiFEr library. We will build privacy-preserving classification and neural networks based on these modules. We will also implement a substrate pallet that integrates the verification logic of the associated zero-knowledge proof for the legitimacy of the encrypted functional key. |
| 2.         | Benchmark             | Perform unit tests on the individual algorithms to ensure their safety. Benchmark on the gas cost and throughput of the proposed module.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 3.         | Docker                | We will provide a dockerfile to demonstrate the usage of our modules.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

~~**Milestone 2: Client Implementation and Integration**~~**  **<mark style="color:green;">**\[COMPLETED]**</mark>

The main deliverable of the milestone is the client that can trigger the aforementioned cryptographic modules and the micropayment scheme and the necessary UI to enable the users to interact with all these algorithms.

| **Number** | **Deliverable** | **Specification**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.         | Client modules  | We will implement the client to support the key distribution and decryption of the functional encryption scheme \[MSHBM2019]. The client will also generate the transaction that can trigger the aforementioned cryptographic modules and the micropayment scheme \[MDJM2019], such as the encrypted functional key and zero-knowledge proof. We will provide a basic UI to take inputs from the users for all these algorithms and receive the outputs. More specifically, the UI will enable the data owner to input the raw data to generate the signed ciphertext and upload it to the cloud server. The UI will also allow the data purchaser to retrieve the functional key from the key authority and the ciphertext from the cloud and then perform the decryption. The UI will also register a qualified data source and allow a data owner to join the data monetization program when he/she meets the data source and the data owners to request a signature from a registered source, which will then be verified on-chain. Finally, it will also allow these entities to interact with the substrate module with the inputs and outputs defined in our architecture. |
| 2.         | Benchmark       | Perform unit tests on the individual algorithms to ensure their safety. Benchmark on the latency and usability of the proposed client functionalities.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 3.         | Docker          | We will provide a dockerfile to demonstrate the usage of our modules.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

### Substrate Builders Program Milestones

**Milestone 1: Implementation of CP-ABE library and modification of zero-pool library**

Implementation of ciphertext-policy attribute-based encryption (CP-ABE) library according to the standard on ABE proposed in ETSI tech specification. Different from our Web 3.0 grant delivery, the library will be full-fledged, and guarantee the following functionalities: The CP-ABE library will be chosen-ciphertext secure and support decentralized and multi authorities and attribute revocation. We will provide full documentation on how to use the CP-ABE library in practice. The existing zero-pool pallet for data monetization will be modified according to the new CP-ABE scheme. Since our project will focus on access control in our future development, we will adapt the data monetization part of our project to the access control requirement.

**Milestone 2: Decentralized Setup of CP-ABE scheme**

Provide a setup mechanism for the decentralized authorities. Add an API for a Ruby token holder to become an authority. This includes a substrate pallet for the holder to stake Ruby token before officially becoming a verified authority. A specification for the authority on how to validate the user’s attributes. This specification will indicate how to translate standard access control policy into attribute universe, etc. A standard for converting an access-control policy into an attribute policy that can be used by the underlying encryption algorithms. Establish a secure and authenticated channel for the transfer of public parameters from the authority to the encryptor. An API for the encryptor to respond to the request for encryption.

**Milestone 3: Revocation Mechanism of CP-ABE scheme**

A standard for the attribute revocation mechanism. The standard will include the specification of the revocation list, and the time-based, and counter-based secret key revocation. An API for the encryptor to re-encrypt the ciphertext before revocation. An XCMP message layer for the notification mechanism between the encryptor and the event triggered by the update of the revocation list. A procedure for the authority to perform attribute revocation duty. This will include a backend algorithm for the authority to set up and maintain the attribute universe and attribute revocation list. It will also have an API for the authority to interact with the substrate pallet to update the revocation list. Launch an access control service based on Substrate pallet.

### Future Plan

In phase 1, we will complete the implementation of cryptographic modules as a substrate pallet that integrates the verification logic of the associated zero-knowledge proof for the legitimacy of the encrypted functional key.

In phase 2, our goal is to deliver the micropayment scheme and enable the users to interact with all these algorithms in a working product.

Finally, our goal is to provide an essential open API and SDK from a high-level perspective with the above tools, fully powering the data monetization framework on Polkadot.

**Open API and SDK**

* A cryptographic library that implements the inner product functional encryption and quadratic polynomial functional encryption. A substrate module that integrates the verification logic of the associated zero-knowledge proof for the legitimacy of the encrypted functional key.&#x20;
* The client can trigger the aforementioned cryptographic modules and the micropayment scheme and the necessary UI to enable the users to interact with all these algorithms.
