---
hide:
  - toc
---

<h2>Mempool</h2>

In traditional blockchains, each node reserves a part of its memory for the memory pool, more commonly known as mempool. The mempool is used to store transactions that are currently being broadcasted over the network but have not yet been added to a block.

This creates a big communication overhead where every transaction must reach all nodes in the network. While not all nodes need to be aware of every transaction in the mempool, it is most important for miner and validator nodes (depending on the type of network), which must include them in new blocks.

!!! note

    If there are more transactions in the mempool than can fit into a block, a backlog of pending transactions is created.

<h2>Gulf Stream</h2>

Gulf Stream is Solana’s mempool-less solution for forwarding and storing transactions before processing them. Instead of having a single shared mempool, transactions are pushed to the next expected leader. This allows the next leader to quickly receive transactions and start processing them immediately.

!!! info

    For this to work, the next leader must always be known in advance. In Solana, leader rotation is scheduled one full [epoch](../chapter1/slots-epochs-leaders.md) ahead of time.
