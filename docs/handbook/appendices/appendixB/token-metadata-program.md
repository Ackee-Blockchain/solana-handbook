---
hide:
  - toc
---

The **Token Metadata program** is one of the most important programs when working with NFTs. Its main goal is to attach additional data to fungible or non-fungible tokens on Solana.

It achieves this using [PDAs](../../chapter3/program-derived-address.md) that are derived from the address of [mint accounts](../../chapter4/mint-account.md).

!!! important

    Mint accounts are responsible for storing the global information of a token and [token accounts](../../chapter4/token-account.md) store the relationship between a wallet and a mint account.

<h2>Metadata Account</h2>

Whilst mint accounts contain a few data attributes such as its current supply, they cannot hold standardized data that can be understood by apps and marketplaces. This is why the Token Metadata program offers a metadata account that attaches itself to a mint account via a PDA.

![Blockchain](../../../images/metaplex-metadata-account.png)

<h2>Master Edition</h2>

Additionally, the Token Metadata program offers another account specifically for NFTs called the **Master Edition account**. This account is also a PDA derived from the mint account.

!!! note

    Before creating this account, the Token Metadata program will ensure the special characteristics of NFTs are met. Thus, the existence of the **Master Edition account** acts as **proof of non-fungibility** for that mint account.

The Master Edition account includes some additional fields that are not crucial for the main idea. In essence, [Metaplex](./metaplex.md) offers the capability to create copy of NFTs, with the Master Edition account serving as proof of whether an NFT is original or a copy.

![Blockchain](../../../images/master-edition.png)
