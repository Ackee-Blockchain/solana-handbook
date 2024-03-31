# Turbine –⁠ Block Propagation Protocol

Turbine is a name for a smart block propagation protocol that reduces the time needed for block propagation and the overall message complexity reducing the communication overhead of a node.

Turbine is a multi-layer propagation protocol. First, nodes in the network are divided into small partitions called neighborhoods. Nodes within a particular neighborhood are responsible for sharing received data with other nodes in the same neighborhood and propagating the data to a small number of nodes in other neighborhoods (Figure 1.3 and 1.4). The data unit shared is called a shred, and one block is constituted of many shreds.

The partitioning of nodes into neighborhoods and how exactly are shreds shared within and out of their neighborhoods are implementation details.

Since we are in an adversarial environment, any node can decide not to rebroadcast the received shreds or broadcast incorrect data.

These two problems are solved with a series of countermeasures:

- Forward Error Code (FEC), specifically the Erasure Code, helps by broadcasting a block with more shreds than initially needed to reconstruct the entire block without errors, even if some shreds are lost along the way. With N = 6 data shreds and additional K = 3 shreds, we can lose up to 1/3 of the shreds and still be able to reconstruct the entire block fully.
- Propagation is prioritized according to their stake. Validators with the most stake are put closer to the current leader. A stake-weighted selection algorithm is used to create a tree where the risk of faulty or malicious nodes is minimized.

![Blockchain](../../images/neighbours.png)
![Blockchain](../../images/neighbours2.png)
