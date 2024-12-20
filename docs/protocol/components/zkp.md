# Zero-Knowledge Proof System

ZkSnap uses zero-knowledge proofs to ensure vote validity, privacy, and correctness of the tallying process without revealing any individual votes.

## Circuit Design

### Vote Circuit

The main circuit that proves vote validity and correct encryption.

#### Public Inputs
```
- Vote nullifier
- Encrypted vote commitment
- Public voting key
- Merkle root of valid voters
```

#### Private Inputs
```
- Vote choice
- Vote encryption randomness
- Private voting key
- Merkle path for voter inclusion
```

#### Constraints
```
1. Voter Eligibility
   - Merkle path is valid
   - Voter public key included in tree

2. Vote Validity
   - Choice within valid range
   - Correct encryption of choice
   - Valid nullifier generation

3. Key Ownership
   - Prove knowledge of private key
   - Signature verification
```

### Aggregation Circuit

Circuit for proving correct vote aggregation and tallying.

#### Public Inputs
```
- Previous state root
- New state root
- Encrypted tally commitment
```

#### Private Inputs
```
- List of encrypted votes
- State transition witnesses
- Aggregation randomness
```

#### Constraints
```
1. State Transition
   - Valid state update
   - Correct vote inclusion

2. Tally Computation
   - Homomorphic addition
   - Commitment correctness
```

## Proof Generation

### Vote Proof

1. **Preparation**
```plaintext
- Format inputs
- Generate nullifier
- Encrypt vote
- Create commitments
```

2. **Proof Generation**
```plaintext
- Construct witness
- Generate SNARK proof
- Package proof data
```

### Aggregation Proof

1. **Batch Processing**
```plaintext
- Collect valid votes
- Update state
- Compute running tally
```

2. **Proof Creation**
```plaintext
- Build aggregation witness
- Generate batch proof
- Create state update proof
```

## Verification System

### Individual Vote Verification

1. **Public Verification**
```plaintext
Check:
- Proof validity
- Nullifier uniqueness
- Commitment structure
```

2. **Constraints Verification**
```plaintext
Verify:
- Range constraints
- Encryption correctness
- Signature validity
```

### Batch Verification

1. **State Update Verification**
```plaintext
Check:
- State transition validity
- Vote inclusion proofs
- Nullifier set updates
```

2. **Tally Verification**
```plaintext
Verify:
- Homomorphic operations
- Commitment consistency
- Final tally validity
```

## Security Properties

### Proof Properties

1. **Zero-Knowledge**
   - No vote choice revealed
   - No voter identity leaked
   - No key information exposed

2. **Completeness**
   - Valid votes always accepted
   - Correct proofs verify
   - Honest execution succeeds

3. **Soundness**
   - Invalid votes rejected
   - No false proofs accepted
   - Cannot forge valid proofs

### Trust Assumptions

1. **Cryptographic**
   - Discrete log problem
   - Algebraic group properties
   - Hash function security

2. **Protocol**
   - Setup phase security
   - Parameters generation
   - CRS trustworthiness

## Implementation Details

### Circuit Optimizations

1. **Constraint Reduction**
```plaintext
- Efficient range proofs
- Optimized encryption checks
- Minimal constraint system
```

2. **Performance Considerations**
```plaintext
- Parallel proof generation
- Batched verification
- Memory efficient design
```

### Proof System Integration

1. **With Vote Processing**
```plaintext
- Proof generation during voting
- Real-time verification
- State updates
```

2. **With Tallying System**
```plaintext
- Aggregate proof generation
- Final tally verification
- Result publication
```

## Protocol Interactions

### During Setup

1. **System Setup**
```plaintext
- Generate proving/verification keys
- Set up circuit parameters
- Initialize state
```

2. **Voter Registration**
```plaintext
- Generate voter proofs
- Update Merkle tree
- Verify registration
```

### During Voting

1. **Vote Submission**
```plaintext
- Generate vote proof
- Submit to coordinator
- Verify acceptance
```

2. **State Management**
```plaintext
- Update nullifier set
- Maintain vote records
- Track state changes
```