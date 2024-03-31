# Pipelining – Transaction Processing Optimizations

It is not enough to be able to form a consensus and share a block with the rest of the network quickly. A node must validate and execute all those transactions in received blocks before another block comes.

For this reason, the Solana team developed something called the Transaction Processing Unit (TPU) [14]. The TPU works as a processor and extensively uses pipelining, a common CPU optimization that helps keep the chip more utilized by splitting an instruction execution into stages. It is a general way to keep all the hardware parts busy instead of idle. This concept of pipelining was borrowed, and that is how the TPU was born.

The pipeline stages of TPU are following (Figure 1.6):
- Data fetch in kernel space via network card (I/O)
- Signature verification using GPU (very computation heavy if not offloaded)
- Change of the state using CPU (banking)
- Write to the disk in kernel space and send out via network card (I/O)

![Blockchain](../../images/tpu.png)

In fact, there are two TPUs in the Solana node software. The one called TPU is used for creating a new block, and the second one, TVU, where the V stands for validator or validation, is used for validating. They may slightly differ. However, the concept and functionality are very similar.
