## Definition

An **UTXO** (Unspent Transaction Output) represents the amount of cryptocurrency available after a transaction that can be used in subsequent transactions. Think of it as discrete units of value—you must spend them entirely; you cannot use only a portion of a single UTXO.

## Conceptual Foundation

**UTXO Model (Bitcoin, Cardano)** = Physical Currency
- Discrete, indivisible units
- Must be consumed entirely in a transaction
- Outputs become new, independent units

**Account Model (Ethereum)** = Bank Account
- Single balance per address
- Can transfer any amount
- Balance updates atomically on-chain

## Transaction Structure

Every UTXO-based transaction consists of two components:

**Inputs**
- References to previously unspent outputs you control
- Cryptographic proof of ownership via private key signature
- Once referenced, the previous UTXO becomes permanently spent

**Outputs**
- New UTXO units created from the transaction
- Each specifies recipient and amount
- Locked by recipient's public key or script condition
- Become available for future transactions

## Practical Example

```
Alice controls: 5 BTC (single UTXO)
Alice sends: 2 BTC to Bob

Transaction Structure:
  Input:  Reference to 5 BTC UTXO (signed with Alice's private key)
  Outputs:
    → 2 BTC to Bob's address (new UTXO)
    → 2.99 BTC to Alice's address (change/return value)
    → 0.01 BTC to miner (transaction fee)

Result:
  - Original 5 BTC UTXO: marked as spent (irreversible)
  - New UTXO available: 2.99 BTC (Alice's change)
  - New UTXO available: 2 BTC (Bob's received amount)
```

## Fundamental Properties

### 1. Atomicity of Consumption
- A UTXO must be spent in its entirety within a single transaction
- Partial spending is cryptographically impossible
- Excess value returns as "change" to the sender

### 2. Non-Reusability (Single Spend Rule)
- Each UTXO can be consumed exactly once
- Double-spending is prevented by consensus rules
- Once a UTXO is referenced in a confirmed transaction, it becomes permanently invalid for future transactions

### 3. Output Generation
- Every transaction creates one or more new UTXOs
- The sum of output values equals input value minus transaction fees
- This creates a continuous chain: previous UTXO → consumed → new UTXOs created

## Balance Calculation

Unlike account-based systems where balance is stored on-chain, UTXO-based blockchains calculate balance client-side:

```
Wallet Balance = Sum of all unspent outputs controlled by the wallet's private key
```

The wallet achieves this by:
1. Scanning blockchain history for all transactions paying to your addresses
2. Identifying unspent outputs (inputs not yet consumed)
3. Summing their values

**Example:**
If your wallet controls these UTXOs:
- 0.138 BTC
- 0.1 BTC  
- 0.004 BTC
- 0.73 BTC
- 0.028 BTC

**Total Balance = 1 BTC**