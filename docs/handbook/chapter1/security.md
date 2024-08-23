## Sybil Resistance

To prevent a single entity from taking over the network, there must be a mechanism put in place so that no one can just spawn more nodes that can mine or vote (depending on the network) and thus subvert the network reputation system. These dishonest nodes would be able to out-vote honest nodes and start censoring transactions, approving invalid transactions, or changing the entire protocol.

Currently, the two most common Sybil resistance mechanisms are:

- Proof-of-Work
- Proof-of-Stake

 **Proof-of-Work** (PoW) employs a model where miners in the network are given a chance to mine a block that is proportional to their hashing power in the network. Miners basically compete with each other which makes PoW-based networks very energy-inefficient. Bitcoin uses PoW mechanism.

 **Proof-of-Stake** (PoS) is a type of model for voting-based networks, where a validator is given the power of their vote proportionally to staked coins. In each round one validator is randomly chosen to propose a new block, while others validate it. By eliminating competition among validators, PoS-based networks are significantly more energy-efficient.

## Consensus

To agree on a certain state of a blockchain, network nodes need to reach a consensus. We assume there are malicious nodes in the network. Therefore, the system must be able to withstand not only simple node failures but also attacks to a certain extent. BFT ([Byzantine Fault Tolerance](https://en.wikipedia.org/wiki/Byzantine_fault)) is thus a desired property of such a distributed system.

There are three widely used consensus families:

1. **PBFT-like (Practical BFT) algorithm family**: Nodes achieve consensus through a series of voting rounds which ensures that the network can function properly even if some nodes are malicious or fail.
2. **Nakamoto consensus**: This family combines a Sybil resistance mechanism of Proof-of-Work with the longest-chain rule. It was invented by Satoshi Nakamoto for Bitcoin in 2008.
3. **Avalanche Consensus**: A new family introduced in 2018. Nodes randomly sample each other, "gossip", and repeatedly vote.

## Security

Consensus and Sybil resistance mechanism are often confused as the same thing, which is not true and is worth pointing out. One works in conjunction with the other. Let’s look at how this works in both PoW-based and PoS-based networks.

Consider what makes Bitcoin, a PoW-based network, theoretically secure – it is the fact that only the longest chain is respected, also commonly known as the longest chain rule. This is why the consensus is called, as mentioned before, the Nakamoto consensus.

For a PoS-based network, the Sybil resistance mechanism is usually associated with a variant of a PBFT-like algorithm or the novel Avalanche consensus.

!!! note

    Solana uses **Proof-of-Stake** mechanism coupled with a timekeeping protocol called [**Proof-of-History**](../chapter3/proof-of-history.md).
