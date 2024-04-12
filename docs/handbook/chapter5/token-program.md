# Token Program

A Token program on the Solana blockchain. This program defines a common implementation for Fungible and Non Fungible tokens.

All tokens on Solana, whether they are fungible tokens or NFTs (see Figure 1.9), are created using the SPL Token Program. If you’re familiar with Ethereum, you can think of SPL tokens as a token standard such as ERC-20 or ERC-721. One key difference, however, is that Solana does not require you to deploy a new contract for each token you create. Instead, it simply requires you to send instructions to the Token Program and it will create and mint tokens on your behalf.

![Blockchain](../../images/token_program.png)

## Creating a new Token

A new Token can be created by initializing a new Mint with the InitializeMint instruction. The Mint is used to create or "mint" new tokens, and these tokens are stored in Accounts. A Mint is associated with each Account, which means that the total supply of a particular token type is equal to the balances of all the associated Accounts (see Figure 1.9 for mentioned fields).

Once a Mint is initialized, the mint_authority can create new tokens using the MintTo instruction. As long as a Mint contains a valid mint_authority, the Mint is considered to have a non-fixed supply, and the mint_authority can create new tokens with the MintTo instruction at any time.


## Transferring Tokens

Balances can be transferred between Accounts using the Transfer instruction. The owner of the source Account must be present as a signer in the Transfer instruction when the source and destination accounts are different.

The image provided below depicts the process of token transfer. Further information about Associated Token Accounts (ATA) will be covered in subsequent sections.


## Burning Tokens

The Burn instruction decreases an Account's token balance without transferring to another Account, effectively removing the token from circulation permanently.

There is no other way to reduce supply on chain. This is similar to transferring to an account with an unknown private key or destroying a private key. But the act of burning by using Burn instructions is more explicit and can be confirmed on chain by any parties.


## Freezing Accounts

The Mint may also contain a freeze_authority which can be used to issue FreezeAccount instructions that will render an Account unusable. Token instructions that include a frozen account will fail until the Account is thawed using the ThawAccount instruction. The SetAuthority instruction can be used to change a Mint's freeze_authority.

## Wrapping Sol

The Token Program can be used to wrap native SOL. Doing so allows native SOL to be treated like any other Token program token type and can be useful when being called from other programs that interact with the Token Program's interface.

Accounts containing wrapped SOL are associated with a specific Mint called the "Native Mint"

These accounts have a few unique behaviors:

- InitializeAccount sets the balance of the initialized Account to the SOL balance of the Solana account being initialized, resulting in a token balance equal to the SOL balance.
- Transfers to and from not only modify the token balance but also transfer an equal amount of SOL from the source account to the destination account.
- Burning is not supported
- When closing an Account the balance may be non-zero.


## Non-Fungible Tokens

An NFT is simply a token type where only a single token has been minted.
A more comprehensive discussion about NFTs is conducted in [Appendix B](../appendixB/index.md).
