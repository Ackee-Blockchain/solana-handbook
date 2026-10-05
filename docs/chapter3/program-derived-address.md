---
hide:
  - toc
---

Programs can issue instructions that include accounts that were not signed in the original transaction by using **Program Derived Addresses (PDAs)**. These accounts are referred to as PDA accounts. PDAs allow for programmatically generated addresses to be used without needing a private key when invoking instructions of other programs.

PDA is an address deterministically derived from the **program ID** and **supplied seeds** (keywords). However, the resulting address is bumped off the Ed25519 curve with a so-called **bump seeds**. This ensures that no private key exists for the PDA.

<h2>PDA Generation</h2>

When generating a PDA there is approximately 50% chance that the address will fall on the elliptic curve, meaning it has a corresponding private key. To avoid this, system uses bump seeds, an 8-bit number, to "bump" the address off the curve.

![PDA Generation](../images/pda-generation.png)

<iframe src="https://plgrnd.io/embed?theme=dark&ref=ackee-handbook#flow=N4IgbiBcDMA0IDsD2ATApgZygbVASxShAGMBGEeAFwE8AHNIgYQHkBZVgUQDkAVCkWkgx5KeJAiigAHlAAM8alAC0paLIC+8FAENK2ySEpoplIjwAWaAAQAzPAHMArgCc0sKwBs8YNJCsY0NBQMKwBqK1pnJHtnbQBbKwBJABErQCTCKwBlAAkAQSUAJgBWADZ0qwAFZNywqwAjRzjaAB0EDm1ic0rqq2R0K0pnPEx6xtorYqL3YoAWd0AyAitHBFEPAcsrbRQUVwwQvBCkGxt16w4USdIATitiFx8AOkqomPik5L9KDczqDCMEiovWJxdzaELaXpoRyDbRrYzxWgeNAPEDqTT4QiQQyyfg0ehmDgADT48EEwlE4gMMkg8hAihpmhAOj0BiMJiIpE5XO5PN5fO5qPRIAIREo5CodAYWJ4RJJAiEIjEEkg0jkCigJQKjOZ+hVhmMpixYG0jg8pjRsAxooKuMlBOJ-DJispeuptPppBmGi0ul1oDZhpA9g8SDqsMFluFmMM0Ft+OlssdCopytVNPVkAKpAAHNrfayDURHAFnAB9HURq1YygzONSkAyh2k5NKqlqulQArZ71M-N6gNEbNFABiCAAalcAJrmJAj6CkOrJbRcGb2LiOTKOGwAJTAAEUpCgAF54AqTgCqBRQAHZoFIAFb3gDiFQA1pWo0RaOLDHasVVciTclW1dKBoC9DMvTzFkVQtKsBBtCV4xAACgOdVMQGpcD3SgT0ewrWChRFLFaFjJD61Q5tgJdNNsIzAooJ9GDgDgz8sRQH88XrZJEkyCoABlcknNCUzbSAigKHCYHwvt-ULLEP2IplEN-ZCeL4wThKo9CxIkqTry1Ji-X1dkFNYpSUDI1TuN4gShJEkC0z0jNSC7aDjIHMyiOjFBa3Ioh1LsrT5WojDqWcjtIFIa8ZOYkzA0UnyijrALbM0hyaMwqAIvpApoBKdyC1MkBEqIFAShSrFAvS7TRNA8TJPo69cyMoqEvM6NiBsSqQBYdhuDlJ06totQM3y2KPPkkAACExhCSxXD8WYrAACkmKwAHcwSscRTlue40AASmmIoilWuxnD+AZnGoY6JiKWRzu8axBmGEIbG0PAkRQQ6nnOERNn8QIUE2BAQa2yhOj2homhRNEAF14CCexMBweCpGoJRkbQUtS0oWQlADJQhnscxKCUb8KaBeJEhQJQkRsUx4AwJAXGIet8f4Fm2bQbJtDBpFRQJomSbJ3FtGcFHA2-cXJbQSg+YF+tKciaJgVp+m0EZ1FIyUjGsZQFHcbFQmDWJhwyYp0glACIIAGICYZpmQG55x2dFH9XfZxWUEF6trZFi3nb0OXpc4iWpZ9v2BGt22UAdzXte8oh9ex43hbN0XydoAoqbVmm6adrnWbdjmcWZkvvf532y9NkxzdJ4OI-lr8VJDyPq+jnO89eOINaL5OsVTw2cbx3PA8binc7jhOi4rnnrWLnmo458fM6D2Wpdbzf5ZX1ubeB2etfNXXo2Ho28Yz+us4p6Ae-Vwvj6X0uhefqulaFuvyaznfpas9vd6d2VnfVWvd+5P0HphTGac8Z3wnpbUiB97aOyfvPF+1YrJe15kA0UcD16N1-l+f+zcFY4JInfGeKCk6nxTtAkexsZhfwbggihh9rZzxdpXDmflOHLzIYYRh8Cm6hyIb-Pe5CkHx3YRAmhQ86EXxVjoZh5MOJKDwAgWg0JE7OywV+T2XDxExwpkon+VASFlXDqHQxqj1GaPJgPWRUCDYKOtjDWgyilAXDURorRHDdEkX0Xwj+ASlBuOUYQ9ibcSHWNzrY3xMj0byNHt3WgJig6eLvnE+xqDeHoIQm-bBwSELGO0OEsxIj2LEKsfwyy3i7HaJ1ok5xyTc5hJvr5Op8TtZoPdiRFSWDDHdzaRvcpW92I8IAaQopHSskNMgefZJIC0mTxQEUTp2Tum5N6QITBBj+GINSaU0xhhzHsWSqMwB0y1mzIcU0mBiDhkrJKOshpPTgEFMGXfR5YsLmBnKmImpzybkQPhuoIAA" title="PDA derivation: seeds and bump" width="100%" height="520" style="border:0;border-radius:8px" sandbox="allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox" allow="clipboard-write" loading="lazy"></iframe>

!!! insight

    To find a suitable bump seed, the program iterates through possible values from 255 down to 0. The first bump that works is known as the **canonical bump**.

!!! warning

    Other bump seeds beyond the canonical bump may also result in a valid PDA. However, for security reasons, it is recommended to **only use the canonical bump**.

When a program tries to invoke a [CPI](./cross-program-invocation.md) with PDA, the runtime takes the supplied keywords and bump seeds, uses the caller’s program ID, and repeats the process. If the resulting PDA matches, the account is considered to be signed.
