---
hide:
  - toc
---

Programs can issue instructions that include accounts that were not signed in the original transaction by using **Program Derived Addresses (PDAs)**. These accounts are referred to as PDA accounts. PDAs allow for programmatically generated addresses to be used without needing a private key when invoking instructions of other programs.

PDA is an address deterministically derived from the **program ID** and **supplied seeds** (keywords). However, the resulting address is bumped off the Ed25519 curve with a so-called **bump seeds**. This ensures that no private key exists for the PDA.

<h2>PDA Generation</h2>

When generating a PDA there is approximately 50% chance that the address will fall on the elliptic curve, meaning it has a corresponding private key. To avoid this, system uses bump seeds, an 8-bit number, to "bump" the address off the curve.

![PDA Generation](../../images/pda-generation.png)

!!! insight

    To find a suitable bump seed, the program iterates through possible values from 255 down to 0. The first bump that works is known as the **canonical bump**.

!!! warning

    Other bump seeds beyond the canonical bump may also result in a valid PDA. However, for security reasons, it is recommended to **only use the canonical bump**.

When a program tries to invoke a [CPI](./cross-program-invocation.md) with PDA, the runtime takes the supplied keywords and bump seeds, uses the caller’s program ID, and repeats the process. If the resulting PDA matches, the account is considered to be signed.
