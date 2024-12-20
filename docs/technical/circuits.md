
# Circuit Design

This document details the zero-knowledge circuits used in ZkSnap for vote validity and tallying.

## Vote Circuit

### Circuit Structure

1. **Public Inputs**
```plaintext
- Vote nullifier
- Encrypted vote commitment
- Public voting key
- Merkle root of voters
- Protocol parameters
```

2. **Private Inputs**
```plaintext
- Vote choice
- Vote encryption randomness
- Private voting key
- Merkle path
- Auxiliary data
```

### Circuit Components

1. **Vote Validity**
```plaintext
Constraints:
1. Range check on vote choice
   - 0 <= choice < num_options
   - Bit decomposition check

2. Encryption correctness
   - c = Enc(vote, r, pk)
   - Homomorphic properties maintained
```

2. **Nullifier Verification**
```plaintext
Constraints:
1. Nullifier computation
   - N = PLUME(sk, vote_data)
   - Uniqueness verification

2. Membership check
   - Not in nullifier set
   - Correct generation
```

3. **Key Verification**
```plaintext
Prove:
1. Knowledge of private key
   - Key pair validity
   - Signature verification

2. Merkle path validity
   - Path correctness
   - Root matching
```

## Aggregation Circuit

### Structure

1. **Public Inputs**
```plaintext
- Previous state root
- New state root
- Aggregated vote commitment
- Batch parameters
```

2. **Private Inputs**
```plaintext
- List of encrypted votes
- Vote validity proofs
- State transition data
- Aggregation witnesses
```

### Components

1. **Batch Verification**
```plaintext
Checks:
1. Vote validity
   - Individual proofs
   - Nullifier uniqueness
   - Format correctness

2. State transitions
   - Root updates
   - Consistency checks
```

2. **Homomorphic Operations**
```plaintext
Compute:
1. Vote aggregation
   - Homomorphic addition
   - Commitment updates

2. State updates
   - Tree modifications
   - Root calculations
```
