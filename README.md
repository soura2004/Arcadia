# ArcadiaID – Decentralized Identity Verification on Aptos

ArcadiaID is a simple Move smart contract module that addresses the broken identity verification problem by registering and verifying identities on the Aptos blockchain. It is part of the Arcadia ecosystem, aiming to provide trustless, decentralized identity solutions.

## 📦 Module Overview

```move
module MyModule::ArcadiaID
This module contains:

A struct Identity that stores basic user identity data.

Two functions:

register_identity: Allows users to create their identity on-chain.

verify_identity: Allows a trusted verifier to mark the identity as verified.

🛠️ Functions
1. register_identity(user: &signer, name: string::String)
Registers a new identity for the user.

Parameters:

user: The signer of the transaction (identity owner).

name: The identity name to be stored.

Effect: Creates an Identity resource with verified = false.

2. verify_identity(verifier: &signer, user_addr: address) acquires Identity
Marks an identity as verified. Intended to be called by a trusted verifier.

Parameters:

verifier: The signer performing the verification.

user_addr: Address of the identity to verify.

Effect: Sets verified = true for the user’s identity.

📦 Structs
move
Copy
Edit

struct Identity has key, store {
    name: string::String,
    verified: bool,
}
Stores:

name: Identity name string.

verified: Boolean status of verification.

🚀 Deployment Instructions
Compile the module using the Aptos CLI:

bash
Copy
Edit

aptos move compile
Publish the module:

bash
Copy
Edit

aptos move publish --package-dir .
Interact with the functions using the Aptos CLI or a front-end DApp.

📌 Notes
Add proper access control (e.g. check verifier's role) in production use.

Extend to support additional fields (email, KYC hash, etc.) if needed.

This is a minimal version for demonstration or MVP purposes.
