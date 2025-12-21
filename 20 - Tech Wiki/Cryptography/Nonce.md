## Rôle du nonce

- Le header d’un nouveau bloc est passé dans une fonction de [[Hash]] (ex. SHA‑256).
- Pour qu’un bloc soit accepté, le hash de son header doit être **inférieur à une valeur cible** (target).
- Comme la fonction de hachage est déterministe, on ajoute un nombre arbitraire, le **nonce**, au header pour pouvoir changer le résultat du hash.

Forme simplifiée :
- `header + nonce₁ -> SHA256 -> hash₁`
- `header + nonce₂ -> SHA256 -> hash₂`
- …
- On cherche un `nonce` tel que `hash_nonce < target`.

## Critère de « hash suffisamment petit »

- En pratique, on demande au hash de **commencer par un certain nombre de zéros** en représentation hexadécimale.
- Plus il y a de zéros initiaux, plus le hash est petit et plus la difficulté est élevée.
- La difficulté peut donc être exprimée en **nombre de bits / nombre de 0** exigés au début du hash.

## Minage = recherche du bon nonce

- La seule méthode réaliste est d’**essayer les nonces un par un** (brute force) jusqu’à obtenir un hash qui respecte la cible.
- Ce processus :
  - consomme des ressources matérielles et énergétiques ;
  - est **difficile à réaliser** (très nombreux essais) ;
  - mais **très facile à vérifier** : il suffit de rehacher le header + nonce proposé.

## Incitation économique

- Le nœud qui trouve un nonce valide peut publier le bloc et reçoit une **récompense en bitcoins nouvellement créés** (plus les frais de transaction).
- Cette récompense est programmée pour **diminuer dans le temps** (halving tous les 4 ans environ).
- Quand un bloc valide est trouvé et diffusé, le réseau l’accepte et **tous les mineurs repartent sur le bloc suivant**, en recommençant la recherche d’un nouveau nonce.
