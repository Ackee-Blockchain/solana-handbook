---
hide:
  - toc
---

Runtime policy is a set of rules enforced by the runtime to ensure security of the system:

1. **Account Modification**

       The contents of an account can only be modified by the program that owns the account. When an account is assigned to a program, its data is initialized to zero.

2. **Conservation of Balances**

       The sum of balances across all accounts must not change before and after transaction execution.

3. **Read-Only Account Balances**

       The balances of all read-only accounts cannot be changed by any program during transaction execution.

4. **Atomic Transaction Execution**

       All instructions are executed atomically. If any instruction fails, the entire transaction fails.

<h2>Compute Budget</h2>

Each transaction is allocated a compute budget to prevent abuse of node resources that could potentially lead to network failures or denial of service. When the program consumes its entire compute budget or exceeds certain bounds, the runtime halts the currently running instructions and returns an error.
