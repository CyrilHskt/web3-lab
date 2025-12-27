## Definition

- **Gwei** is a denomination of ether (ETH).
- 1 gwei = 0.000000001 ETH = 10⁻⁹ ETH.
- 1 ETH = 1,000,000,000 gwei.
- The name comes from “giga-wei” (one billion wei) and from Wei Dai, the cryptographer behind B-Money.

## Role of gwei

- Gwei is mainly used to express the **gas price**:
  - instead of saying “gas costs 0.00000002 ETH”, you say “20 gwei”.
- The higher the **gas price in gwei**:
  - the more attractive your transaction is to validators;
  - the more likely it is to be included quickly in a block.

## Fee calculation

- Transaction fee (in ETH) = `gas_used × gas_price`.
  - `gas_used` = the amount of gas actually consumed.
  - `gas_price` = the gas price, generally expressed in gwei.
- Example:  
  - `gas_used = 21,000`, `gas_price = 20 gwei`.  
  - Cost = 21,000 × 20 gwei = 420,000 gwei = 0.00042 ETH.

Note: in practice today, the most commonly used units are wei, gwei, and ether.![[Pasted image 20251211100734.png]]