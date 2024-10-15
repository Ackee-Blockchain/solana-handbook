---
hide:
  - toc
---

A smart contract is a piece of code deployed on a blockchain with a cryptographically signed transaction. Users can then interact with it by sending transactions that invoke a specific function defined in the smart contract and the business logic is executed as stated in the deployed code.

Data relevant to the smart contract state are also stored on the blockchain. Hence we can look at smart contracts as programs on a decentralized computer that access files in its file system and modify them according to the predefined rules. If such a contract is made immutable, we can trust that the smart contract will do nothing other than what it is supposed to do.

!!! note

    Apart from storing the blockchain itself, each node creates a state as a result of transaction execution. The final state is the result of all processed transactions and can always be deterministically recreated from the blockchain history.

<h2>ISA and Virtual Machines</h2>

Code is compiled for a predefined [Instruction Set Architecture (ISA)](https://en.wikipedia.org/wiki/Instruction_set_architecture) and executed in a Virtual Machine (VM) which understands it. The mentioned VM is a special runtime environment similar to well-known VMs such as Java Virtual Machine (JVM) or Common Language Runtime (CLR).

!!! info

    The Solana blockchain's execution environment is called **Solana Virtual Machine (SVM)**. It is written in Rust and enables the blockchain to handle thousands of transactions per second.

!!! note

    Only transactions involving smart contract execution need to be processed by the VM.
