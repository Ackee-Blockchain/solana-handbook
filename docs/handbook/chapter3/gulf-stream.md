# Gulf Stream –⁠ Transaction Forwarding Protocol

Gulf Stream is Solana’s mempool-less solution for forwarding and storing transactions before processing them.

In traditional blockchains, each node reserves a part of its memory for the memory pool. This memory pool, more commonly referred to as mempool, is used to store transactions currently being broadcasted over the network but have not been processed and added to the blockchain as a part of a new block yet.

This implies a huge communication overhead where every transaction must reach every other node in the network. While not everyone necessarily needs to be aware of all transactions in the mempool, they are the most important for miner and validator nodes (depending on the type of a network), which must include them in new blocks.

If there are more transactions in the mempool than can fit in the block, the backlog of transactions is created. This can generally lead to increased transaction fees for users who need to push their transaction ahead of other transactions, as it is economically viable for the nodes securing the network to prefer transactions with higher fees. This is currently not possible on Solana, but on the other hand, the network is so fast with its ~400ms block rate that the aim is to process all remaining transactions almost instantaneously anyway.

## The Solution

The solution that Solana devised is to avoid having a single shared mempool and instead push transactions to the edge of the network to the expected leader. The leader receives the transaction as quickly as possible and can process it immediately.

However, this solution has a catch. The expected leader must be known ahead. Leaders are known in advance; their rotation is a function of the blockchain data and is known one full epoch before. An epoch is the number of slots for which one leader’s schedule is valid. It is set to 432,000 slots, and with a ~400ms block rate, it takes about two days.
