---
hide:
  - toc
---

<h2>Memory Bottleneck</h2>

As the speed of computation increases, memory access becomes a new bottleneck. LevelDB is the industry-standard local database for storing blockchain data and state. However, it does not support parallel reads and writes. That is fine for Bitcoin or Ethereum, but not for a massively parallel system like Solana.

The sheer size of the blockchain state makes storing everything in RAM impractical even for large servers. To combat this, Solana had to invent its own database system that supports parallel reads and writes and scales easily with addition of more disks.


<h2>Cloudbreak</h2>

Cloudbreak is Solana's custom database. It makes use of memory-mapped files to store data in a way that allows for independent access to each file.

!!! info

    A memory-mapped file is a file that is mapped to the process’s virtual memory address space and can be accessed directly without further system calls.

The speed is still limited by the disk I/O, but we get less overhead, and the kernel can store a part of it in its page cache (also known as file cache).

- Reads are randomly distributed among available disks, as the data is stored evenly.
- Writes use Copy-on-Write semantics, appending new data sequentially to random disks.

Old data entries are garbage collected in order to preserve space for future use. The design of Cloudbreak makes it ideal for hardware setups, such as RAID 0 with fast NVMe SSDs.

!!! note

    The Cloudbreak database was benchmarked by the Solana team. The results show that even with **10 million accounts**, a size that does not fit in RAM, Cloudbreak still achieves **nearly 1 million of read and write operations per second** with a single SSD.
