# Nullifier System

The nullifier system in ZkSnap prevents double voting while maintaining voter privacy. It uses PLUME (Pseudonymously Linked Unique Message Entity) for generating deterministic nullifiers that ensure each eligible voter can only cast one valid vote.

## Nullifier Design

### Structure
```
Nullifier = PLUME_sign(
    privateKey,    // Voter's private key
    voteData      // Vote-specific data
)
```

### Properties

1. **Deterministic**
   - Same inputs always produce same nullifier
   - No randomness in generation
   - Verifiably unique per voter

2. **Private**
   - Cannot link to voter identity
   - Cannot link to vote contents
   - Cannot predict future nullifiers

3. **Verifiable**
   - Efficient membership checking
   - Public verification
   - No private data needed for verification

## Generation Process

### Components

1. **Inputs Required**
   - Voter's private key
   - Vote parameters
   - Protocol constants

2. **Output Properties**
   - Fixed-size value
   - Uniform distribution
   - Collision resistant

### Generation Steps
```plaintext
1. Combine inputs with domain separator
2. Generate PLUME signature
3. Hash signature to create nullifier
4. Verify uniqueness
```

## Verification System

### State Management

1. **Nullifier Set**
   - Maintains all used nullifiers
   - Efficient lookup structure
   - Indexed Merkle tree implementation

2. **Verification Process**
   - Check nullifier not previously used
   - Verify nullifier correctness
   - Update nullifier set

### Circuit Integration
```plaintext
Public Inputs:
- Nullifier value
- Nullifier tree root

Private Inputs:
- Private key
- Vote data
- Generation parameters

Circuit Constraints:
- Correct nullifier generation
- Valid signature verification
- Proper input formatting
```

## Security Properties

### Guaranteed Properties

1. **Double-Vote Prevention**
   - Each voter gets one valid vote
   - Cannot reuse nullifiers
   - Cannot forge valid nullifiers

2. **Privacy Preservation**
   - No identity leakage
   - No vote content leakage
   - No key correlation possible

3. **Verifiability**
   - Public verification possible
   - Efficient checking
   - No trust requirements

### Security Requirements

1. **Cryptographic Properties**
   - Collision resistance
   - Pre-image resistance
   - Second pre-image resistance

2. **Privacy Requirements**
   - Nullifier unlinkability
   - Input hiding
   - Key hiding

## Implementation Details

### Nullifier Tree

1. **Structure**
   - Indexed Merkle tree
   - Efficient inclusion proofs
   - O(log n) verification

2. **Operations**
   - Insert new nullifier
   - Check nullifier existence
   - Generate inclusion proofs

### PLUME Integration

1. **Signature Generation**
```plaintext
Input: 
- Private key sk
- Message m

Output:
- Deterministic signature σ
- Nullifier N = H(σ)

Properties:
- σ = PLUME_sign(sk, m)
- Verification with public key
- Unique per (key, message) pair
```

2. **Verification Process**
```plaintext
1. Check nullifier format
2. Verify PLUME signature
3. Confirm tree non-membership
4. Update nullifier set
```

## Protocol Integration

### During Vote Creation

1. **Nullifier Generation**
   - Create vote data
   - Generate PLUME signature
   - Derive nullifier
   - Prepare inclusion proof

2. **Vote Submission**
   - Include nullifier in vote
   - Prove nullifier correctness
   - Submit to coordinator

### During Vote Processing

1. **Coordinator Actions**
   - Verify nullifier uniqueness
   - Update nullifier tree
   - Generate new root
   - Create inclusion proof

2. **Verification Steps**
   - Check nullifier validity
   - Verify tree updates
   - Confirm non-membership proofs