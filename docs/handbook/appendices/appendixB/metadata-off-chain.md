---
hide:
  - toc
---

One important attribute of the [metadata account](./token-metadata-program.md) is the **URI** attribute that points to a JSON file off-chain. This is used to safely provide additional data whilst not being constrained by the fees involved in storing on-chain data. That JSON file follows a certain standard that anyone can use to find useful information on tokens.

!!! note

    The JSON file can be stored using a permanent storage solution such as [Arweave](https://www.arweave.org/) to ensure it cannot be updated. Additionally, one can use the **Is Mutable** attribute of the metadata account to make it immutable.

<h2>Arweave</h2>

Arweave is a **decentralized**, **trust-minimized**, **censorship-resistant** data storage network designed to retain data permanently, making it a great fit for NFTs. To cover the cost of storing your media forever, storage and mining fees are paid at the time of upload and distributed to storage providers participating in the network.

<h3>Storage Fees</h3>

Storage fees are based on the total size of the files you upload to the network during NFT creation. Each NFT consists of three files:

- The asset (image, video, audio, etc).
- The accompanying metadata file (attributes etc.).
- A generated manifest which creates a logical grouping or relationship between your files.

The cumulative size of these files (in bytes) is submitted to the Arweave storage cost estimation service which returns the real time estimated fee for storage, priced in winstons. We then convert the winstons to SOL for payment.
