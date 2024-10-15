---
hide:
  - toc
---

<h2>Merkle Tree</h2>

A Merkle tree is a data structure that organizes data into a tree-like form.

- Each **leaf node** inside this tree represents a hash of some data.
- Each **non-leaf node** represents a hash of its child nodes.

The root is a compact representation of all data stored in the tree. Merkle trees allows us to easily verify integrity of the data without having to store all of it on-chain.

??? note "Tree Terminology"

    [**Tree**](https://en.wikipedia.org/wiki/Tree_(graph_theory)) is a term from [graph theory](https://en.wikipedia.org/wiki/Graph_theory) and it refers to a type of a graph.

    <div class="grid" markdown>

    - **Root node** is the top-most node of a tree, which does not have a parent. *(example node A)*
    - **Non-leaf node** is a node that does have children in the tree. *(example nodes A and B)*
    - **Leaf node** is a node that **does not** have any children in the tree. *(example nodes C, D and E)*

    ``` title="Example Tree Graph"

               A is the root of the tree   A
                                          / \
        B is a parent of nodes D and E   B   C
                                        / \
              D is a child of node B   D   E
    ```

    </div>

<h2>Account Compression Program</h2>

Minting a single NFT may be relatively inexpensive, however, the cost of storing the asset's data on-chain can quickly become uneconomical as the quantity increases.

The **Account Compression program** is an on-chain system designed to address the rising concern of storage costs on Solana.

The solution lies in storing a compressed hash of the asset data on-chain, while the actual data is stored off-chain in a database. The data is split into pieces, a Merkle tree is built and only the Merkle root is stored on-chain.

!!! info

    The account compression program uses a special type of Merkle tree called a [concurrent Merkle tree](https://spl.solana.com/account-compression/concepts). Concurrent Merkle trees allow simulataneous data changes to occur while still maintaining the integrity of the tree.

<h2>Zero-Knowledge Compression</h2>

!!! important

    **Zero-knowledge (ZK) proofs** allow one party to prove to another party that some statement is true without revealing any information about the statement itself.

ZK proofs can be used to further reduce the amount of data that needs to be stored on a blockchain. With ZK proofs, we can verify that certain calculations or balances are correct without needing to store or reveal the underlying data.
