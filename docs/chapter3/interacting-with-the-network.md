---
hide:
  - toc
---

<h2>RPC Requests</h2>

Any user who chooses to interact with the network must communicate with one of the network’s nodes through a **Remote Procedure Call (RPC)** endpoint. The available [RPC methods](https://solana.com/docs/rpc) are listed in the Solana documentation.

The methods vary from simple queries, such as retrieving specific account information, or checking the state of the network, to sending transactions that modify state of the blockchain.

!!! example

    _Request of the **getBlockHeight** method:_

    ```bash
    curl https://api.mainnet-beta.solana.com -X POST -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","id":1,"method":"getBlockHeight","params":[]}'
    ```

    _Response of the **getBlockHeight** method:_

    ```json
    {"jsonrpc":"2.0","result":269624245,"id":1}
    ```

!!! important

    The ability to send transactions is crucial because is the only way we can alter data on the blockchain. All write operations, including account creation or transfer of tokens are done through transactions.

!!! info

    While users can interact with the blockchain through RPCs, it is not required. There are several libraries that provide convenient interfaces for languages such as **JavaScript**, **Rust** and **Python**.

<h2>Solana CLI</h2>

Typically, you will not be interacting with the network through raw RPC requests. Instead, you will often use a wrapper around them such as the interfaces mentioned above. **Solana's Command-Line Interface (CLI)** is a powerful tool that provides a more user-friendly experience for interacting with the blockchain.

!!! example

    Solana CLI allows you to:

    - **Generate a keypair**
    ```bash
    solana-keygen new
    ```

    - **View your public key**
    ```bash
    solana-keygen pubkey
    ```

    - **Check account balance**
    ```bash
    solana balance <account-address>
    ```

    - **Airdrop SOL** (available on Devnet and Testnet)
    ```bash
    solana airdrop 1 <account-address>
    ```

    For more detailed information, checkout the [documentation](https://docs.solanalabs.com/cli/).
