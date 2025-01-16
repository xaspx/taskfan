# 🛹 Master Solana Frontend

<br>


## 🛹 Introduction to [@solana/web3.js](https://solana-labs.github.io/solana-web3.js/)


### Demos

<br>


* [Demo 1: Interacting with the Blockchain](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/01_connecting_to_the_blockchain)
* [Demo 2: Non-native Programs](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/02_non_native_programs)

<br>


---


## 🛹 Interacting with Wallets 

<br>

* A wallet is a software or hardware that stores a secret key to keep it secure and handle secure transaction signing.

* Solana's [@solana/wallet-adapter-base and @solana/wallet-adapter-react.-Adapter](https://github.com/anza-xyz/wallet-adapter) libraries simplify the process of supporting wallet browser extensions.

* `@solana/wallet-adapter-react` allows us to persist and access wallet connection states through hooks and context providers:
    - `useWallet`
    - `WalletProvider`
    - `useConnection`
    - `ConnectionProvider`

* Any use of `useWallet` and `useConnection` should be wrapped in `WalletProvider` and `ConnectionProvider`.

* `@solana/wallet-adapter-react-ui` allows the creation of custom components for, such as:
    - `WalletModalProvider`
    - `WalletMultiButton`
    - `WalletConnectButton`
    - `WalletModal`
    - `WalletModalButton`
    - `WalletDisconnectButton`
    - `WalletIcon`



<br>

---

### Demos

<br>



* [Demo 3: Interacting with Wallets](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/03_wallets_ping)
* [Demo 4: Sending Transactions with Wallets](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/04_wallets_tx)


<br>

---

## 🛹 Serializing Data and PDA

<br>

### Instruction Serialization

<br>

* Instruction data must be serialized into a byte buffer to send to clients. 

* Every transaction contains:
    - an array with every account it intends to read or write
    - one or more instructions
    - a recent blockhash
    - one or more signatures

* Every instruction contains:
    - the program ID (public key) of the intended program
    - an array listing every account that will be read from or written to during execution
    - a byte buffer of instruction data

<br>

---

### Libraries

* [@solana/web3.js](https://solana-labs.github.io/solana-web3.js/) simplifies this process, so developers can focus on adding instructions and signatures. 
    - The library builds the array of accounts based on that information and handles the logic for including a recent blockhash.


* To facilitate this serialization process, we can use the [Binary Object Representation Serializer for Hashin (Borsh)](https://borsh.io/) and the library [@coral-xyz/borsh](https://github.com/coral-xyz).
    - Borsh can be used in security-critical projects as it prioritizes consistency, safety, and speed and has a strict specification.

<br>

---

### PDA

<br>

* Programs store data in PDAs (Program Derived Addresses), which can be thought of as a key-value store. The address is the key, and the data inside the account is the value.
    - Like records in a database, with the address being the primary key used to look up the values inside.

* PDAs do not have a corresponding secret key. 
    - To store and locate data, we derive a PDA using the `findProgramAddress(seeds, program_id)` method.

* The accounts belonging to a program can be retrieved with `getProgramAccounts(program_id)`.
    - Account data needs to be deserialized using the same layout used to store it in the first place.
    - Accounts created by a program can be fetched with `connection.getProgramAccounts(program_id)`.



<br>

---

## 🛹 RPC Pagination 

<br>

* RPC calls can be used to paginate, order and filter deserialized account data, through some configuration options for the `getProgramAccounts`:
    1. You can fetch a large number of accounts without their data by filtering them to return just an array of public keys.
    2. Once you have a filtered list of public keys, you can order them and fetch the account data they belong to.

* `dataSlice` lets you provide two things:
    - `offset`,  the offset from the beginning of the data buffer to start the slice
    - `length`, the number of bytes to return, starting from the provided offset

<br>

```javascript
const accountsWithoutData = await connection.getProgramAccounts(
  program_id,
  {
    dataSlice: { offset: 0, length: 0 }
  }
)

const accountKeys = accountsWithoutData.map(account => account.pubkey)
```

<br>

* `filters` let you match specific criteria, which can have objects matching the following:
    - `memcmp`, compares a provided series of bytes with program account data at a particular offset. Fields:
        - `offset`, the number to offset into program account data before comparing data
        - `bytes`, a base-58 encoded string representing the data to match; limited to less than 129 bytes
        - `dataSize`, compares the program account data length with the provided data size
 


<br>

----

## 🛹 `create-solana-dapp`

<br>

* For full-stack development, [create-solana-dapp](https://github.com/solana-developers/create-solana-dapp) is an awesome CLI for creating Solana dApps on the fly.

* Supported UI frameworks:
    - ReactJS
    - NextJS

* Supported on-chain program frameworks:
    - Anchor


<br>


---

## 🛹 Demos

<br>

* [Demo 5: Serializing Custom Data with PDA I](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/05_serialize_custom_data)
* [Demo 6: Serializing Custom Data with PDA II](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/06_serialize_custom_data_II)
* [Demo 7: Example with create-dapp-cli](https://github.com/urani-labs/solana-dev-onboarding-rs/tree/main/demos/frontend/07_create_dapp_cli)