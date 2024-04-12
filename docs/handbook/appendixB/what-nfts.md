# What has this got to do with NFTs?

Well, NFTs are special tokens that are Non-Fungible. More precisely,

NFTs on Solana are Mint Accounts with the following characteristics (Figure 1.12):

- It has a supply of 1, meaning only one token is in circulation.
- It has zero decimals, meaning there cannot be such a thing as 0.5 tokens.
- It has no mint authority, meaning no one can ever mint additional tokens.


![Blockchain](../../images/mint-with-nft.png)


Metaplex suite offers essential tools for NFT creation on Solana, including the NFT Metadata program itself, minting tools and marketplex, and auction toolkits.

Outside of the essential tools, the toolkit also contains many other rather experimental tools like Fireball, Fuse, and Gumball that enable NFT creators to do many different things with their NFTs on Solana.


## Master Edition

Additionally, the Token Metadata program offers another account specifically for NFTs called the Master Edition Account (Figure 1.13). This account is also a PDA derived from the Mint Account.

Before creating this account, the Token Metadata program will ensure the special characteristics of Non-Fungible Tokens listed above are met. Thus, the existence of the Master Edition account acts as proof of Non-Fungibility for that Mint Account. As shown in Figure 1.13, the Master Edition Account incorporates several fields that haven't been addressed yet. While these fields hold significance, they aren't pivotal for understanding the core principle. In essence, Metaplex offers the capability to create copy of NFTs, wherein the Master Edition, and likewise the Edition Account, functions as evidence of either replication or originality.

![Blockchain](../../images/master-edition.png)
