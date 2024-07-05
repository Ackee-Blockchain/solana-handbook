Any user who chooses to interact with the network must interact with any of the network’s nodes via a JSON-RPC or a WebSocket endpoint. The available methods are all listed publicly in the Solana documentation.

The methods vary from queries, such as specific account information, the network state (example below) to sending transactions.

_Request of the **getBlockHeight** method:_

```bash
curl http://localhost:8899 -X POST -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","id":1,"method":"getBlockHeight"}'
```

_Response of the **getBlockHeight** method:_

```json
{ "jsonrpc": "2.0", "result": 0, "id": 1 }
```

What is really important is the ability to send transactions. Sending a transaction is the only way we can change data on the Solana blockchain. Any write operation is done through the means of transactions.

Users are not required to use the RPCs directly. There are several libraries that provide convenient interfaces for languages such as Javascript, Rust and Python.
