## Définition

- **Opcode** = *operation code* : instruction primitive comprise directement par la machine (ici, l’EVM).
- Le bytecode d’un smart contract est une **suite d’opcodes** (1 octet chacun) que l’EVM lit et exécute.
- Chaque opcode représente une action **atomique** :
  - opération arithmétique (`ADD`, `MUL`, …)
  - gestion de la pile (`PUSH`, `POP`, `DUP`, `SWAP`)
  - lecture/écriture en mémoire ou stockage (`MLOAD`, `MSTORE`, `SLOAD`, `SSTORE`)
  - contrôle de flux (`JUMP`, `JUMPI`, `STOP`, `RETURN`, `REVERT`)
  - interactions blockchain (`CALL`, `LOG`, lecture du `BLOCKNUMBER`, `TIMESTAMP`, etc.).

## Lien avec Solidity

- Le développeur écrit en **Solidity** (ou Vyper, Yul…).
- Le code est **compilé en bytecode EVM**, donc en séquence d’opcodes.
- L’EVM ne « comprend » que ces opcodes ; le langage haut niveau n’est qu’une abstraction humaine.
- Comprendre les opcodes permet :
  - d’analyser précisément le comportement d’un contrat (sécurité, gas) ;
  - de faire de l’audit, de la vérification formelle, voire d’écrire de l’assembly EVM à la main.

## Opcodes et gas

- Chaque opcode a un **coût en gas fixé par le protocole**.
  - Exemple : une addition coûte peu, un accès au stockage (`SSTORE`) coûte beaucoup.
- Le **gas total consommé** par une transaction est la somme des coûts des opcodes exécutés.
- Optimiser un contrat = souvent réduire le nombre d’opcodes chers, ou remplacer une séquence coûteuse par une séquence plus compacte.

## Rôle dans l’exécution d’un contrat

1. L’EVM lit le prochain opcode pointé par le **Program Counter**.
2. Il le **décode** pour savoir quelle opération exécuter.
3. Il manipule la **pile**, la mémoire, le stockage ou le contexte selon l’opcode.
4. Il met à jour le compteur de programme, le gas restant, et continue jusqu’à `STOP`, `RETURN` ou `REVERT`.

## Pourquoi c’est important

- Les opcodes sont la **couche la plus basse** de la logique des contrats.
- Toute transaction Ethereum n’est, en dernière analyse, qu’une exécution séquentielle d’opcodes.
- Pour l’audit de sécurité, la compréhension fine du gas, ou le reverse‑engineering de bytecode, il est indispensable de raisonner directement en termes d’opcodes.
-