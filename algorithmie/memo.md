---
title: Mémo
description: 
published: true
date: 2024-12-06T23:15:26.510Z
tags: algorithmie, memo
editor: markdown
dateCreated: 2024-12-06T23:15:26.510Z
---

# Définition de l'algorithmie
> L'algorithmie est la science des algorithmes, c'est-à-dire l'étude des méthodes de résolution de problèmes de manière structurée et logique. Un algorithme est une suite finie et ordonnée d'instructions précises permettant de résoudre un problème ou d'effectuer une tâche.
{.is-success}


# Représentation des algorithmes
> Les algorithmes peuvent être représentés de différentes manières :
> 
> - Pseudo-code : une description textuelle proche du langage naturel, facilitant la compréhension et l'écriture.
> - Organigrammes (ou flowcharts) : des diagrammes représentant graphiquement la suite d'instructions et les flux de contrôle.
> - Code : l'algorithme peut être directement traduit dans un langage de programmation (Python, C++, Java, etc.).
> 
> ‎
{.is-success}

# Types d'algorithmes
> Il existe plusieurs types d'algorithmes selon la méthode utilisée :
> 
> - Algorithmes séquentiels : les instructions sont exécutées dans l'ordre où elles sont écrites.
> - Algorithmes conditionnels : les instructions sont choisies selon une condition (si ... alors ... sinon ...).
> - Algorithmes itératifs : certaines instructions sont répétées un certain nombre de fois (boucles).
> - Algorithmes récursifs : l'algorithme s'appelle lui-même pour résoudre un sous-problème similaire.
> 
> ‎
{.is-info}




<!-- # Complexité des algorithmes
La complexité d'un algorithme mesure la quantité de ressources (temps et mémoire) qu'il nécessite pour résoudre un problème. Il existe deux types principaux de complexité :

Complexité temporelle : le temps d'exécution par rapport à la taille de l'entrée.
Complexité spatiale : la quantité de mémoire requise par rapport à la taille de l'entrée.
La notation Big-O est utilisée pour exprimer la complexité en fonction de la taille de l'entrée :

O(1) : Complexité constante.
O(n) : Complexité linéaire.
O(n²) : Complexité quadratique.
O(log n) : Complexité logarithmique.
O(n log n) : Complexité quasi-linéaire.

# Structures de données courantes
Les algorithmes travaillent souvent avec des structures de données. Quelques-unes des structures les plus courantes :

Tableaux (array) : contiennent des éléments de même type, accessibles par leur index.
Listes chaînées (linked list) : chaque élément contient une référence vers l'élément suivant.
Piles (stack) : structure LIFO (Last In, First Out).
Files (queue) : structure FIFO (First In, First Out).
Arbres (tree) : structure hiérarchique avec des nœuds connectés par des arêtes.
Graphes (graph) : ensemble de nœuds reliés par des arêtes, avec ou sans orientation.

# Exemples d'algorithmes célèbres
Tri : Tri à bulles (bubble sort), Tri rapide (quick sort), Tri fusion (merge sort).
Recherche : Recherche linéaire, Recherche dichotomique (ou binaire).
Parcours de graphes : Parcours en largeur (BFS), Parcours en profondeur (DFS).
Algorithmes de plus court chemin : Dijkstra, Bellman-Ford. -->

# Pseudo-code d'exemple : Vérification de la Parité d'un Nombre
Voici un exemple de pseudo-code pour un algorithme qui vérifie si un nombre est pair :

```arduino
Variables :
	nombre : entier
  
Début
    // Lire le nombre
    Lire nombre

    // Vérifier la parité
    Si (nombre % 2 == 0) Alors
        Afficher "Le nombre est pair"
    Sinon
        Afficher "Le nombre est impair"
    FinSi
Fin

```

# Notions de Base
## Variables et Types
> Une variable c’est une sorte de boîte, étiquetée, où l’on peut stocker de l’information pour la consulter ou la modifier plus tard.
{.is-success}

> Une variable est donc une zone de la mémoire de l'ordinateur dans laquelle une valeur est stockée. Cette variable est définie par **un nom**, **un type** et **sa valeur**
{.is-success}

> Pour l'ordinateur, il s'agit en fait d'une adresse, c'est-à-dire d'une zone particulière de la mémoire, où une valeur est stockée.
{.is-info}

![memory2.png](/images/python/memory2.png){.align-center}

![schema_memoire_ram_avec_donnees.jpg](/images/python/schema_memoire_ram_avec_donnees.jpg){.align-center}

<center>

| Type               | Exemple                     |
|--------------------|-----------------------------|
| Entier       			 | `42`, `-7`                  |
| Flottant (Réel)    | `3.14`, `-0.001`            |
| Chaîne (Caractères)| `"Bonjour"`, `"Algorithmie"`|
| Booléen (bool)     | `Vrai`, `Faux`              |

</center>

## Opérations

### Les opérateurs arithmétiques

<center>
  
| Signe |               Opération               |Exemple|
| :---: | :-----------------------------------: |:-----:|
|  `+`  |               Addition                |`2 + 3`|
|  `-`  |             Soustraction              |`2 - 3`|
|  `*`  |            Multiplication             |`2 * 3`|
|  `/`  |               Division                |`2 / 3`|
|  `%`  | Modulo (reste de la division entière) |`2 % 3`|
  
</center>

### Les opérateurs de comparaisons

<center>
  
| Signe |          Opération           |Exemple|
| :---: | :--------------------------: |:-----:|
| `==`  |           Egalité            |`a == b`|
| `!=`  |          Différent           |`a != b`|
|  `<`  |    Strictement Inférieur     |`a < b`|
| `<=`  |      Inférieur ou égal       |`a <= b`|
|  `>`  |    Strictement Supérieur     |`a > b`|
| `>=`  |      Supérieur ou égal       |`a >= b`|
  
</center>

### Les opérateurs logiques

<center>
  
|   Signe    |      Opération      |Exemple|
| :--------: | :-----------------: |:-----:|
| `ET` |     ET logique      | `a == b ET b == c`|
| `OU`  |     OU logique      |`a == b OU b == c`|
  
</center>

# Les Structures Algorithmiques
Il existe trois structures fondamentales utilisées pour construire un algorithme :

## Séquence : exécution d'instructions les unes après les autres.

```arduino
Lire A
Lire B
C ← A + B
Afficher C
```

## Condition (ou sélection) : choix entre plusieurs alternatives.

```arduino
Si (A > B) Alors
    Afficher "A est plus grand"
Sinon Si (A < B) Alors
		Afficher "B est plus grand"
Sinon
    Afficher "B est égal à A"
Fin Si
```

## Boucle (ou répétition) : exécution répétée d’instructions.

```arduino
Tant que (i ≤ 10) faire
    Afficher i
    i ← i + 1
Fin Tant que
```