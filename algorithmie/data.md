---
title: Les données
description: 
published: 1
date: 2022-08-14T07:53:13.626Z
tags: 
editor: markdown
dateCreated: 2022-08-14T07:53:13.626Z
---

# Les variables et les données

## Les Variables

Une variable est un identifiant qui permet de _mémoriser_ des valeurs.

Une variable est définie par :

- **son nom** : un identificateur
- **sa portée** : les portions de code où elle est utilisable
- **son type** : les valeurs qu'elle peut prendre
- **sa classe** d'allocation : indique la zone mémoire où elle est stockée [Chapitre 0](./NotionDeBase.md)
- **sa valeur** initiale

### Les types prédéfinis de variables

Les différents types prédéfinis en langage algorithmique que nous utiliserons sont :

- **ENTIER** nombres entiers signés ex : 42
- **RÉEL** nombres flottants signés ex : 0.154
- **BOOLÉEN** énumération définissant les données vrai et faux ex : vrai
- **CARACTÈRE** caractère ANSI sur un octet ex : ‘a’
- **CHAINE** chaîne de caractères ex : « lapin »

### La déclaration des variables

Déclaration :

- variables simples

```
VARIABLES variable1, variable2, variable3, ... : type
```

<p align="right">(En anglais : VARIABLES)</p>

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

Déclaration des constantes :

```
CONSTANTES MACONSTANTE, ... : type  ...
```

<p align="right">(En anglais : CONSTANTS)</p>

⛔ /!\ Une constante ne peut être modifiée dans l’algorithme.

---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/algorithmie/instructions)