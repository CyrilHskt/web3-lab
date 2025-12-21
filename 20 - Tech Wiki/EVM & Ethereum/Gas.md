## Pourquoi le gas existe

- Chaque interaction avec une Dapp / un smart contract exécute des instructions **sur tous les [[Node]] du réseau.
- Pour chaque opération, on paie un coût en **unités de gas**.
- Objectifs principaux :
  - Limiter les abus et attaques (spam, DDoS par transactions massives).
  - Rémunérer les nœuds qui fournissent puissance de calcul et stockage.
  - Donner une utilité économique à l’ETH (il sert à acheter du gas).

## Distinction gas / ether

- **Gas** : unité abstraite qui mesure le **coût en calcul** d’une opération (addition, stockage, appel de fonction, etc.).
  - Chaque type d’instruction a un coût de gas fixe (par ex. `SSTORE` coûte plus cher qu’une simple addition).
- **Ether (ETH)** : monnaie native dont le **prix varie sur le marché**.
- Le coût réel payé = `gas_used × gas_price` (exprimé en ETH ou [[Gwei (Etherium GAS basic unit)]]).

## Marché du gas

- L’expéditeur choisit :
  - une **limite de gas** (`gas limit`) = nombre max d’unités de gas que la transaction peut consommer.
  - un **prix par unité de gas** (`gas price`).
- Les validateurs / producteurs de blocs :
  - peuvent **accepter** ou **refuser** une transaction selon le prix proposé.
  - priorisent les transactions avec un prix de gas plus élevé.

(En pratique, les wallets modernes estiment automatiquement ces paramètres.)

## Règles de consommation du gas

- Si `gas_used ≤ gas_limit` :
  - la transaction est exécutée ;
  - seul le gas effectivement consommé est facturé ;
  - le **gas non utilisé est remboursé** en ETH à l’expéditeur.
- Si `gas_used > gas_limit` :
  - l’exécution s’arrête avec une erreur (revert) ;
  - **tous les changements d’état sont annulés** ;
  - mais le gas dépensé jusqu’à l’erreur est **perdu** (payé au validateur).
- Il est donc conseillé d’envoyer une **limite de gas supérieure à l’estimation** : on ne paie que ce qui est réellement consommé.

![[Pasted image 20251211100543.png]]