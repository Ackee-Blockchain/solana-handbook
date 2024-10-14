---
hide:
  - toc
---

<h2>Block</h2>

Block is a data structure that contains a header and a set of [transactions](./transaction.md). Header is comprised of three items – the **hash of the previous block’s header**, **metadata** and a **Merkle root**. Metadata depends on the protocol. The Merkle root is a root of the well-known [Merkle tree](../chapter4/account-compression-program.md), which can be used to verify later that transactions in a block have not been tampered with.

<h2>Blockchain</h2>

A blockchain can be thought of as a series of blocks or an append-only data structure that resembles an ordered back-linked [linked list](https://en.wikipedia.org/wiki/Linked_list), which uses hashes as pointers to previous blocks. This structure consists of blocks that form a chain, hence the term blockchain.

![Blockchain](../../images/blockchain.png)

!!! important

    **Header** is used to maintain the blockchain's integrity. If any part of the **header** changes, the hash will change, breaking the link to subsequent blocks.
