---
hide:
  - toc
---

There are more types of tokens on Solana besides **fungible** and **non-fungible**. Here are some of the token types that you can come across on Solana.

<h2>Semi-Fungible Tokens</h2>

**Semi-Fungible Token** has attributes of a typical NFT such as image and metadata but its supply is greater than one. These tokens are becoming popular in gaming contexts to support fungible items such as a kind of sword or a piece of wood.

<h2>Programmable NFT</h2>

Since the [Token Metadata program](./token-metadata-program.md) builds on the [Solana Token program](../../chapter4/token-program.md), tokens (fungible or not) can be transferred without involving the Token Metadata program. Metadata accounts include a **Seller Fee Basis Points** field for royalties, but it’s only informational. This allows marketplaces to bypass royalties, which has happened.

Programmable NFTs were introduced to fix this. They are a new token standard that keeps token accounts frozen, ensuring transfers go through the Token Metadata program. Creators can define custom authorization rules in a **RuleSet** account, such as enforcing royalties. These **RuleSets** are part of the [Token Auth Rules program](https://developers.metaplex.com/token-auth-rules).

![Blockchain](../../../images/programmable.png)

<h2>Executable NFT</h2>

Executable NFTs (xNFTs), available in the open source wallet Backpack, represent an entirely new way to build applications. They combine executable websites and applications that can run locally on a user’s computer with a crypto wallet.

xNFTs take a radically practical approach to solving two of web3’s main problems today, decentralization and distribution. While smart contracts run on globally distributed and decentralized networks like Solana, nearly everyone who interacts with smart contracts does so through a website.
!!! example

    Executable NFTs can bring a new level of interactivity to traditional collections. The first xNFT Collection, [Mad Lads](https://www.madlads.com/), showcases the power of an executable profile picture collection — the pictures themselves act as a chatroom for users which is rendered entirely within the NFT. The possibilities are almost limitless.

![Blockchain](../../../images/xnfts.png)

<h2>Compressed NFT</h2>

Compressed NFTs use [state compression and Merkle trees](../../chapter4/account-compression-program.md) to drastically reduce the storage cost for NFTs. Instead of storing metadata in a typical Solana account, compressed NFTs store the metadata within the ledger. This allows compressed NFTs to still inherit the security and speed of the Solana blockchain, while at the same time reducing the overall storage costs.

Even though the on-chain data storage mechanism is different than their uncompressed counterparts, compressed NFTs still follow the exact same metadata schema/structure. Allowing you to define your collection and NFT in an identical way.

!!! note

    Minting **100 million** compressed NFTs costs about **50 SOL** to store on-chain, compared to **1.2mm SOL** for their uncompressed counterpart. Every incremental compressed NFT is solely a modification of an existing tree, which brings the cost down to as little as **0.000005 SOL**.
