# Substrate/Polkadot Integration

The Ruby Protocal will be implemented as Substrate modules. More specifically, we will build a Raze substrate pallet that supports:

* The user could mint an anonymized token by invoking the Mint module. It will support all tokens issued on the Polkadot blockchain such as the native DOT or Kusama, as well as ERC-20 tokens.
* A user who owns a Raze account could transfer the anonymized token to another Raze account by running the Transfer module to hide the identities of the involved parties and the transferred amount.
* A user could run the Redeem module to convert the anonymized token back to its native form.
* The lock and unlock modules will allow the users to participate in the anonymity mining, and thus provide incentives to the users to join the Ruby Protocal and thus increase the anonymity set.

The ledger state will mainly keep a record of the Raze accounts, the encryption of balances, and the pending transfer tables, etc.
