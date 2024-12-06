---
title: Les données
description: 
published: true
date: 2024-12-06T23:46:58.722Z
tags: data, données, donnée, variables, variable
editor: markdown
dateCreated: 2024-12-06T23:46:58.722Z
---

# Les variables et les données

## Les Variables

> Une variable est un identifiant qui permet de **_mémoriser_** des valeurs.
{.is-success}


> Une variable est définie par :
> 
> - **son nom** : un identificateur
> - **son type** : les valeurs qu'elle peut prendre
> - **sa valeur** : initiale
> - **sa portée** : les portions de code où elle est utilisable
> - **sa classe d'allocation** : indique la zone mémoire où elle est stockée
> 
> ‎
{.is-info}


### Les types prédéfinis de variables

Les différents types prédéfinis en langage algorithmique que nous utiliserons sont :


|Type|Définition|Exemple|
|:--:|:--------:|:-----:|
|**ENTIER**|nombres entiers signés|`42`|
|**RÉEL**|nombres flottants signés|`0.154`|
|**BOOLÉEN**|énumération définissant les données vraies et fausses|`Vrai`|
|**CARACTÈRE**|caractère ANSI codé sur un octet|`‘a’`|
|**CHAINE**|chaîne de caractères|`"lapin"`|


### La déclaration des variables

Déclaration :

- variables simples

```
VARIABLES variable1, variable2, variable3, ... : type
```

- variables indicées ou tableaux

Les tableaux permettent d’associer dans une même variable plusieurs données de même type avec un indice allant de l’indice minimum <entier1> à l’indice maximum <entier2>.

```
VARIABLES tableau[<entier1>,entier2] , ... : type
```

Un tableau peut comporter plusieurs dimensions délimitées par un point virgule :

```
VARIABLES tableau[<entier1.1>,<entier1.2>;<entier2.1>,<entier2.2>] , ... : type
```

Dans ce dernier exemple , il s’agit d’un tableau à 2 dimensions avec un indice pour les lignes (compris entre <entier1.1> et <entier1.2>) et un deuxième indice pour les colonnes (compris entre <entier2.1> et <entier2.2>).

Utilisation : l’accès à un élément d’un tableau se fait en indiquant la liste des indices correspondant à chaque dimension.

```
tableau[<indice1>;<indice2>; ...]
```

## Les constantes
  
> Une constante est un identifiant dont la valeur, qui comme son nom indique, reste constante.
{.is-success}


Déclaration des constantes :

```
CONSTANTES MACONSTANTE, ... : type  ...
```

> ⛔ /!\ Une constante ne peut être modifiée dans l’algorithme.
{.is-danger}
  
---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/algorithmie/instructions)