# Proof-of-History (PoH) –⁠ Virtual Clocks

Agreement on time in distributed systems has always been problematic. First, a high-level overview of this concept is described, followed by an in-depth description.

Solana leverages the so-called Proof-of-History (PoH) mechanism to synchronize local virtual clocks on all nodes. PoH ensures that the timestamp in any message can be trusted and that any timeouts in the consensus protocol can be avoided because everyone knows the time and knows whether to start a new round of consensus or not. PoH allows minimizing the block time as there’s no waiting overhead. In other words, thanks to synchronized clocks, communication can be replaced by local computation.

To prevent validators from skipping the validator that comes before them, PoH is used to force all validators to spend a minimum amount of time before they can even submit their block. Thus, if validator B follows validator A, B cannot attempt to skip A by chaining off its previous block because B has to run the Proof-of-History algorithm at least as long as A does, so A gets a fair chance to submit their block.


## Verifiable Delay Function (VDF)

PoH is based on a Verifiable Delay Function (VDF). Specifically, Solana uses a recursive pre-image resistant SHA256 VDF, where the output of one SHA256 iteration is recursively used as the next iteration’s input.
To create a block, the producer needs to compute the VDF with all new messages to be included in the block:

```
Message1 → Hash1
Hash1 + Message2 → Hash2
Hash2 + Message3 → Hash3
…
Hashn-1 + Messagen → Hashn
```

### Observations:

- From PoH, we have a proof of the Lower Bound on the time of Messagei (i.e., Messagei must have taken place after Hash<sub>i−1</sub>).
- From PoH, we have a proof of the Upper Bound on the time of Messagei (i.e., Messagei must have taken place before Hash<sub>i</sub>).
- Points 1 and 2 prove the exact order of the messages, which implies that VDF not only provides us virtual clocks, but everyone can trust the order of events.

### Phases of PoH:

- Evaluation phase (leader): computation on only one CPU core as it is a strictly sequential computation by definition. This takes:

$$
\frac{total\_number\_of\_hashes}{hashes\_per\_second\_for\_single\_core}
$$

- Verification phase (voters): the block can be checked in parallel using GPU with thousands of cores as it can be easily sliced and the intermediate hashes are known; this takes:

$$
\frac{total\_number\_of\_hashes}{hashes\_per\_second\_for\_single\_core * number\_of\_cores\_available}
$$


Thus, it can be concluded that PoH is difficult to produce but easy to verify. These are two important factors that are crucial for the use of PoH –⁠ it is not easy to falsify the PoH, but once it is finished, any validator can verify the results very quickly.




<!-- ![Blockchain](../../images/blockchain.png) -->
