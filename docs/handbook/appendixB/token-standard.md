# Is this all ? “No, Token Standard”

As token usage has evolved on Solana, it has become clear that there are more types of tokens than simply "fungible" and "non-fungible" tokens.

An example is something the community is calling a "semi-fungible token", an SPL token with a supply greater than 1 but which has typical NFT attributes such as an image and an attributes array in the JSON metadata.

The consensus seems to be that these should be stored in wallets in the same view as standard NFTs, or in their own view but separate from "standard" fungible SPL tokens. These tokens are becoming popular in gaming contexts to support fungible items such as a kind of sword or a piece of wood, etc. but which are in a different league from typical fungible SPL tokens such as USDC.

The Token Standard field (in Metadata Account) can have the following values:

- NonFungible: A non-fungible token with a Master Edition.
    - Examples of these are Solana Monkey Business, Stylish Studs and Thugbirdz.
- FungibleAsset: A token with metadata that can also have attributes, sometimes called Semi-Fungible.
    - An example of this kind of token is something the community has been calling "semi-fungible tokens" often used to represent a fungible but attribute-heavy in-game item such as a sword or a piece of wood.
- Fungible: A token with simple metadata.
    - USDC, GBTC and RAY.
- NonFungibleEdition: A non-fungible token with an Edition account (printed from a Master edition).
    - very similar to NonFungible (more here).
- ProgrammableNonFungible: A special NonFungible token that is frozen at all times to enforce custom authorization rules.
    - This standard is similar to the Non-Fungible standard above, except that the underlying token account is kept frozen at all times to ensure nobody can transfer, lock or burn Programmable NFTs without going through the Token Metadata program. This enables creators to define custom authorization rules for their NFTs such as enforcing secondary sales royalties.


## Programmable Non-Fungible-Tokens
Because the Token Metadata program builds on top of the Solana Token program, anyone can transfer tokens (fungible or not) without going through the Token Metadata program. In other words, Metadata Account contains field Seller Fee Basis Points, which holds information about secondary sales royalties. The problem is, if we want to transfer tokens (fungible or not), we don't use Metaplex (as its only purpose is to store additional data), however we use SPL for Token Transfer. Whilst there is Seller Fee Basis Points attribute on the Metadata account, it is purely indicative and anyone could create a marketplace that does not honor royalties — which is exactly what happened.

Programmable NFTs were introduced to solve this problem. They are a new opt-in Token Standard that keeps the underlying token accounts frozen at all times. That way, nobody can transfer, lock or burn Programmable NFTs without going through the Token Metadata program.

It is then up to the creators to define custom operation-specific authorization rules (Figure 1.14) that will be enforced by the Token Metadata program. These are defined in a special RuleSet account which is attached to the Metadata account. An example of such a RuleSet could be an allowlist of program addresses that honor royalties. RuleSets are part of a new Metaplex program called Token Auth Rules.

![Blockchain](../../images/programmable.png)
