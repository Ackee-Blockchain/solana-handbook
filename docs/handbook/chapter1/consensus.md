# Consensus

To agree on a certain state of a blockchain, network nodes need to reach a consensus. We assume there are malicious nodes in the network. Therefore, the system must be able to withstand not only simple node failures but also attacks to a certain extent. BFT ([Byzantine Fault Tolerant](https://en.wikipedia.org/wiki/Byzantine_fault)) is thus a desired property of such a distributed system.
Currently, only three viable consensus families can be used in practice. The first is the classic PBFT-like (Practical BFT) algorithm family. The second is a so-called Nakamoto consensus, which couples a Sybil protection mechanism of Proof-of-Work with the longest-chain rule, a novel consensus invented by Satoshi Nakamoto for Bitcoin in 2008. The third and newest family of consensus protocols known today is called Snow. Yet it is better known by its implementation name – Avalanche Consensus, introduced in 2018 and used for the Avalanche cryptocurrency.