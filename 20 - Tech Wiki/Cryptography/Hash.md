## Qu’est-ce qu’un hash ?

- Une fonction de hachage prend une donnée en entrée (de taille quelconque) et renvoie une donnée de taille fixe.
- En blockchain, on utilise massivement les hashs, par exemple avec SHA‑256 pour transformer un message en une empreinte de 256 bits.

> Exemple : appliquer SHA‑256 à une chaîne comme `alyra` produit un hash hexadécimal (une longue suite de caractères 0‑9 et a‑f).

## Propriétés importantes des fonctions de hachage

- **Sens unique (pré‑image)**  
  - À partir du hash, il est pratiquement impossible de retrouver l’entrée.  
  - Connaître l’empreinte ne permet pas de remonter aux données d’origine dans un temps raisonnable.

- **Effet avalanche**  
  - Une très petite modification de l’entrée (par exemple `alyra` → `alyra0`) change complètement le hash.  
  - Les deux empreintes n’ont aucun lien visible : on ne peut pas les « rapprocher » en regardant les valeurs.

- **Résistance aux collisions**  
  - Il est considéré comme impossible (en pratique) de trouver deux entrées différentes qui produisent exactement le même hash.  
  - Cette propriété est cruciale pour l’intégrité des données (transactions, blocs…).

## Représentation en [[Hexadecimal (16)]]

- Les hashs sont souvent affichés en **hexadécimal** (base 16) : chiffres `0‑9` et lettres `a‑f` pour les valeurs 10 à 15.
- C’est une notation compacte, adaptée au monde informatique : chaque caractère hexa représente 4 bits.
- Un hash peut donc être vu comme un **grand nombre** ; on peut les comparer numériquement (par exemple comparer le premier caractère hexa `e` > `6`).

## Utilisation en blockchain

- Les hashs servent à :
  - Chaîner les [[Block]] (chaque bloc contient le hash du bloc précédent).  
  - Vérifier l’intégrité des transactions ou des entêtes.  
  - Construire des structures comme les [[Merkle Tree]].
- Dans un header de bloc, plusieurs hashs distincts sont souvent utilisés (par exemple hash des transactions + hash du header lui‑même).
