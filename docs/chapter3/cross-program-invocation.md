---
hide:
  - toc
---

A **Cross Program Invocation (CPI)** is a mechanism that allows Solana programs to call other programs from within an instruction. The caller is halted until execution returns from the callee.

Programs can extend their signer privileges to other programs using CPIs. CPIs are executed by calling either **invoke** or **invoke_signed** methods within their instructions:

- **invoke** - All necessary signatures are already available before the call.
- **invoke_signed** - Calling program needs PDAs to act as signers during the CPI.

!!! info

    After a CPI to another program is made, the callee program can make further CPIs to other programs. The **maximum CPI depth is 4**.

CPIs are a very powerful feature as they allow developers to make use of other deployed programs and continuously build on and expand the Solana's already existing ecosystem.
