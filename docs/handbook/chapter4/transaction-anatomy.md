**A Solana transaction consists of two major parts in the following order:**

- A compact array of signatures.
- A message that contains a compact array of account addresses followed by a recent blockhash and ending with a compact array of instructions.

![Transaction Anatomy](./../../images/transaction-anatomy.png)

## Signatures

**For signatures in the compact array of signatures, the Solana runtime verifies the following:**

- The number of signatures must match the first 8 bits of the message header.
- The signature is verified against the public key at the same index in the message’s account addresses array.

## Message

**The message layout is shown in the following table:**

![Message Layout](./../../images/message-layout.png)

1. Header
    - \# of required signatures in the transaction (8 bits).
    - \# of read-only accounts requiring signatures (8 bits).
    - \# of read-only accounts not-requiring signatures (8 bits).
2. Accounts
    - Addresses that require signatures with read-write access.
    - Addresses that require signatures with read-only access.
    - Addresses that do not require signatures with read-write access.
    - Addresses that do not require signatures with read-only access.
3. Recent blockhash
    - Transaction lifetime: transaction is deemed invalid if the blockhash is older than 32 blocks.
    - Transaction replay: identical txs get rejected, the blockhash can be changed and the exact same action repeated. It works in a similar way as nonce in Ethereum.
4. Instructions with the following instruction anatomy:
    - Program id index.
    - Compact-array of account address indices (indices to Accounts).
    - Compact-array of opaque 8-bit data (what operations to perform and any additional data).

![Instruction Anatomy](./../../images/instruction-anatomy.png)