# index.md

# ZkSnap: Privacy-Preserving, Collusion-Resistant Voting

ZkSnap is a zero-knowledge voting protocol designed for decentralized organizations that provides:
- Complete vote privacy
- Prevention of vote buying and selling
- Zero-cost voting
- Universal result verification

## Key Properties

1. **Vote Privacy**: No one, including system operators, can determine individual votes
2. **Collusion Resistance**: Voters cannot prove their vote choice to others
3. **Non-interactivity**: Voters can cast votes without coordination
4. **Universal Verifiability**: Anyone can verify vote counting accuracy

## Protocol Components

1. **Dual Key System**
   - Registration keys for eligibility
   - Evolving voting keys for collusion prevention

2. **Time-Locked Privacy**
    - Vote contents remain encrypted during voting
    - Results revealed only after deadline

3. **Zero-Knowledge Proofs**
    - Vote validity verification
    - Private vote aggregation

4. **Deterministic Nullifiers**
    - Double-vote prevention
    - Vote linkability prevention
