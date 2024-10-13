The **Token Metadata Program** is one of the most important programs when working with NFTs. Its main goal is to attach additional data to fungible or non-fungible tokens on Solana.

It achieves this using [PDAs](../../chapter3/program-derived-address.md) that are derived from the address of [mint accounts](../../chapter4/mint-account.md).

!!! important

    Mint accounts are responsible for storing the global information of a token and [token accounts](../../chapter4/token-account.md) store the relationship between a wallet and a mint account.

## Metadata Account

Whilst mint accounts contain a few data attributes such as its current supply, they cannot hold standardized data that can be understood by apps and marketplaces. This is why the Token Metadata Program offers a metadata account that attaches itself to a mint account via a PDA.

![Blockchain](../../../images/metaplex-metadata-account.png)

## Master Edition

Additionally, the Token Metadata Program offers another account specifically for NFTs called the **Master Edition Account**. This account is also a PDA derived from the mint account.

!!! note

    Before creating this account, the Token Metadata Program will ensure the special characteristics of NFTs are met. Thus, the existence of the **Master Edition Account** acts as **proof of non-fungibility** for that mint account.

The Master Edition Account includes some additional fields that are not crucial for the main idea. In essence, [Metaplex](./metaplex.md) offers the capability to create copy of NFTs, with the Master Edition account serving as proof of whether an NFT is original or a copy.

![Blockchain](../../../images/master-edition.png)
