# Protocol Overview

ZkSnap is a privacy-preserving voting protocol that enables anonymous, verifiable voting while preventing vote buying and coercion. It achieves this through a combination of zero-knowledge proofs, homomorphic encryption, and a novel key management system.

## Protocol Goals

ZkSnap is designed to achieve several critical properties:

1. **Vote Privacy**
   - Individual votes remain secret
   - Vote contents are encrypted until tallying
   - No correlation between voters and votes

2. **Collusion Resistance**
   - Prevents vote buying/selling
   - Voters cannot prove their vote choice
   - Key changes remain private

3. **Vote Integrity**
   - One vote per eligible voter
   - All valid votes are counted
   - Results are verifiable

4. **Efficiency**
   - Zero cost for voters
   - Minimal on-chain footprint
   - Efficient proof verification

## System Participants

### 1. Voters
- Hold registration and voting keys
- Create encrypted votes
- Generate zero-knowledge proofs

### 2. Coordinator
- Manages vote collection
- Aggregates encrypted votes
- Generates aggregate proofs
- Cannot manipulate votes

### 3. Verifiers
- Anyone can verify results
- Check proof validity
- Verify final tally

## Core Components

### 1. Dual Key System
The protocol uses two types of keys:
- **Registration Key**: Proves voting eligibility
- **Voting Key**: Used for actual vote casting
  - Can be changed privately
  - Changes are undetectable

### 2. Nullifier System
Prevents double voting while maintaining privacy:
- One nullifier per voter
- Deterministically generated
- Cannot be linked to voter identity

### 3. Vote Structure
Each vote contains:
- Encrypted vote choice
- Vote nullifier
- Zero-knowledge proof
- Public parameters

### 4. Time Lock System
Ensures vote privacy during voting:
- Encrypts vote contents
- Decryption key time-locked
- Results revealed only after voting ends

## Protocol Flow

### 1. Setup Phase
```plaintext
1. System parameters generated
2. Coordinator publishes public key
3. Time-lock parameters established
4. Voter registration begins
```

### 2. Voting Phase
```plaintext
1. Voter creates encrypted vote
2. Generates nullifier
3. Produces validity proof
4. Submits vote package
```

### 3. Tallying Phase
```plaintext
1. Time lock expires
2. Votes decrypted
3. Results computed
4. Proofs verified
```

## Security Properties

### Guaranteed Properties
- No one can determine individual votes
- Votes cannot be changed or deleted
- Double voting is impossible
- Results are verifiable
- Vote buying is ineffective

### Trust Assumptions
- Coordinator is semi-honest
- Time-lock mechanism is secure
- Cryptographic primitives are secure
- ZK proof system is sound

## Protocol Innovations

1. **Key Privacy**
    - Private key evolution
    - Undetectable changes
    - Maintained vote validity

2. **Nullifier Design**
    - Efficient verification
    - Privacy preserving
    - Double-spend prevention

3. **Proof System**
    - Vote validity proofs
    - Aggregation proofs
    - Efficient verification