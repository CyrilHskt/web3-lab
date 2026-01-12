- A Merkle Tree (or hash tree) is a binary tree structure where each leaf node contains the [[Hash]] of a data block, and each non-leaf node contains the hash of its children.
- The root hash (Merkle root) represents a cryptographic fingerprint of all the data in the tree.

## How it works

- Data blocks are hashed individually (leaf nodes).
- Pairs of hashes are combined and hashed again (parent nodes).
- This process continues until a single root hash is obtained.

## Benefits in blockchain

- **Efficient verification**: To verify if a transaction is included in a block, you only need a small subset of hashes (Merkle path), not the entire block.
- **Data integrity**: Any change in the data will result in a completely different root hash.
- **Lightweight**: Blockchain clients can verify transactions without downloading the full blockchain.

## Usage in Bitcoin/Ethereum

- The Merkle root is stored in the block header.
- Allows quick proof that a transaction exists in a block (Merkle proof).