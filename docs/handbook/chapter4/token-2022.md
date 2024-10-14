---
hide:
  - toc
---


The Token-2022 program extends the functionality provided by the [Token program](./token-program.md). This means that the Token-2022 program is not only backward compatible but also includes all the functions of the original Token program, as well as additional functionality often referred to as token extensions.

!!! info

    One associated token account program still creates token accounts for both Token and Token-2022.

!!! tip

    To see the source code, check out [Solana Program Library Token-2022 program](https://github.com/solana-labs/solana-program-library/tree/master/token/program-2022).

<h2>Benefits</h2>

- **Flexibility**

    Some token extension are [incompatible](https://solana.com/developers/guides/token-extensions/getting-started#what-extensions-are-compatible-with-each-other), however, you can create a variety of custom combinations that fit your needs.

- **Reduced risk**

    Using audited and well-tested extensions helps protect protocols and funds.

- **Reduced testing costs**

    Extensions are added by specifying the extensions in code, this reduces number of errors and saves time on testing.

- **Reduced development time**

    Extensions are uniform and reusable, which significantly speeds up development.


<h2>Extensions</h2>

There are two types of extensions:

- **Mint Extensions**
- **Token Account Extensions**

!!! note

    - **Mint extensions** are added on top of the original Solana Token program and extend the capabilities of tokens.
    - **Token account extensions** are added on top of Solana accounts and add account-related features.

Mint extensions:

- **Confidential transfers**: Confidential transactions that do not reveal the amount transferred.
- **Transfer fees**: Collection of fees on each transfer. The fees are then sent to a specified account.
- **Mint close authority**: Enables mint owners to close their accounts and reclaim the lamports.
- **Transfer hook**: Calls specific programs when a token transfer occurs.
- **Interest-bearing tokens**: Set an interest rate on a token. The interest can be tracked and displayed.
- **Non-transferable tokens**:  Restrict token transfers between users.
- **Permanent delegate**: Permanently assign a delegate that has the authority to manage token accounts of a given mint.
- **Metadata pointer**: Allows token creators to link an external address that contains the official metadata of the token.
- **Metadata**:  Allows integration of metadata into tokens through custom fields.

Token account extensions include:

- **Memo required on transfer**: Requires an attached memo as a message during each token transfer.
- **Immutable owner**: Makes it impossible to reassign ownership of an account.
- **Default account state**: Freezes all new token accounts so that users must interact with the project in some way to unfreeze the accounts/tokens.
- **CPI guard**: Restricts how other programs can interact with your token by prohibiting certain actions inside cross-program invocations.

!!! note

    You can find a list of Token-2022 extensions in the [documentation](https://spl.solana.com/token-2022#extensions).
