# Cryptographic Primitives

This document details the cryptographic building blocks used in ZkSnap.

## Homomorphic Encryption

### Paillier Cryptosystem

1. **Key Generation**
```plaintext
Generate two large primes p, q where:
- length(p) = length(q)
- gcd(pq, (p-1)(q-1)) = 1

Compute:
- n = pq
- λ = lcm(p-1, q-1)
- g in Z*_n²
- μ = (L(g^λ mod n²))^(-1) mod n
  where L(x) = (x-1)/n

Output:
- Public key: (n, g)
- Private key: (λ, μ)
```

2. **Encryption**
```plaintext
Input:
- Message m in Z_n
- Random r in Z*_n
- Public key (n, g)

Compute:
c = g^m * r^n mod n²

Output:
- Ciphertext c
```

3. **Decryption**
```plaintext
Input:
- Ciphertext c
- Private key (λ, μ)

Compute:
m = L(c^λ mod n²) * μ mod n

Output:
- Message m
```

## PLUME Nullifiers

### Nullifier Generation

1. **Components**
```plaintext
Input:
- Private key sk
- Message m (vote data)
- Domain separator d

Properties:
- Deterministic output
- Unique per (key, message)
- Non-invertible
```

2. **Generation Process**
```plaintext
Steps:
1. h = Hash(m || d)
2. s = PLUME_sign(sk, h)
3. N = Hash(s)

Output:
- Nullifier N
```

## Zero-Knowledge Circuits

### Base Components

1. **Field Arithmetic**
```plaintext
Operations:
- Field addition
- Field multiplication
- Field inversion
- Scalar multiplication
```

2. **Range Constraints**
```plaintext
Features:
- Efficient range proofs
- Binary decomposition
- Comparison circuits
- Membership proofs
```

### Encryption Circuit

1. **Structure**
```plaintext
Public Inputs:
- Encrypted vote
- Public key
- Vote parameters

Private Inputs:
- Vote choice
- Randomness
- Private key
```

2. **Constraints**
```plaintext
Verify:
- Proper encryption
- Valid range
- Correct format
```

## Timelock Encryption

### DRand Integration

1. **Setup**
```plaintext
Parameters:
- Time difficulty T
- Security parameter λ
- Beacon frequency
```

2. **Key Generation**
```plaintext
Process:
1. Generate encryption keys
2. Create timelock puzzle
3. Encrypt decryption key
4. Set reveal parameters
```

## Protocol Constants

### Security Parameters

1. **Field Parameters**
```plaintext
Specifications:
- Field size: 254 bits
- Security level: 128 bits
- Hash length: 256 bits
```

2. **Protocol Parameters**
```plaintext
Settings:
- Batch size: 1024
- Tree depth: 32
- Window size: 256
```

## Hashing Schemes

### Hash Functions

1. **Requirements**
```plaintext
Properties:
- Collision resistant
- Pre-image resistant
- Length-extension resistant
```

2. **Usage Contexts**
```plaintext
Applications:
- Nullifier generation
- State commitments
- Message hashing
- Tree nodes
```

## Merkle Trees

### Indexed Merkle Tree

1. **Structure**
```plaintext
Components:
- Binary tree
- Index pointers
- Efficient updates
- O(log n) proofs
```

2. **Operations**
```plaintext
Functions:
- Insert element
- Generate proof
- Verify proof
- Update state
```