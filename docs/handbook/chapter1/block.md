# Block

Block is a data structure that contains a header comprising three items – the hash of the previous block’s header, metadata and a Merkle root [5]. Metadata depends on the protocol. The Merkle root is a root of the well-known Merkle tree, which can be used to verify later that transactions in a block have not been tampered with. After the header comes the core part of the block, the transaction.
