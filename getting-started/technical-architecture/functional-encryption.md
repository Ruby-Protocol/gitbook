# Functional Encryption

### Background <a href="#background" id="background"></a>

There are three relevant projects to Ruby: the first one is perhaps the Enigma project, a privacy protocol that enables the creation of decentralized applications (DApps) that guarantee privacy. The protocol Enigma is based on secure multi-party computation (MPC). The second one, In- sights Network, is a data exchange protocol based on combining blockchain technology, Substrate module, and MPC. It is based on the EOS blockchain and a custom MPC system. The third one, NuCypher, is a cryptographic infrastructure for privacy-preserving applications. Its main technology is threshold proxy re-encryption and fully homomorphic encryption.

There are several different ways of implementing an MPC protocol: threshold homomorphic encryption, garbled circuit, and secret sharing. The general idea of MPC is to outsource private data (either in the form of secret shares or homomorphic encryption) to a few separate computing parties so that they can perform confidential computation over the encrypted data. Directly applying MPC to fine-grained data monetization is problematic in the sense that once the data is outsourced, the data owner does not retain any control over what type of computation can be performed by the computing party. In other words, individual privacy is now at the mercy of these computing parties, which is against the owner-centric ethos of fine-grained data management, where the access control policy should be defined by the data owner and enforced by the algorithm.

On the other hand, functional encryption was specifically proposed and tailored for enforcing fine-grained access control over encrypted data. Compared with traditional public-key encryption schemes that only allow the message receiver to either decrypt the whole data set or nothing, functional encryption allows the sender to determine exactly which part of the message can be decrypted by exactly which kinds of receivers. By allowing the data owner to define the access control policy, the owner has full control over what type of access the data purchaser can have over the encrypted data. The only decryption result the data querier will be able to retrieve is the predefined function evaluation.

### Introduction <a href="#introduction" id="introduction"></a>

Function encryption was first proposed by Boneh, Sahai and Waters in 2011. This encryption al- gorithm broke the original ”All-or-Nothing” data query mode. The computing results of functional encrypted data can be obtained without revealing the plaintext content.A classic Functional Encryption Scheme contains four algorithms, namely:

* FE.Setup: (PK,MSK) ← Setup(1λ). The setting algorithm is used to generate the masterkey (MSK) and public key (PK)
* FE.KeyGen: SK ← KeyGen(MSK, k). The key generation algorithm is used to generate thekey for the function fk.
* FE.Enc: C ← Encrypt(PK, x). Encryption algorithm is used to encrypt data.
* FE.Dec: y ← Decrypt(SK,C). The decryption algorithm is used to safely calculate thefunction value y = fk(x). The above is a general form of function encryption. In order to realize that users can achievefine-grained control of their data, that is to say, the data owner can specify who can access the encrypted data and has complete control over the data, Ruby will use the Ciphertext-Policy ABE (CP-ABE) or Key-Policy ABE (KP-ABE) algorithm in the Functional Encryption algorithm to encrypt their personal data. The algorithms have to be CCA secure to guarantee the authenticity of the underlying message. The encryption algorithms will also have a revocation mechanism to ensure the access policy can be updated periodically. For more details on the encryption scheme, the interested readers are referred to our yellowpaper.

### ABE Scheme <a href="#abe-scheme" id="abe-scheme"></a>

Based on the ABE scheme, Ruby will support the revocation and restoration of user attributes. The execution includes 7 steps:

1\. FE.Setup: The initialization algorithm is a randomization one, and the initialization only generates the system public key PK and the system master secret key MSK.

2\. FE.Setup.Cancel: The input parameter is PK, a prime number field P is generated, and list=1 is calculated for each attribute att. The algorithm outputs the initialized P, map\<userGID,prime> and map\<att,list>. The list is not a common one but a large, prime number, which is used to record whether it has been revoked.

3\. FE.KeyGen: By the set S provided by PK, MK and data requesters, the trusted authorization center generates the user secret key UK associated with the attribute set for the data requesters. Apply a prime number for the user in the prime number field, delete this prime from P to ensure that the primes obtained by different users are varied, and then store the prime number in the mapping table map\<userGID,prime>.

4\. FE.Enc: The input parameters of the encryption algorithm (randomization algorithm) are PK, the message to be encrypted M, the access control structure associated with the access policy, and the ciphertext based on attribute encryption is output.

5\. FE.Dec: Decryption is a deterministic algorithm, executed by the data requester. Decryption is divided into two steps. The first step is to access the leaf node of the policy tree, let i = att(x), where x represents the leaf node of the ciphertext policy access tree. If i ∈ S, the algorithm obtains the revocation list corresponding to this attribute list and modulo list% prime. If the value is not 0, it means that the user has not been revoked. If it is 0, it means that it has been revoked and the decryption is over. Step 2: After the verification of Step 1 is passed, the algorithm enters UK and ciphertext M. If the attribute set satisfies the access Strategy, the algorithm can successfully decrypt the ciphertext M.

6\. User.Attribute.Cancel: att is the algorithm input parameter; list is the cancellation list corresponding to the attribute; and prime is the prime number prime corresponding to the user. When att of a user is cancelled, DO takes out the prime corresponding to the user and the list corresponding to the attribute from the mapping tables map\<user,prime> and map\<att,list> respectively, and calculates list’=listprime. The revocation list corresponding to the attribute att is updated to list’.

7\. User.Attribute.Recovery: att is the algorithm input parameter; list is the cancellation list corresponding to the attribute; and prime is the prime number corresponding to the user. The cancellation of the user may be temporary. When the user re-owns the attribute att, DO takes out the prime number corresponding to the user and the list corresponding to the attribute from the mapping tables map\<user,prime> and map\<att,list> respectively, and calculate list’=listprime. The revocation list corresponding to the attribute att is updated to list’.

### Attribute and Function Management <a href="#attribute-and-function-management" id="attribute-and-function-management"></a>

**User Management**

Basic information owned by the user (minimum data set): GID (provided by CA or business side, but overall uniqueness must be guaranteed), CP-ABE user attributes (provided by the business side), unique prime number (provided by the CA user registration unit), private key (generated by CA user private key generation unit). The user submits information (GID, CP-ABE user attribute, unique prime number) to the CA, applies for registration and generates a user private key.

**Modification of Access Control Policy**

In practical engineering applications, better choose the cancellation scheme with low complexity,

low computing cost, and simple implementation. Therefore, the policy cancellation scheme adopted in this design is as follows: Revoke users through a fixed-length cancellation list record, so that the cancellation process does not need to update the secret keys of the system and related users, which can greatly reduce the computational burden caused by the cancellation.

**Cancellation**

User attribute cancellation: att is the algorithm input parameter; list is the cancellation list; prime is the prime number corresponding to the user prime. When the att of a user is cancelled, DO takes out the prime corresponding to the user and list corresponding to the attribute from the mapping tables map\<user, prime> and map\<att, list> respectively, and calculates list’=listprime. The cancellation list corresponding to the attribute att is updated to list’.

**Recovery**

User attribute restoration: att is the algorithm input parameter; list is the cancellation list corresponding to the attribute; prime is the prime number corresponding to the user. The can- cellation of the user may be temporary. When the user re-owns the att, DO takes out the prime number and the cancellation list from the mapping tables map\<user,prime> and map\<att,list> respectively, and calculate list’=listprime. The cancellation list corresponding to the attribute att is updated to list’.
