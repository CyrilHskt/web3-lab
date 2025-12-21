Au sein d'une blockchain [[Proof of Work (POW)]] :
![[Pasted image 20251210213052.png]]
Schématiquement, un bloc est composé de deux parties : son « header » et les transactions incluses dans le bloc. Le header reprend une série de métadonnées (des données à propos définis), à savoir :

- **la version du protocole utilisée**

- **le [[Hash]] du bloc précédent (de son header en fait)**

- **le [[Hash]] de la racine de [[Merkle Tree]] des transactions de ce bloc**

- **un timestamp (la journée et l’horaire de la création de ce bloc)**

- **la cible de difficulté**

- **un [[Nonce]]