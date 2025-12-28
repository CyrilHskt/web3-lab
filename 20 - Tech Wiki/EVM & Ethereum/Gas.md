## Why gas exists

- Each interaction with a Dapp / a smart contract executes instructions **on every [[Node]] in the network**.
- For each operation, you pay a cost in **gas units**.
- Main goals:
  - Limit abuse and attacks (spam, DDoS via massive transaction submission).
  - Compensate nodes that provide compute power and storage.
  - Give ETH an economic utility (it is used to buy gas).

## Gas vs ether

- **Gas**: an abstract unit that measures the **computational cost** of an operation (addition, storage, function call, etc.).
  - Each instruction type has a fixed gas cost (e.g. `SSTORE` costs more than a simple addition).
- **Ether (ETH)**: the native currency whose **price fluctuates on the market**.
- The actual amount paid = `gas_used × gas_price` (expressed in ETH or [[Gwei (Etherium GAS basic unit)]]).

## The gas market

- The sender chooses:
  - a **gas limit** (`gas limit`) = the maximum number of gas units the transaction can consume.
  - a **price per unit of gas** (`gas price`).
- Validators / block producers:
  - can **accept** or **reject** a transaction depending on the offered price.
  - prioritize transactions with a higher gas price.

(In practice, modern wallets estimate these parameters automatically.)

## Gas consumption rules

- If `gas_used ≤ gas_limit`:
  - the transaction is executed;
  - only the gas actually consumed is charged;
  - **unused gas is refunded** in ETH to the sender.
- If `gas_used > gas_limit`:
  - execution stops with an error (revert);
  - **all state changes are rolled back**;
  - but the gas spent up to the error is **lost** (paid to the validator).
- It is therefore recommended to set a **gas limit above the estimate**: you only pay for what is actually consumed.

![[Pasted image 20251211100543.png]]