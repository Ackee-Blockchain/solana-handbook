# Cloudbreak –⁠ Horizontally-scalable Database

With fast computation, the obvious thing that becomes the new bottleneck is the memory. For example, the industry-standard local database for storing blockchain and state, LevelDB, does not support parallel reads and writes. That is fine for Bitcoin or Ethereum, but not for a massively parallel system like Solana.

We could ask the question, why not store everything in RAM? It is too big; even for enterprise machines and large servers, this becomes impossible over time. Therefore Solana had to invent its own database system that supports parallel reads and writes and scales easily with more disks.

This new database system is called Cloudbreak and makes use of memory-mapped files. The data is therefore stored in files that can be accessed independently. A memory-mapped file is a file that is mapped to the process’ virtual memory address space and can be accessed directly without further system calls. The speed is still limited by the disk I/O, but we get less overhead, and the kernel can store a part of it in its page cache (also known as file cache).

Reads in Cloudbreak are randomly distributed among available disks, as the data is stored evenly. Writes in Cloudbreak use the Copy-on-Write semantics and are appended to a random disk. Hence we get the speed of sequential writing. This is all possible thanks to a clever system of bookkeeping. Old data entries are also garbage collected for future use.

The design of Cloudbreak makes it ideal for hardware setups, such as RAID 0 with fast NVMe SSDs. The Cloudbreak database was benchmarked by the Solana team. The results show that even with 10 million accounts (unit of data storage on Solana that will be described in the Programming model), a size that does not fit in the RAM (i.e., cannot be cached by page cache in the kernel), Cloudbreak still achieves reads and writes close to 1 million with a single SSD.
