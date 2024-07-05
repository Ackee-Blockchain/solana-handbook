The following steps can be thought of as an overview of what happens when an app or any user interacts with the Solana network by sending a transaction. Terms, such as instruction, account, or program, will be explained shortly, followed by a more in-depth explanation.

- An app or a user sends a transaction with one or more instructions to a Solana node that accepts RPC requests.

- The transaction gets validated and forwarded according to the deterministic leader schedule to the next leader.

- The transaction is validated and processed by the leader and included in a new block, which is then streamed to all other validators who also validate and process the transaction to reach the same final state.

- During processing, the instructions in the transactions are passed to programs that the developers have deployed in advance. This is the job of the Sealevel runtime. The relevant accounts are modified by code in those programs. Everything happens isolated in the VM. Instructions are executed sequentially and atomically, which means that either all instructions finish successfully or all changes made by any instruction within the transaction are discarded.
