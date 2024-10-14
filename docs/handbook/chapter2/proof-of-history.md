---
hide:
  - toc
---

Achieving agreement on time in distributed systems has always been problematic. Solana uses a timekeeping protocol called **Proof of History (PoH)** to synchronize local virtual clocks on all nodes. PoH ensures that the timestamp in any message can be trusted and that any timeouts in the consensus protocol can be avoided because every node knows the current time and when to begin a new consensus round.

!!! important

    Proof of History minimizes block time by eliminating waiting overhead. Thanks to synchronized clocks, communication can be replaced by local computation.

To prevent validators from skipping their predecessors, PoH is used to force all validators to complete some computational work making them wait specific amount of time before they can submit their block.

!!! example

    If validator B follows validator A, B cannot attempt to skip A's block by chaining off the previous block because B has to run the PoH algorithm for at least as long as A did. This gives validator A a fair chance to submit their block.

!!! warning

    Proof of History is **neither** a consensus mechanism **nor** a Sybil resistance mechanism!

<h2>Verifiable Delay Function</h2>

PoH is based on a **Verifiable Delay Function (VDF)**. Solana uses a recursive, pre-image-resistant SHA-256 VDF, where the output of one SHA-256 iteration is recursively used as the input for the next.

To create a block, the producer needs to compute the VDF with all new messages to be included in the block:

<pre><code>Message<sub>1</sub> → Hash<sub>1</sub> <br>
Hash<sub>1</sub> + Message<sub>2</sub> → Hash<sub>2</sub> <br>
Hash<sub>2</sub> + Message<sub>3</sub> → Hash<sub>3</sub> <br>
... <br>
Hash<sub>n-1</sub> + Message<sub>n</sub> → Hash<sub>n</sub></code></pre>

!!! note

    Using PoH, we are able establish the exact order of messages because we can prove that **Message<sub>n</sub>** occured after **Message<sub>n-1</sub>** and before **Message<sub>n+1</sub>**.

<h2>Phases of PoH</h2>

- **Evaluation phase (leader):**

    During this phase computation takes place on only one CPU core, as PoH requires **strictly sequential processing** by definition.

    This phase takes:

$$
\frac{total\ number\ of\ hashes}{hashes\ per\ second\ for\ single\ core}
$$

- **Verification phase (voters):**

    In verification phase, blocks can be **checked in parallel** using GPU with thousands of cores since the intermediate hashes are known.

    This phase takes:

$$
\frac{total\ number\ of\ hashes}{hashes\ per\ second\ for\ single\ core \times number\ of\ cores\ available}
$$

!!! important

    The key takeaway is that while PoH is **computationaly intensive to produce**, it can be **verified very quickly** by validators.




<!-- ![Blockchain](../../images/blockchain.png) -->
