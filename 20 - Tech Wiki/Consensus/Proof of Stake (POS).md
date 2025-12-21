Communément appelée proof of stake, celle-ci est finalement plus simple à comprendre que la preuve de travail. Ici, pas besoin de puissance informatique. Si avant on prouvait notre bonne foi en dépense d'énergie, ici on dépense de la valeur: la cryptomonnaie associée à la blockchain. On met en gage un certain montant, contre lequel il nous est potentiellement octroyé le droit de valider des transactions et de les inscrire dans un bloc.

La mise en gage du montant demandé fait office de caution: si les transactions ne sont pas correctement inscrites, si on essaie de les falsifier, alors l’ensemble du réseau le remarquera, et le bloc créé sera annulé, et notre caution sera reprise: on appelle cela le slashing. Cette méthode de consensus ne nécessite donc pas de matériel particulier, ou de dépense d’énergie (ce qui convient bien dans un monde où l'énergie est rare, couteuse, et sa dépense en partie mauvaise pour la planète, elle est donc appréciée aujourd’hui.).

De la même manière que l’on récompense les miners en PoW, on vient aussi récompenser les stakers. Les consensus admettent des particularités selon les blockchains, mais on en arrive souvent à un tirage au sort du stakers qui pourra inscrire le block.

## Deux propriétés cibles d’un [[Consensus]]

(Live intéressant qui explique en détails : https://www.youtube.com/live/6c2NdBMFGqY)

- **Safety (sécurité)**  
  - Tous les nœuds honnêtes doivent produire des blocs cohérents entre eux.  
  - Une transaction valide pour un nœud honnête doit l’être pour tous (consistency).  
  - Deux nœuds honnêtes ne doivent pas aboutir à des historiques incompatibles.

- **Liveness (disponibilité)**  
  - Le consensus ne doit pas s’arrêter tant qu’il existe des transactions valides à inclure.  
  - Les blocs doivent continuer à être produits et finalisés malgré pannes, retards réseau, etc.
## Fonctionnement général d’un PoS

- Des nœuds déposent une **caution (stake)** pour devenir validateurs.
- À intervalles réguliers, un validateur est **tiré au sort** pour proposer un bloc.
- Les autres validateurs vérifient ce bloc et émettent une **attestation** :
  - assez d’attestations → bloc considéré valide ;
  - pas assez → bloc invalidé et le validateur fautif risque de perdre une partie de son stake.
- Problème central : garantir la **liveness** (la chaîne continue à avancer) même en cas de pannes ou de nœuds désynchronisés.
## Casper : finality gadget

Casper ajoute une **finalité déterministe** au-dessus du protocole de base.

### Slot

- Temps discret (par ex. 12 secondes).  
- À chaque slot :
  - un validateur est choisi pour proposer un bloc ;
  - le bloc reçoit les attestations des autres validateurs ;
  - s’il atteint un certain seuil d’attestations, il est considéré comme validé pour ce slot ;
  - sinon, le slot reste vide et on passe au suivant.

### Epoch

- Regroupe un ensemble de slots (ex. 32).  
- À la fin d’une epoch :
  - si une quantité suffisante de validateurs ont attesté l’ensemble des blocs de cette epoch,
  - alors ces blocs deviennent un **checkpoint finalisé** :  
    ils sont considérés comme figés dans l’histoire de la blockchain (irréversibles).

## Liveness et problèmes pratiques

- Si trop peu de validateurs attestent (panne réseau, coupure géographique…), la chaîne peut **cesser de produire des blocs** finalisés.
- Certains nœuds peuvent voir une version plus ancienne de la chaîne et refuser les blocs récents.
- La liveness n’est donc pas triviale : il faut des mécanismes pour continuer à avancer malgré les défauts d’attestation.
## LMD Ghost

LMD Ghost gère le choix de la « bonne » chaîne lorsqu’il existe plusieurs forks.

- Chaque attestation porte sur un bloc ; on choisit la chaîne avec **le plus d’attestations (le plus de stake engagé)**, et non la chaîne la plus longue comme en PoW.
- Le nœud sélectionne la chaîne canonique en partant du dernier checkpoint et en suivant à chaque fois le fils qui cumule le plus d’attestations.
- Propriétés :
  - à tout instant, un nœud sous Ghost a toujours une chaîne courante cohérente avec ce qu’il voit ;
  - s’il est seul dans une partition réseau, il continue à produire des blocs ;
  - lorsqu’il revoit le reste du réseau, il rejoint la version avec le plus d’attestations.

Cette finalité est dite **probabiliste** (comme la chaîne la plus longue en PoW) : il reste un risque de réorganisation, surtout en cas de grosses partitions réseau. C’est pourquoi Casper est utilisé en temps normal (finalité forte), et Ghost plutôt en **mode défaillance** pour garder la chaîne vivante.
