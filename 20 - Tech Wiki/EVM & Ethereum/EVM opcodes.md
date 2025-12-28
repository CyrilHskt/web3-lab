## Definition

- **Opcode** = *operation code*: a primitive instruction understood directly by the machine (here, the EVM).
- A smart contract’s bytecode is a **sequence of opcodes** (1 byte each) that the EVM reads and executes.
- Each opcode represents an **atomic** action:
  - arithmetic operation (`ADD`, `MUL`)
  - stack manipulation (`PUSH`, `POP`, `DUP`, `SWAP`)
  - memory/storage read-write (`MLOAD`, `MSTORE`, `SLOAD`, `SSTORE`)
  - control flow (`JUMP`, `JUMPI`, `STOP`, `RETURN`, `REVERT`)
  - blockchain interactions (`CALL`, `LOG`, reading `BLOCKNUMBER`, `TIMESTAMP`, etc.).

## Link to Solidity

- The developer writes in **Solidity** (or Vyper, Yul…).
- The code is **compiled to EVM bytecode**, i.e., a sequence of opcodes.
- The EVM only “understands” these opcodes; the high-level language is just a human abstraction.
- Understanding opcodes helps you:
  - precisely analyze a contract’s behavior (security, gas);
  - do auditing, formal verification, or even write EVM assembly by hand.

## Opcodes and gas

- Each opcode has a **gas cost defined by the protocol**.
  - Example: an addition is cheap, a storage write (`SSTORE`) is expensive.
- The **total gas consumed** by a transaction is the sum of the costs of the executed opcodes.
- Optimizing a contract often means reducing expensive opcodes, or replacing a costly sequence with a more compact one.

## Role in contract execution

1. The EVM reads the next opcode pointed to by the **Program Counter**.
2. It **decodes** it to determine which operation to execute.
3. It manipulates the **stack**, memory, storage, or context depending on the opcode.
4. It updates the program counter, remaining gas, and continues until `STOP`, `RETURN`, or `REVERT`.

## Why it matters

- Opcodes are the **lowest-level layer** of contract logic.
- Every Ethereum transaction, ultimately, is just a sequential execution of opcodes.
- For security auditing, deep gas understanding, or bytecode reverse engineering, it’s essential to reason directly in terms of opcodes.
