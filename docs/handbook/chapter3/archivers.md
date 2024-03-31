# Archivers –⁠ Distributed Ledger Storage

Given that the Solana blockchain can grow at enormous speed, considering a full capacity of 1 Gbps (with no overhead) for 365 days, it is roughly 4 petabytes of data that each node would need to store to have a complete history. There is a concept of a distributed ledger storage that would store this data in a decentralized fashion for everyone else.

The idea is to offload the data from validators to these specialized network nodes. The data is split into many small pieces and replicated so that the full state can always be reconstructed. These specialized nodes are also contested on the protocol level to ensure they store the data they are supposed to store, and the data loss is prevented.

This concept is yet to be implemented. A potential implementation might be using a new decentralized protocol for permanent storage Arweave or Filecoin.
