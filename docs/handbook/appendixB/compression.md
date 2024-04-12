# Compression

Compressed NFTs use State Compression and merkle trees to drastically reduce the storage cost for NFTs (Figure 1.16). Instead of storing an NFT's metadata in a typical Solana account, compressed NFTs store the metadata within the ledger. This allows compressed NFTs to still inherit the security and speed of the Solana blockchain, while at the same time reducing the overall storage costs.

Even though the on-chain data storage mechanism is different than their uncompressed counterparts, compressed NFTs still follow the exact same Metadata schema/structure. Allowing you to define your Collection and NFT in an identical way.

![Blockchain](../../images/compression.png)


This chart is based on a snapshot taken on April 5, 2023 and based on a price of SOL at $21.14, MATIC at $1.14, and ETH at $1,909.45.

State compression is already being used by teams across the Solana ecosystem to power large, user-friendly experiences

- Dialect
    - a blockchain-based messaging service, uses state compression for compressed NFTs to cover the minting cost of NFT stickers to thousands of users.

- Crossmint
    - an NFT and API tooling company, is using state compression to create integrations that power deeper customer loyalty for companies around the world.

And that’s just the beginning — projects like user-owned wireless network Helium, NFT distributor DRiP, and on-chain publisher Wordcel, are using state compression to bring their scalable, user-first experiences to Solana.

Although state compression can be used to store any sort of data on-chain, the first use of this innovative technology is compressed NFTs. Compressed NFTs are just like regular NFTs, only drastically cheaper — minting 100 million compressed NFTs costs about ◎50 to store on-chain, compared to ◎1.2mm for their uncompressed counterpart. In fact, because every incremental compressed NFT is solely a modification of an existing tree, the cost of an NFT on Solana is now as little as the cost of a single transaction (◎0.000005)!
