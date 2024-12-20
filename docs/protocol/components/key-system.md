# Dual Key System

The dual key system in ZkSnap forms the foundation of its privacy and collusion resistance properties. It consists of two distinct key pairs that serve different purposes in the protocol.

## Overview

### Key Types

1. **Registration Key**
    - Permanent, identity-linked key pair
    - Used to prove voting eligibility
    - Registered in the voter Merkle tree
    - Never used for actual voting

2. **Voting Key**
    - Used for casting votes
    - Can be privately changed
    - No public link to registration key
    - Generates vote nullifiers

## Key Structures

### Registration Key
```
RegistrationKey {
    public: Field,    // Public key for registration
    private: Field,   // Private key known only to voter
}
```

### Voting Key
```
VotingKey {
    public: Field,    // Current public voting key
    private: Field,   // Current private voting key
}
```

## Key Operations

### Key Generation

1. **Registration Key Generation**
    - Generated during voter registration
    - Added to voter Merkle tree
    - Used to prove eligibility

2. **Voting Key Generation**
    - Independent from registration key
    - Can generate multiple keys
    - No on-chain record of changes

### Key Changes

The ability to change voting keys privately is crucial for collusion resistance:

1. **Change Process**
    - Generate new voting key pair
    - No public record of change
    - Old key remains valid for verification
    - New key used for voting

2. **Privacy Properties**
   - Changes are undetectable
   - No link between keys
   - Cannot prove which key was used
   - Maintains vote validity

## Protocol Interactions

### During Setup
```plaintext
1. Generate registration key pair
2. Register public key in Merkle tree
3. Generate initial voting key pair
4. Prepare for vote casting
```

### During Voting
```plaintext
1. Use voting key to create vote
2. Generate nullifier with voting key
3. Prove knowledge of registration key
4. Sign vote with voting key
```

## Security Properties

### Guaranteed Properties

1. **Key Separation**
    - Registration key cannot be used to vote
    - Voting key cannot be used to register
    - No linkability between keys

2. **Change Privacy**
    - Key changes are private
    - Cannot detect if keys changed
    - Cannot link multiple keys
   
3. **Collusion Resistance**
    - Cannot prove which key was used
    - Cannot prove vote choice
    - Deniable vote authorship

### Security Requirements

1. **Registration Key**
    - Must remain secret
    - Only used for eligibility proofs
    - Never revealed in transactions

2. **Voting Key**
   - Can be changed at will
   - Changes remain private
   - Used for vote creation

## Circuit Integration

### Registration Circuit
```plaintext
Public Inputs:
- Merkle root
- Public registration key

Private Inputs:
- Private registration key
- Merkle path

Proves:
- Knowledge of private key
- Inclusion in Merkle tree
```

### Voting Circuit
```plaintext
Public Inputs:
- Vote nullifier
- Encrypted vote
- Public voting key

Private Inputs:
- Private voting key
- Vote choice
- Registration key proof

Proves:
- Valid key ownership
- Correct vote encryption
- Registration status
```