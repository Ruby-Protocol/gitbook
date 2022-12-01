# Backend Functionalities

The backend functionalities are all defined in `src/raze/client_base.js` , which is mostly self-explained with rich comments. We list 4 main APIs that are most important here:

`ClientBase.register(secret)`

User inputs his or her private `secret` and the algorithm will generate a Raze public/private key pair. The Raze public key will be sent in a transaction to register an account in the contract.

Create a transaction to convert a specified amount of the user's plain tokens to an equivalent amount of encrypted Raze tokens.

Create a transaction to convert a specified amount of the user's encrypted Raze tokens back to an equivalent amount of plain tokens. Note that the transaction will include necessary cryptographic zeroknowledge proof to guarantee that this is a **valid** burn operation.

`ClientBase.transfer(receiver, value, decoys)`

Create a transaction to transfer a specified amount of the user's encrypted Raze tokens from the current user to a receiver. Note that the transaction will include necessary cryptographic zero-knowledge proof to guarantee that this is a `valid` transfer operation.
