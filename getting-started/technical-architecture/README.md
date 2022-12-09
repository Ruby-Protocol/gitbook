---
description: A Private Data Management Layer for Web 3.0
---

# Technical Architecture

### Layers Structure

**Policy Management Layer**

The policy management layer defines the access control policy of the functional encryption scheme in the specific application scenarios. For instance, in the case of private data sharing between TradFi and DeFi, it will be the regulatory authorities and users who will be responsible for defining exactly what kind of private KYC information is allowed to leak to what kind of third-party DeFi apps. In the case of NFT-gated events, it will be the projects that issue NFTs that define the access control policy. The policy management layer will also specify exactly what type of policy information is privacy-sensitive and thus needs to be confidential.

**Storage Layer**

The storage layer is responsible for storing the encrypted message under functional encryption scheme. We will adopt a chosen-ciphertext secure attribute-based encryption/functional encryption scheme to guarantee the integrity and authenticity of the underlying message. The digital watermarking technology will add an additional authenticity guarantee to the underlying message.

**Credential Issuance Layer**

The credential issuance layer is the anchor of the security of Ruby protocol. It will be responsible for setting up all the key authorities in the system. The key authorities will be responsible for verifying the user and distributing keys corresponding to attributes and policy depending on the types ABE/FE we adopt in the concrete application scenarios. The credential issuance layer will be run collectively by the RubyDAO governors and regulatory authorities.

**Application Layer**

The application layer will interact with the blockchain apps, be it DeFi apps or NFT projects. It will be responsible for providing project requirements of blockchain apps and interacting with the entities responsible for the policy management to specify the privacy requirement of the blockchain apps. It will provide suitable APIs for these projects so that Ruby’s privacy protection feature can be used in a plug-in-and-play manner.

#### **Platform Pillars** <a href="#platform-pillars" id="platform-pillars"></a>

* **Data Management Framework**
* **Access Control Mechanism**
* **Private Micropayment System**
* **Digital Watermarking Technique**

The main features the Ruby system will guarantee are as follows:

* **Fine-grained Data Privacy:** Our access control policy will be well-defined so that it is attunedto the specific application scenarios. A too general access control policy might render it unusable in reality given it might leak too little information on the users. On the other hand, a too specific access control policy will leak too much private information of the users. Therefore, the stakeholders of Ruby protocol will periodically update the policy management standard so that it can concord with the demand of real-world use cases and the latest regulation.
* **Data Quality and Source Assurance**: Ruby guarantees the data coming from the right source and has the highest quality in the sense that it is not guaranteed to be authentic, but also up-to-date.
* **Policy Updateability**: Since regulation and access control policy always change, our system is malleable and updateable so that all apps dependent on the policy can change swiftly once the policy changes.
* **Attribute and Policy Revocability**: Since the attribute value or attribute policy for a secret key might change with time, we should provide a mechanism to revoke the respective secret key. For instance, consider the attribute “age”, a user’s age changes constantly as time goes by.
* **ZKP and Micropayment**: Ruby employs the zkp and micropayment schemes in our system architecture to build a data monetization framework that can accrue the value transferred across different actors to the Ruby token.
* **Multiple Use Cases**: Ruby can serve as a fine-grained access control gateway for data flow in different application scenarios, including private data sharing platform between TradFi and DeFi, NFT-gated or DID-gated access control, and regulatory-compliant tokenized security issuance, etc.
