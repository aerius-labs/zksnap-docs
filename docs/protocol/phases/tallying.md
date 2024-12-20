# Tallying Phase

The tallying phase occurs after voting ends and the timelock expires, enabling decryption and computation of final results with proofs of correctness.

## Overview

The tallying phase involves:
    - Timelock expiration
    - Vote decryption
    - Result computation
    - Proof generation

## Timelock Expiration

### Key Revelation
```plaintext
Process:
1. Wait for timelock period end
2. Obtain decryption key from DRand
3. Verify key authenticity
4. Start decryption process
```

### Verification
```plaintext
Checks:
1. Timelock completion proof
2. Key correctness proof
3. Timing validity
```

## Vote Decryption

### Decryption Process

1. **Preparation**
```plaintext
Steps:
1. Collect all encrypted votes
2. Verify final state
3. Prepare decryption batch
```

2. **Batch Decryption**
```plaintext
Operations:
1. Decrypt encrypted tally
2. Generate decryption proof
3. Verify correctness
```

## Result Computation

### Tally Calculation

1. **Vote Counting**
```plaintext
Steps:
1. Process decrypted votes
2. Compute final tally
3. Generate tally proof
```

2. **Result Verification**
```plaintext
Checks:
1. Tally correctness
2. Proof validity
3. State consistency
```

## Proof Generation

### Correctness Proofs

1. **Component Proofs**
```plaintext
Types:
- Decryption correctness
- Tally computation
- State consistency
```

2. **Aggregate Proof**
```plaintext
Properties:
- Combines component proofs
- Efficient verification
- Complete auditability
```

## Protocol Properties

### Security Guarantees

1. **Privacy**
```plaintext
Ensures:
- No early result leakage
- Vote privacy maintained
- Voter anonymity
```

2. **Correctness**
```plaintext
Guarantees:
- Accurate decryption
- Correct tallying
- Verifiable results
```

### Verification Process

1. **Result Verification**
```plaintext
Steps:
1. Verify decryption proof
2. Check tally computation
3. Validate final state
```

2. **Public Verification**
```plaintext
Enables:
- Independent verification
- Public auditability
- Result confirmation
```

## Implementation Details

### System Requirements

1. **Computational Resources**
```plaintext
Needs:
- Decryption capacity
- Proof generation power
- Storage for results
```

2. **Time Management**
```plaintext
Constraints:
- Decryption window
- Proof generation time
- Publication deadline
```

### Error Handling

1. **Decryption Errors**
```plaintext
Types:
- Key verification failures
- Decryption failures
- Proof generation issues
```

2. **Recovery Procedures**
```plaintext
Steps:
1. Error identification
2. State recovery
3. Process restart
```

## Result Publication

### Data Format

1. **Results Structure**
```plaintext
Components:
- Final tally
- Decryption proof
- Verification data
```

2. **Verification Package**
```plaintext
Includes:
- Complete proofs
- State information
- Audit trail
```

### Publication Process

1. **Result Release**
```plaintext
Steps:
1. Format results
2. Generate verification package
3. Publish data
```

2. **Public Access**
```plaintext
Provides:
- Result accessibility
- Verification tools
- Audit capability
```

## Protocol Completion

### Finalization Steps

1. **State Finalization**
```plaintext
Actions:
1. Lock final state
2. Archive data
3. Clean temporary storage
```

2. **System Cleanup**
```plaintext
Tasks:
1. Clear sensitive data
2. Archive logs
3. Reset system state
```

### Verification Tools

1. **Public Verifier**
```plaintext
Features:
- Result verification
- Proof checking
- State validation
```

2. **Audit Support**
```plaintext
Provides:
- Complete audit trail
- Verification tools
- Documentation
```