# Backend Functionalities

The backend functionalities are all defined in `src/ruby/client_base.js` , which is mostly self-explained with rich comments. We list 4 main APIs that are most important here:

## Register

<mark style="color:red;">`ClientBase.register(secret)`</mark>

User inputs his or her private `secret` and the algorithm will generate a Ruby public/private key pair. The Ruby public key will be sent in a transaction to register an account in the contract.

## Mint

<mark style="color:red;">`ClientBase.mint(value)`</mark>

Create a transaction to convert a specified amount of the user's plain tokens to an equivalent amount of encrypted Ruby tokens.

## Redeem

<mark style="color:red;">`ClientBase.redeem(value)`</mark>

Create a transaction to convert a specified amount of the user's encrypted Ruby tokens back to an equivalent amount of plain tokens. Note that the transaction will include necessary cryptographic zeroknowledge proof to guarantee that this is a **valid** burn operation.

## Transfer

<mark style="color:red;">`ClientBase.transfer(receiver, value, decoys)`</mark>

Create a transaction to transfer a specified amount of the user's encrypted Ruby tokens from the current user to a receiver. Note that the transaction will include necessary cryptographic zero-knowledge proof to guarantee that this is a `valid` transfer operation.
