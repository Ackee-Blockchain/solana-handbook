# Token Metadata Program

The Token Metadata program is one of the most important programs when dealing with NFTs on the Solana blockchain. Its main goal is to attach (Figure 1.11) additional data to Fungible or Non-Fungible Tokens on Solana.

It achieves this using Program Derived Addresses (PDAs) that are derived from the address of Mint Accounts. You should be familiar with Solana’s Token program from SPL (for reminder, Figure 1.10), Mint Accounts are responsible for storing the global information of a Token and Token Accounts store the relationship between a wallet and a Mint Account.

![Blockchain](../../images/spl-token.png)

Whilst Mint Accounts contain a few data attributes such as its current supply, it doesn't offer the ability to inject standardized data that can be understood by apps and marketplaces. This is why the Token Metadata program offers a Metadata Account that attaches itself to a Mint Account via a PDA.

![Blockchain](../../images/metaplex-metadata-account.png)
