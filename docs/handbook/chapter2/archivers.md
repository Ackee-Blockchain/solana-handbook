---
hide:
  - toc
---

The Solana blockchain can grow at enormous speed, making it very challenging for each node to store the complete history of transactions. To address this, there is a concept of **distributed ledger storage** that would store this data in a decentralized fashion for everyone else.

!!! insight

    At the network speed of **1 Gbps**, the Solana blockchain would generate roughly **4 petabytes** of data over the course of **1 year**.

Given how impractical it would be for every validator to keep a full copy of blockchain's history, the idea is to offload the data from validators to these specialized, lightweight network nodes called **Archivers**. The data is split into many small pieces and replicated so that the full state can always be reconstructed. These specialized nodes are also regularly challenged at the protocol level using a mechanism called **Proof of Replication**. This ensures that nodes store the correct data and prevents data loss.

!!! note

    This concept is yet to be implemented.
