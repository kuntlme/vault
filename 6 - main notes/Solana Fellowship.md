# Rust and Solana Roadmap

## General Languages - TS and Rust

### Client Side Sol

1. Read about blockchains - BTC whitepaper.
2. Cryptography, hashing, encryption, public key cryptography.
3. ECDSA, ED25519 curves.
4. Create a wallet on solana, airdrop yourself some SOL, preferably on-ramp some SOL from Binance.
5. Ownership, Authorities
6. **Read about the Accounts model on Solana. Data model, various types of accounts**
    1. Data accounts
    2. **PDAs** 
        1. Program signing
        2. Determinism
    3. Program accounts
    4. Program data accounts
7. Transactions, instructions, Instruction formats.
8. What makes Solana fast - Transaction inputs on Solana.
9. RPCs, interacting with the blockchain via RPCs.
10. Wallet adapters. Create a few DApps. Let a user place trades on meme coins.
11. IDLs and reading contracts. Official clients vs parsing account data yourself.
12. Borsh for serializing/deserialising. Borshjs for deserializing on the frontend.
13. Projects - Memecoin marketplace - dexscreener/vector

---

## Rust

1. Learn the following in rust
    1. Data types
    2. Variables
    3. Loops
    4. Functions
    5. Structs 
    6. Enums
    7. Pattern matching
    8. Package management — Solana Program, Solana SDK, Borsh
    9. Mutability, Memory management, ownership,
    10. Referencing and borrowing 
    11. Options, Errors, Error handling
    12. Lifetimes
    13. Traits
    14. Generics
    15. Macros

---

### Smart Contracts

1. Hard prerequisite - Data model on Solana, Transaction inputs.
2. Native contracts in Rust.
3. Staking contract, escrow contract, marketplace contract, Governance contract, Vault contract, AMM.
4. Write the same contracts in Anchor.
5. Write the same contracts in Pinnocio.

---

## Web2 + Web3 Topics

1. Multisigs
2. MPC and TSS
3. TG APIs
4. Indexing the blockchain - Yellowstone and Geyser plugin
5. Running an RPC, running a validator
6. Building liquidators/arb bots/balancing bots.
