---
hide:
  - toc
---

<h2>Fungible and Non-Fungible Tokens</h2>

**Fungible Tokens:** These tokens are interchangeable with one another. They are indistinguishable and hold the same value.

**Non-Fungible Tokens (NFTs):** Each NFT is a special digital asset that holds a unique information or value. NFTs can represent ownership of a specific digital or physical item, such as digital art or real estate.

<h2>Token Program</h2>

Token program defines a common implementation for fungible and non-fungible tokens. All tokens on Solana are created using the [SPL Token program](https://spl.solana.com/token).

!!! tip

    To see the source code, check out [Solana Program Library Token program](https://github.com/solana-labs/solana-program-library/tree/master/token/program).


!!! info

    Solana's **SPL tokens** are similar to Ethereum's **ERC-20** or **ERC-721** standards. However, Solana does not require you to deploy a new contract for each token you create. Instead, you simply send instructions to the Token program, which will create and mint tokens on your behalf.

![Blockchain](../images/token_program.png)

<h2>Creating Tokens</h2>

A token can be created by initializing a new [mint account](./mint-account.md). The mint account is used to create and hold info about new tokens, which are then stored in [token accounts](./token-account.md). Once a mint account is initialized, the **mint_authority** can create (mint) new tokens using the **MintTo** instruction.

!!! important

    As long as mint account contains a valid **mint_authority**, it is considered to have a non-fixed supply, and the **mint_authority** can create new tokens with the **MintTo** instruction at any time.

<h2>Transferring Tokens</h2>

Balances can be transferred between accounts using the **Transfer** instruction, with the source account owner required as a signer when the accounts differ.

<h2>Burning Tokens</h2>

The **Burn** instruction decreases an account's token balance without transferring to another account. The burnt tokens are permanently removed from the circulation, and this action can be verified on chain.

<h2>Freezing Accounts</h2>

The mint account may include a **freeze_authority**, allowing it to invoke **FreezeAccount** instruction that will make account unusable. Frozen accounts can be reactivated using the **ThawAccount** instruction and **freeze_authority** can be changed using the **SetAuthority** instruction.

<h2>Wrapping SOL</h2>

SOL can be wrapped and used like a Token program token when interacting with programs that use the Token program's interface. Accounts that hold wrapped SOL are associated with **Native Mint**. Wrapped SOL token accounts have unique behaviors, which you can learn more about [here](https://spl.solana.com/token#wrapping-sol).
