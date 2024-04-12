# Account Compression Program

The Account Compression Program is an innovative on-chain system designed to alleviate the rising concern of storage costs on the Solana blockchain. Its main application revolves around the utilization of SPL ConcurrentMerkleTrees, allowing for the on-chain verification of off-chain data edits. This innovative solution has been crafted in response to the challenges brought about by the increased creation of Non-Fungible Tokens (NFTs) on the Solana blockchain.

## Motivation

- Solana's high throughput has fostered a significant increase in the creation of NFTs. The attractive features of NFTs, such as custodial ownership and censorship resistance, have contributed to their popularity. However, this widespread adoption has led to a critical concern: the network storage costs when creating NFTs at scale.
- While minting a single non-fungible token may be relatively inexpensive, the cost of storing the asset's data on-chain can quickly become uneconomical as the quantity increases. This issue presents a barrier to the practical and widespread use of NFTs, especially when they are produced en masse.
- The objective is to make the cost per token as close to zero as possible, ensuring affordability and scalability. The solution lies in storing a compressed hash of the asset data on-chain, while the actual data resides off-chain in a database.
- The Account Compression Program facilitates this by providing a means to verify the off-chain data on-chain and enabling concurrent writes to the data. A central component of this solution is the Concurrent Merkle Tree, a newly introduced data structure that prevents proof collision during concurrent writes.


## Application

The Account Compression Program is already in use in projects like the Metaplex Bubblegum Program. Its implementation has allowed for a reduction in on-chain storage costs, making it more economical to produce and manage NFTs at scale.
