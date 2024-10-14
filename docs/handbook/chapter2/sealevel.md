---
hide:
  - toc
---

Sealevel is a runtime developed by the Solana team that allows for the parallel processing of smart contracts. It can process as many transactions as many cores are available in the system. This is a major improvement, making Solana a multi-threaded global state machine.

!!! important

    **A high-level overview of how Sealevel works:**

    - Sort pending transactions.
    - Schedule non-overlapping transactions to run in parallel.

The reason this is possible with Solana is that each and every transaction explicitly defines states it will read from and write to. Sealevel can then choose non-overlapping instructions to be executed in parallel. Additionally, transactions that only read certain states can be executed in parallel as well.

!!! note

    Other blockchains operate as single-threaded global state machines. The only thing they might do in parallel is signature verification.

<h2>Berkeley Packet Filter</h2>

The standard way to execute code on a blockchain is to use a Virtual Machine (VM) and compile the code, written in various supported languages, into bytecode. This code then gets deployed to the blockchain, and when the user sends a transaction invoking the contract, the code gets loaded into the VM and executed.

Ethereum does this using its own Ethereum Virtual Machine (EVM). Some other blockchains make use of Web Assembly (WASM). Solana iterated through several solutions and chose a variant of the Berkeley Packet Filter (BPF) for its virtual machine.

Sealevel hands off transactions to the VM, where they are executed as BPF bytecode. BPF and its extended version, eBPF, originally designed for high-performance packet filtering in networking systems, are in-kernel VMs available in most UNIX-like operating systems.

!!! important

    Solana uses **Rust Berkeley Packet Filter (rBPF)** which is a modified version of eBPF optimized for Solana's architecture.
