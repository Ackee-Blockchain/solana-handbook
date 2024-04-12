# Storing Metadata Off-chain

One important attribute of the Metadata Account is the URI attribute that points to a JSON file off-chain. This is used to safely provide additional data whilst not being constrained by the fees involved in storing on-chain data. That JSON file follows a certain standard that anyone can use to find useful information on tokens.

Note that, this JSON file can be stored using a permanent storage solution such as Arweave to ensure it cannot be updated. Additionally, one can use the Is Mutable attribute of the Metadata Account to make it immutable and, therefore, forbid the URI attribute — and other attributes such as Name and Creators — to ever be changed. Using this combination, we can guarantee the immutability of the off-chain JSON file.

## Arweave
Arweave is a decentralized, trust-minimized, censorship-resistant data storage network designed to retain data permanently, making it a great fit for NFTs. To cover the cost of storing your media forever, storage and mining fees are paid at the time of upload and distributed to storage providers participating in the network.

Arweave storage fees:

- Storage fees are based on the total size of the files you upload to the network during NFT creation. Each NFT consists of three files
        - The asset itself (image, video, audio, etc)
        - The accompanying metadata file (attributes etc.)
        - A generated manifest which creates a logical grouping or relationship between your files
- The cumulative size of these files (in bytes) is submitted to the Arweave storage cost estimation service which returns the real time estimated fee for storage, priced in winstons. We then convert the winstons to SOL for payment.

## Other possibilities

- AWS S3
- IPFS
- NFT.Storage
- Shadow Drive

For further details, refer to the documentation.
