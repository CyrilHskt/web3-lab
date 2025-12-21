## Définition

- Système de numération en **base 16**.
- Utilise 16 symboles : `0 1 2 3 4 5 6 7 8 9 a b c d e f`.
- Correspondance :
  - `a = 10`, `b = 11`, `c = 12`, `d = 13`, `e = 14`, `f = 15`.

## Lien avec le binaire

- 1 caractère hexadécimal = 4 bits en binaire.
  - Exemple :  
    - `0xF` = `1111₂`  
    - `0xA` = `1010₂`
- Avantage : notation beaucoup plus compacte que le binaire pour représenter des valeurs binaires longues (adresses, hashs, clés…).

## Conversion rapide

- Pour convertir un nombre binaire en hexadécimal :
  - Regrouper les bits par paquets de 4 en partant de la droite.
  - Remplacer chaque paquet par le symbole hexa correspondant.
- Exemple :
  - `1101 1010₂` → `0xDA`.

## Hexadécimal et hashs

- Les hashs (SHA‑256, etc.) sont souvent affichés en **hexadécimal** :
  - Plus lisible qu’une suite de bits, tout en restant directement convertible.
  - Permet de voir le hash comme un **grand nombre**.
- Comparaison numérique possible :
  - Exemple : le premier caractère `e` (14) est supérieur à `6` (6), donc un hash commençant par `e` est numériquement plus grand qu’un hash commençant par `6`.

## Usages courants

- Représentation de [[Hash]] (blockchain, signatures, empreintes de fichiers).
- Adresses mémoire, couleurs HTML/CSS (`#RRGGBB`), identifiants divers.
- Format naturel pour manipuler des données binaires au niveau « bas » (réseaux, crypto, systèmes).
