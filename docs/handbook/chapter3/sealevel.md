# Sealevel –⁠ Parallel Smart Contract Runtime

Other blockchains are single-threaded global state machines. The only thing they might do in parallel is signature verification. Solana introduced Sealevel, a parallelized transaction processing engine designed to scale horizontally across GPUs and SSDs.

Sealevel can theoretically process as many transactions as many cores are available to the system. According to the source code,
Sealevel is not yet parallelized on the GPU level.

This is a major improvement that makes Solana a multi-threaded global state machine, a thing not seen until Solana. Other blockchains, including the leading Ethereum, can be considered single-threaded global state machines because only one smart contract invocation can be processed at a time.

The reason this is possible with Solana is that each and every Solana transaction describes all the states required to read and write to. Sealevel can then choose non-overlapping instructions to be executed in parallel and not only that. Transactions that only read certain states can be executed in parallel as well.

This is a high-level description of how it works:
- Sort millions of pending transactions.
- Schedule all the non-overlapping transactions in parallel.


## SIMD approach with GPUs

There is a great potential for GPU parallelization and leveraging its SIMD capability. For example, in Nvidia CUDA, modern cards have thousands of CUDA cores and tens of Streaming Multiprocessors.

When a CPU invokes a kernel grid, the blocks of threads are distributed among streaming multiprocessors and executed using specific ALU execution units, usually called CUDA cores and other SFUs (special function units).

The executed code is the same for all cores. Imagine a situation where there is a single smart contract invocation but with numerous different inputs. This exact workload can be efficiently executed on GPU architectures, such as Nvidia CUDA.

Since Sealevel is not yet optimized for GPU offloading, GPUs today are only used to accelerate PoH and signature verification and only if it is available to the system and the algorithm decides it is worth the overhead of launching the kernel grid.


## BPF – Berkeley Packet Filter


There is one important thing that has not been covered in Sealevel yet. What actually executes the code, and how it is done. The standard way is to use some sort of a Virtual Machine (VM) and compile the code for it from any supported language. This code gets deployed to the blockchain, and when the user sends a transaction invoking this contract, the code gets loaded into the VM and executed.

Ethereum does this using its own Ethereum Virtual Machine (EVM). Some other blockchains make use of Web Assembly (WASM). Solana iterated through all possible solutions and chose an unexpected VM called Berkeley Packet Filter (BPF).

Sealevel hands off transactions to be executed using an industry-proven bytecode called the Berkeley Packet Filter (BPF), designed for high-performance packet filters. It can also be used for non-networking purposes. BPF and the extended BPF (eBPF) are in-kernel VMs available in most UNIX-like operating systems. They are very performant because their primary use was for packet matching, which needs to be as fast as possible. It also has decades of development behind it.
The original version of BPF is now called classic BPF (cBPF), and this one could not be used for anything other than packet matching. The Linux kernel now includes only extended BPF (eBPF), a virtual machine with 64-bit registers. The eBPF is now called just BPF.

It is worth mentioning that new modern firewalls are being built on top of the extended BPF.  BPF execution is currently parallelized only on the CPU level. What is used is a modified version of BPF called rBPF, which runs in the user space instead of the kernel. This was important as the kernel version of the BPF would not be able to facilitate certain operations.
