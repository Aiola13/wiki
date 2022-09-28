---
title: Un Pseudo-code
description: 
published: 1
date: 2022-09-28T18:48:28.783Z
tags: 
editor: markdown
dateCreated: 2022-08-14T07:52:08.185Z
---

# Un Pseudo-Code

> Il n'existe aucun **standard** ni de **normalisation** pour l'écriture d'un algorithme en pseudo-code. Mais voici quelques **conventions** et bonnes pratiques 😉.
{.is-warning}

## Structure générale

```
ALGORITHME
    <partie déclarations>
    Début
        <partie instructions>
    Fin
```

## Conventions et règles d'écriture

### Conventions

Nous utiliserons les conventions suivantes :

- __mots clés__
- *identifiants*
- <élément à développer>
- {élément facultatif}
- ... pour indiquer que la structure peut être répétée

### Identifiants

En programmation, un identifiant (ou identificateur) est un mot choisi (par le programmeur), qui peut désigner : 

- une constante
- une variable
- une procédure
- une fonction
- l’algorithme principal


> Les noms d’identifiants ne peuvent contenir que des caractères compris dans les intervalles suivants
{.is-warning}
> - ‘a’..’z’
> - ‘A’..’Z’  
> - ‘0’..’9′
> - On peut également utiliser le caractère \_ (souligné/underscore)
{.is-warning}


> Voici la bible de la construction d'un identifiant (Et oui, il y toujours des règles à respecter 😁) :
> - il ne doit pas commencer par un chiffre.
> - il doit être déclaré avant d'être utilisé
> - il ne doit pas ressembler à un mot-clé existant
> - il doit être explicite

Exemple, un identifiant contenant la largeur d'une image : 
|Bonne pratique|Mauvaise pratique|
|:------------:|:----------------:
|largeur_image|li|
|largeurImage|image|


### Mots-Clés

> Les mots clés sont des mots utilisés pour construire les algorithmes, ils sont préféfinis. 
{.is-warning}

Liste des principaux mots clés du langage :

| ALGORITHME | PROCÉDURE | CONSTANTES | VARIABLES | DÉBUT | FIN | FONCTION | SI | ALORS SINON | POUR | TANT_QUE | JUSQU’À | RÉPÉTER | SELON | BOOLÉEN | ENTIER RÉEL | CARACTÈRE | OU | ET |

### Les symboles spéciaux

Voici la liste des caractères spéciaux utilisés en Pseudo-Code :

← ^ . , : { } [ ] <= >= <> = + – \* / ()`

### Les commentaires

Pour aider à la compréhension, il faut ajouter des commentaires. Les blocs de commentaires seront délimités par les caractères // :

`// un commentaire`


<p align="right">(En anglais : ALGORITHM – BEGIN – END)</p>



---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/algorithmie/data)