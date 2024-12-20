# getting-started.md

# Getting Started with ZkSnap

This guide provides a high-level overview of the ZkSnap protocol and its core components. 

## Basic Concepts

### What is ZkSnap?
ZkSnap is a protocol that enables private, verifiable voting while preventing vote buying and coercion. It achieves this through:
    - A dual key system for voter privacy
    - Time-locked vote revelation
    - Zero-knowledge proofs for verification

### Key Components

1. **Voter Keys**
    - Registration Key: Proves voting eligibility
    - Voting Key: Used to cast votes, can be changed privately

2. **Vote Structure**
    - Encrypted vote choice
    - Nullifier to prevent double voting
    - Zero-knowledge proof of validity

3. **Coordinator**
    - Processes votes
    - Maintains vote state
    - Generates aggregate proofs

## Protocol Flow

1. **Setup Phase**
    - System parameters generated
    - Voter registration opens
    - Timelock parameters established

2. **Voting Phase**
    - Voters create encrypted votes
    - Submit votes with proofs
    - Can privately change voting keys

3. **Tallying Phase**
    - Timelock expires
    - Votes decrypted and counted
    - Results verified

## Next Steps
- User Guide [here](guides/user-guide.md)
- Understand [core protocol concepts](protocol/overview.md)
- Learn about [collusion resistance](security/collusion-resistance.md)
- Review [security model](security/threat-model.md)