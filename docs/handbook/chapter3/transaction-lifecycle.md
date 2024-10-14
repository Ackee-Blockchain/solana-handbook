---
hide:
  - toc
---

The following steps can be thought of as an overview of what happens when an app or any user interacts with the Solana network by sending a transaction.

1. The user or app submits a transaction with one or more instructions to a node that accepts [RPC requests](./interacting-with-the-network.md).

2. The transaction is then forwarded, according to the leader schedule, to the next leader.

3. The leader validates the transaction, processes it, and includes it in a new block. This block is then broadcasted to all other validators who also validate and process the transaction.

4. During the transaction processing, instructions are executed by the previously deployed programs, and relevant accounts are modified accordingly.

!!! important

    Everything happens in an isolated virtual machine. Instructions are executed **sequentially** and **atomically**, which means that either all instructions in the transaction complete successfully or none of the changes are applied.
