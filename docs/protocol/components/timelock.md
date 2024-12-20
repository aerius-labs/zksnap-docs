# Timelock Encryption

ZkSnap uses timelock encryption to ensure vote privacy during the voting period and prevent early result calculations. The system uses DRand for distributed timelock encryption.

## Overview

### Purpose
    - Prevent early vote counting
    - Ensure vote privacy during voting
    - Enable verifiable decryption timing
    - Prevent coordinator manipulation

### Properties
    - Time-based encryption
    - Distributed trust
    - Verifiable delay
    - Guaranteed decryption

## Timelock Components

### 1. Encryption System
```plaintext
Components:
- Public encryption key (available immediately)
- Private decryption key (time-locked)
- Timelock parameters
- Verification parameters
```

### 2. Time Periods
```plaintext
Phases:
1. Setup: Parameter generation
2. Voting: Votes remain encrypted
3. Unlock: Decryption key revealed
4. Tallying: Results computed
```

## Protocol Operations

### Setup Phase

1. **Parameter Generation**
```plaintext
- Generate encryption keypair (pk, sk)
- Set voting duration parameter T
- Create timelock puzzle for sk
- Publish encryption parameters
```

2. **Timelock Creation**
```plaintext
Input:
- Decryption key sk
- Time parameter T
- DRand parameters

Output:
- Encrypted key E(sk)
- Verification parameters
- Public parameters
```

### Vote Encryption

1. **Vote Processing**
```plaintext
- Encrypt vote with public key
- Add randomness for security
- Generate encryption proof
- Submit encrypted package
```

2. **Encryption Properties**
```plaintext
- Homomorphic addition
- Verifiable encryption
- Randomized
- Timelock compatible
```

### Key Revelation

1. **Timelock Expiration**
```plaintext
- DRand reveals decryption key
- Verify key correctness
- Enable vote decryption
- Begin tallying phase
```

2. **Verification Process**
```plaintext
- Check timelock completion
- Verify key authenticity
- Confirm proper timing
- Validate parameters
```

## Security Properties

### Guaranteed Properties

1. **Time Security**
   - No early decryption possible
   - Verifiable delay function
   - Distributed trust model

2. **Encryption Security**
   - IND-CPA security
   - Forward security
   - Collusion resistance

3. **Verification Properties**
   - Public verifiability
   - Proof of correct encryption
   - Proof of proper timing

### Trust Assumptions

1. **Timelock Service**
   - DRand security model
   - Threshold trust assumption
   - Byzantine fault tolerance

2. **Cryptographic Assumptions**
   - Hardness of time-lock puzzles
   - Security of encryption scheme
   - Random oracle model

## Implementation Details

### Encryption Scheme

1. **Vote Encryption**
```plaintext
Input: 
- Vote v
- Public key pk
- Random value r

Output:
- Encrypted vote c
- Encryption proof π

Properties:
- Homomorphic
- Verifiable
- Non-malleable
```

2. **Key Management**
```plaintext
Components:
- DRand beacon
- Timelock parameters
- Verification keys
- Proof system
```

### Verification System

1. **Setup Verification**
```plaintext
Verify:
- Parameter generation
- Timelock creation
- Public key distribution
- Initial state
```

2. **Operation Verification**
```plaintext
Check:
- Vote encryption
- Timelock progression
- Key revelation
- Decryption process
```

## Integration Points

### With Vote System
```plaintext
1. Vote Creation:
   - Encrypt vote choice
   - Generate proofs
   - Package with nullifier

2. Vote Processing:
   - Verify encryption
   - Store encrypted votes
   - Maintain state
```

### With Tallying System
```plaintext
1. Key Revelation:
   - Obtain decryption key
   - Verify timing
   - Begin decryption

2. Result Computation:
   - Decrypt votes
   - Aggregate results
   - Generate proofs
```