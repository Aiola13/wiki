---
title: Un Pseudo-code
description: 
published: 1
date: 2022-08-14T07:52:08.185Z
tags: 
editor: markdown
dateCreated: 2022-08-14T07:52:08.185Z
---

# Un Pseudo-Code

Remarques :

- il n’y a pas de standard (et donc pas de normalisation) pour l’écriture d’un algorithme en pseudo-code mais seulement quelques conventions partagées par un grand nombre !
- pour chaque mot clé, nous donnerons son équivalent en anglais.

## Structure générale

Voici la structure générale d’un algorithme :

```
ALGORITHME
    <partie déclarations>
    Début
        <partie instructions>
    Fin
```

<p align="right">(En anglais : ALGORITHM – BEGIN – END)</p>

## Conventions et règles d'écriture

### Conventions

Nous utiliserons les conventions suivantes :

- _mots clés_
- _identifiants_
- <élément à développer>
- {élément facultatif}
- ... pour indiquer que la structure peut être répétée

### Identifiants

Un identifiant (ou identificateur) est un nom déclaré et valide pour :

- une constante [Chapitre 0](./NotionDeBase.md)
- une variable [Chapitre 0](./NotionDeBase.md)
- une procédure
- une fonction
- l’algorithme principal
- Les noms d’identifiants ne peuvent contenir que des caractères compris dans les intervalles suivants :
  - ‘a’..’z’
  - ‘A’..’Z’
  - ‘0’..’9′
  - On peut également utiliser le caractère \_ (souligné/underscore)

Pour construire un identifiant, il faudra respecter les règles suivantes :

- il ne peut en aucun cas commencer par un chiffre
- tout identifiant doit avoir été déclaré avant d’être utilisé
- un identifiant doit bien entendu être différent d’un mot clé, ceci pour éviter toute ambiguïté
- enfin, pour faciliter l’écriture et la lecture des algorithmes, il est très fortement conseillé d’utiliser des identifiants explicites (par exemple : largeur_image ou largeurImage et non li)

### Mots-Clés

- Les mots clés seront utilisés pour construire les algorithmes, les déclarations et les instructions.
- Ceux-ci sont prédéfinis dans le langage. Comme pour les identifiants, aucune distinction n’est faite entre les majuscules et les minuscules.

Liste des principaux mots clés du langage :

| ALGORITHME | PROCÉDURE | CONSTANTES | VARIABLES | DÉBUT | FIN | FONCTION | SI | ALORS SINON | POUR | TANT_QUE | JUSQU’À | RÉPÉTER | SELON | BOOLÉEN | ENTIER RÉEL | CARACTÈRE | OU | ET |

### Les symboles spéciaux

Voici la liste des caractères spéciaux utilisés en Pseudo-Code :

← ^ . , : { } [ ] <= >= <> = + – \* / ()`

### Les commentaires

Pour aider à la compréhension, il faut ajouter des commentaires. Les blocs de commentaires seront délimités par les caractères // :

`// un commentaire`

---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/algorithmie/data)