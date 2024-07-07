Runtime policy or Sealevel runtime account rules are a set of rules enforced by the Sealevel runtime to protect the security of the system and make Solana a safe and predictable environment for its users.

**The following list of rules is taken from the official documentation:**

1. Only the owner of the account may change owner.
    - And only if the account is writable.
    - And only if the account is not executable.
    - And only if the data is zero-initialized or empty.
2. An account not assigned to the program cannot have its balance decrease.
3. The balance of read-only and executable accounts may not change.
4. Only the owner may change account size and data.
    - And if the account is writable.
    - And if the account is not executable.
5. Executable switch is a one-way (false→true) operation, and only the account owner may set it.
6. No one can make modifications to the rent_epoch associated with this account.

## Compute Budget

Each transaction is given a compute budget to prevent abuse of the Solana nodes’ resources that could potentially lead to network failures or denial of service. When the program consumes its entire compute budget or exceeds certain bounds, the runtime halts the currently running instructions and returns an error.