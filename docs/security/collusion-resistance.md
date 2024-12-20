# Collusion Resistance

This document details how ZkSnap prevents vote buying and selling through its cryptographic design and protocol mechanisms.

## Threat Model

### Attack Scenarios

1. **Direct Vote Buying**
    - Attacker offers payment for specific votes
    - Requests proof of voting choice
    - Attempts to verify vote compliance

2. **Coercion Attempts**
    - Forced vote choices
    - Demanded vote proofs
    - Verification of compliance

3. **Vote Selling**
    - Voluntary vote selling
    - Proof of vote choice
    - Vote verification schemes

## Security Mechanisms

### 1. Key Privacy

The dual key system prevents vote proving:

1. **Registration Key**
   - Never used for voting
   - Only proves eligibility
   - Cannot link to votes

2. **Voting Key**
   - Used for actual voting
   - Cannot prove which key voted
   - No public key history

### 2. Vote Privacy

Multiple layers ensure vote content privacy:

1. **Encryption**
   - Homomorphic encryption
   - Timelock protection
   - No early decryption

2. **Proof System**
   - Zero-knowledge proofs
   - No vote content revelation
   - Validity verification only

### 3. Nullifier System

Ensures one-time voting while maintaining privacy:

1. **Properties**
   - One nullifier per voter
   - Cannot link to identity
   - Prevents double voting

2. **Privacy Features**
   - No voter correlation
   - No vote linkability
   - Deterministic generation

## Attack Prevention

### Vote Buying Prevention

1. **Proof Impossibility**
```plaintext
Why vote buying fails:
- Cannot prove vote choice
- Cannot verify vote timing
- Cannot link voter to vote
```

2. **Deniability**
```plaintext
Voter capabilities:
- Generate fake proofs
- Cannot prove real vote
- Maintain plausible deniability
```

### Coercion Resistance

1. **Vote Privacy**
```plaintext
Properties:
- Vote contents hidden
- No proof of choice
- No timing information
```

2. **Identity Protection**
```plaintext
Features:
- Anonymous voting
- Unlinkable actions
- Private key management
```

## Security Guarantees

### Cryptographic Guarantees

1. **Vote Privacy**
```plaintext
Ensures:
- Vote content secrecy
- Voter anonymity
- Action unlinkability
```

2. **Proof Soundness**
```plaintext
Provides:
- Valid vote verification
- No false proofs
- Correct tallying
```

### Protocol Guarantees

1. **Temporal Privacy**
```plaintext
Until timelock expiration:
- No vote decryption
- No partial results
- No tally information
```

2. **Participation Privacy**
```plaintext
Protected information:
- Voter identity
- Vote timing
- Vote correlation
```

## Implementation Requirements

### System Requirements

1. **Cryptographic Implementation**
```plaintext
Requirements:
- Secure random generation
- Proper key management
- Robust encryption
```

2. **Protocol Implementation**
```plaintext
Needs:
- Correct proof generation
- Secure state management
- Proper nullifier handling
```

### Security Considerations

1. **Key Management**
```plaintext
Guidelines:
- Secure key storage
- Private key protection
- Key update procedures
```

2. **Proof Generation**
```plaintext
Requirements:
- Correct circuit implementation
- Secure parameter generation
- Proper randomness use
```

## Verification Methods

### Proof Verification

1. **Vote Proofs**
```plaintext
Verify:
- Vote validity
- Nullifier correctness
- Key ownership
```

2. **Tally Proofs**
```plaintext
Check:
- Result correctness
- State consistency
- Proper aggregation
```