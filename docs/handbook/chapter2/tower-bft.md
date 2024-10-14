---
hide:
  - toc
---

<h2>Tower Byzantine Fault Tolerance</h2>

Solana uses **Tower Byzantine Fault Tolerance (TBFT)** as its consensus algorithm, which is a custom implementation of the Practical Byzantine Fault Tolerance (PBFT) algorithm published in 1999 by Miguel Castro and Barbara Liskov.

The goals of PBFT are to ensure:

- **Safety**: Results are valid and identical across all non-faulty nodes.
- **Liveness**: Nodes that don’t fail will always produce a result.

!!! note

    Safety is guaranteed because the process is deterministic, meaning it always produces the same results across all non-faulty nodes. The liveness guarantee is enabled by the view-change mechanism, which allows nodes to switch leaders if the current leader appears to be malicious or faulty.

<h2>View-change</h2>

View-changes occur when a leader appears to have failed, and so another node attempts to take his place by initiating an election process. This process is triggered by timeouts that prevent nodes from waiting indefinitely for unexecuted requests. The timeout is postponed whenever the protocol detects that nodes are nearing agreement on the current block.

<h2>TBFT vs PBFT</h2>

TBFT is a variation of PBFT, with one key difference. [Proof of History](./proof-of-history.md) provides a global source of time before consensus is reached and can therefore be used to enforce the exponentially increasing timeouts introduced in the original PBFT algorithm. No additional messages are needed because PoH itself enforces the timeouts, thereby reducing communication overhead.
