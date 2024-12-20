# Threat Model

This document outlines the security assumptions, adversarial capabilities, and trust model of the ZkSnap protocol.

## System Model

### Protocol Participants

1. **Voters**
   - Hold registration and voting keys
   - Create and submit votes
   - Verify results

2. **Coordinator**
   - Processes votes
   - Maintains state
   - Generates proofs

3. **DRand Service**
   - Provides timelock encryption
   - Distributed trust
   - Time-based decryption

## Trust Assumptions

### Coordinator Trust Model

1. **Semi-Honest Model**
   - Follows protocol correctly
   - May attempt to learn vote contents
   - Cannot forge votes or proofs
   - Cannot prevent valid vote inclusion

2. **Capabilities and Limitations**
```plaintext
Can:
- View encrypted votes
- Process submissions
- Generate proofs
- Manage state

Cannot:
- Decrypt votes early
- Forge valid votes
- Link votes to voters
- Prevent valid voting
```

### DRand Assumptions

1. **Security Model**
```plaintext
Assumes:
- Threshold security
- Byzantine fault tolerance
- Distributed trust
- Correct time maintenance
```

2. **Trust Requirements**
```plaintext
- Majority honest participants
- Correct time-lock enforcement
- Proper key revelation
- Protocol adherence
```

## Adversarial Model

### Adversary Capabilities

1. **Network Control**
```plaintext
Can:
- Observe all communications
- Delay messages
- Read public data
- Track timing

Cannot:
- Modify messages
- Block communications entirely
- Break encryption
```

2. **Computation Power**
```plaintext
Assumed Limits:
- Polynomial-time computation
- No quantum capabilities
- Standard cryptographic bounds
- Cannot break timelock
```

### Attack Vectors

1. **Vote Privacy Attacks**
```plaintext
Types:
- Vote content analysis
- Timing analysis
- Correlation attacks
- Identity linking
```

2. **Protocol Attacks**
```plaintext
Categories:
- Double voting attempts
- Invalid vote insertion
- State corruption
- Proof forgery
```

## Security Properties

### Vote Privacy

1. **Content Privacy**
```plaintext
Guarantees:
- Vote secrecy until tally
- No partial information leakage
- No statistical inference
```

2. **Voter Privacy**
```plaintext
Ensures:
- Voter anonymity
- Action unlinkability
- Participation privacy
```

### Vote Integrity

1. **Correctness**
```plaintext
Properties:
- One vote per voter
- No vote modification
- Accurate tallying
```

2. **Verifiability**
```plaintext
Features:
- Public verification
- Proof validation
- Result auditability
```

## Attack Scenarios

### Network-Level Attacks

1. **Communication Attacks**
```plaintext
Types:
- Message interception
- Timing analysis
- Replay attacks
- Man-in-the-middle
```

2. **Mitigation**
```plaintext
Methods:
- Encryption
- Authentication
- Replay protection
- Timing resistance
```

### Protocol-Level Attacks

1. **Vote Manipulation**
```plaintext
Attempts:
- Invalid vote insertion
- Vote modification
- Double voting
- State corruption
```

2. **Countermeasures**
```plaintext
Protections:
- ZK proofs
- Nullifier system
- State verification
- Proof validation
```

## Security Analysis

### Formal Properties

1. **Privacy Properties**
```plaintext
- Vote secrecy
- Voter anonymity
- Unlinkability
- Forward security
```

2. **Integrity Properties**
```plaintext
- Vote correctness
- Tally accuracy
- State consistency
- Proof soundness
```

### Security Reductions

1. **Cryptographic Assumptions**
```plaintext
Based on:
- Discrete logarithm
- Zero-knowledge soundness
- Timelock puzzles
- Hash security
```

2. **Protocol Security**
```plaintext
Relies on:
- Semi-honest coordinator
- DRand security
- Network assumptions
- Cryptographic primitives