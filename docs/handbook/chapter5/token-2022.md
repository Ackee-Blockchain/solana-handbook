# Token 2022 Program

The Token-2022 Program [20] extends the functionality provided by the Token Program. This means that the Token-2022 program is backward compatible and includes all the functions of the original Token program, as well as additional functionality often referred to as token extensions. You can think of the extensions as a series of options, features, and capabilities built into the newest iteration of the Solana token program.

## Benefits

- **Flexibility**: Token issuers can choose to enable any combination of token extensions.
- **Reduced risk**: Using audited and well-tested extensions reduces attack vectors and helps to protect protocols and funds.
- **Reduced testing costs**: Because the extensions are added by simply specifying the extensions in your code, the chances of defects and human error are greatly reduced, saving on testing time and costs.
- **Reduced development time**: Because the extensions are uniform and reusable, the time required to develop applications using the extensions is significantly reduced.


## Extensions

Extensions can be of two types: mint and account extensions. All of these extensions can be used out-of-the-box.

Mint extensions are added on top of the original Solana Token Program and extend the abilities of tokens. Account extensions are added on top of Solana accounts and add account-related features.

Current mint extensions include 14 extensions. Some of the most important are:

- **Confidential transfers**: Allow confidential transfers between participating users without revealing the amount of the transfer.
- **Transfer fees**: Allow transfer fees to be charged on each transfer and sent to a defined account.
- **Mint close authority**: Allows owners to close mint accounts and reclaim the lamports on the mint account.
- **Transfer hook**: Allows calling specific programs with each token transfer.

Current account extensions include:

- **Memo required on transfer**: Requires an attached memo as a message during each token transfer. This could be used for regulatory compliance, reporting, and enhanced audit trails. Immutable owner: Makes it impossible to reassign ownership of an account.
- **Default account state**: Freezes all new token accounts so that users must interact with the project in some way to unfreeze the accounts/tokens.
- **CPI guard**: Restricts how other programs can interact with your token by prohibiting certain actions inside cross-program invocations.
- **Reallocate**: Some extensions can be enabled after account creation. Reallocate allows owners in this situation to reallocate their token account to create room for more extensions.
For a complete explanation and guide about the Token 2022 Program and its extensions see [20].
