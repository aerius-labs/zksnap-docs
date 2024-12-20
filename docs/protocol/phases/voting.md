# Voting Phase

The voting phase is when registered voters submit their encrypted votes with zero-knowledge proofs of validity.

## Overview

During this phase:
- Voters create encrypted votes
- Generate validity proofs
- Submit votes to coordinator
- Coordinator verifies and processes votes

## Vote Creation

### Components
```plaintext
Vote Structure:
- Encrypted vote choice
- Nullifier
- Zero-knowledge proof
- Public parameters
```

### Creation Process

1. **Vote Preparation**
```plaintext
Input:
- Vote choice
- Voting key pair
- Protocol parameters

Steps:
1. Encrypt vote using public key
2. Generate nullifier
3. Create validity proof
4. Package vote data
```

2. **Proof Generation**
```plaintext
Required Proofs:
- Vote validity
- Voter eligibility
- Nullifier correctness
- Encryption validity
```

## Vote Submission

### Submission Process

1. **Voter Actions**
```plaintext
1. Package vote components
2. Submit to coordinator
3. Verify acceptance
4. Receive confirmation
```

2. **Protocol Validation**
```plaintext
Checks:
- Proof validity
- Nullifier uniqueness
- Vote format
- Timing constraints
```

## Coordinator Processing

### Vote Processing

1. **Initial Checks**
```plaintext
Verify:
- Vote structure
- Timing validity
- Proof integrity
- Nullifier status
```

2. **State Updates**
```plaintext
Actions:
- Add nullifier
- Update state
- Store encrypted vote
- Log submission
```

### Batch Processing

1. **Vote Aggregation**
```plaintext
Operations:
- Collect valid votes
- Update Merkle roots
- Maintain state consistency
```

2. **State Management**
```plaintext
Track:
- Vote count
- Nullifier set
- Encrypted tally
- System state
```

## Security Properties

### Vote Privacy

1. **Encryption Security**
```plaintext
Guarantees:
- Vote content hidden
- Voter privacy preserved
- No early decryption
```

2. **Nullifier Privacy**
```plaintext
Properties:
- Unlinkable to voter
- Prevents double voting
- No vote tracking
```

### Vote Integrity

1. **Proof Verification**
```plaintext
Ensures:
- Valid vote choice
- Correct encryption
- Proper nullifier
```

2. **State Integrity**
```plaintext
Maintains:
- Consistent state
- Valid updates
- Verifiable changes
```

## Error Handling

### Vote Submission Errors

1. **Invalid Votes**
```plaintext
Cases:
- Invalid proofs
- Used nullifiers
- Malformed votes
- Timing violations
```

2. **Resolution**
```plaintext
Steps:
- Reject invalid votes
- Provide error details
- Allow resubmission
- Log failures
```

### System Errors

1. **Processing Failures**
```plaintext
Types:
- State update failures
- Proof verification errors
- Storage issues
```

2. **Recovery**
```plaintext
Actions:
- State rollback
- Error logging
- System recovery
- Vote reprocessing
```

## Implementation Details

### Performance Optimization

1. **Batch Processing**
```plaintext
Methods:
- Parallel verification
- Batched updates
- Efficient storage
```

2. **Resource Management**
```plaintext
Considerations:
- Memory usage
- Computation costs
- Storage efficiency
```

### System Constraints

1. **Timing Requirements**
```plaintext
Limits:
- Vote submission window
- Processing deadlines
- Verification timeouts
```

2. **Resource Limits**
```plaintext
Bounds:
- Maximum votes per batch
- Storage capacity
- Computation limits
```

## Protocol Interactions

### With Setup Phase
```plaintext
Dependencies:
- Registration status
- System parameters
- Initial state
```

### With Tallying Phase
```plaintext
Preparation:
- Vote collection complete
- State finalization
- Transition readiness
```