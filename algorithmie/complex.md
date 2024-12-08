---
title: La compléxité d'un algorithme
description: 
published: true
date: 2024-12-08T10:22:38.628Z
tags: complex, complexité
editor: markdown
dateCreated: 2024-12-08T10:22:38.628Z
---

# Introduction à la Complexité d'un algorithme

> Voici une petite introduction (informelle) à la joie du calcul de la complexité algorithmique.
> 
> Le calcul de la complexité d'un algorithme permet de meurer sa **performance**. Il en existe deux types :
>   - complexité spatiale
>   - complexité temporelle
> 
> ‎
{.is-success}


> La complexité temporelle d'un algorithme est une mesure du temps (nombre d'étapes) requis par l'algorithme pour accomplir sa tâche (arriver à la solution), en fonction de la taille (nombre d'éléments) de l'échantillon à traiter.
{.is-success}


> La complexité spatialle d'un algorithme  mesure l'espace mémoire nécessaire (stockage de variable, structure de données, les appels de fonction...) pour exécuter l'algorithme en fonction de la taille de l'entrée, incluant les variables, structures de données temporaires et appels de fonction, exprimée en notation asymptotique.
{.is-success}



## Calculer la complexité temporelle d'un algorithme

> Cela peut sembler évident a posteriori, mais voilà : pour calculer la complexité d'un algorithme donné, il convient tout d'abord de compter le nombre d'opérations élémentaires impliquées par son exécution.
> 
> Puisqu'il s'agit seulement de comparer des algorithmes, les règles de ce calcul doivent être indépendantes : 
> - du langage de programmation utilisé
> - du processuer de lordinateur sur lequel sera exécuté le code
> - de l'éventuel compulateur employé
> 
> ‎
{.is-success}



> Par soucis de simplicité, on fera l’hypothèse que toutes les opérations élémentaires sont à égalité de coût, soit 1 « unité » de temps.
> 
> Exemple : `a = b * 3`  : 1 multiplication + 1 affectation = 2 « unités »
{.is-warning}


> La complexité en temps d’un algorithme sera exprimé par une fonction, notée T (pour Time) ou C (pou complexité), qui dépend :
> - de la taille des données passées en paramètres : plus ces données seront volumineuses, plus il faudra d’opérations élémentaires pour les traiter.
> On notera n le nombre de données à traiter.
> 
> - de la donnée en elle même, de la façon dont sont réparties les différentes valeurs qui la constituent.
> par exemple, une recherche dans un tableau où la recherche peut s'arréter dès la première itération si la valeur est trouvée.
> 
> ‎
{.is-info}


> Cette remarque nous conduit à préciser un peu notre définition de la complexité en temps. En toute rigueur, on peut en effet distinguer deux formes de complexité en temps :
> - la complexité dans le meilleur des cas : c’est la situation la plus favorable,
> par exemple : recherche d’un élément situé à la première position d’un tableau.
> - la complexité dans le pire des cas : c’est la situation la plus défavorable,
> par exemple : recherche d’un élément dans une liste alors qu’il n’y figure pas
> On calculera le plus souvent la complexité dans le pire des cas, car elle est la plus pertinente. Il vaut mieux en effet toujours envisager le pire.
> 
> ‎
{.is-info}



###  Ordre de grandeur : **$O$**

> La notation la plus utilisée pour noter la complexité d'un algorithme est la notation $O$ (pour ordre de...), qui dénote un ordre de grandeur. Par exemple, on dira d'un algorithme qu'il est $O(15)$ s'il nécessite au plus 15 opérations (dans le pire cas) pour se compléter. En français, on dira qu'il est $O$ de 15 ou encore de l'ordre de 15.
> 
> Souvent, comme dans le cas où un algorithme manipule un tableau de n éléments (on dira un tableau de taille n), la complexité sera notée en fonction de cette taille. Par exemple, un algorithme de complexité O(2n+8) prendra dans le pire cas huit opérations, plus deux opérations supplémentaires par élément du tableau.
> 
> La notation $O$ a le mérite de simplifier très facilement. Nous verrons comment y arriver sous peu.
> 
{.is-success}


#### Un peu de Mathématique ?

Pour comparere des algorithmes, il n'est pas nécessaire d'utiliser la fonction $T$, mais seulement l'ordre de grandeur asymptotique noté $O$.

Une fonction $T(n)$ est en $O(f(n))$ (en grand O de f(n)) si : 
$∃n_0 ∈ N,∃c ∈ R, ∀n ≥ n_0 : |T(n)| ≤ c|f(n)|$

autrement dit : 

$T(n)$ est en $O(f(n))$ s'il exxiste un seuil $n_0$ à partir duquel la fonction $T$ est toujours dominée par la fonction $f$, ç une constant multiplicative fixée $c$ près.

Exemples :

- $T1(n)=7=O(1)$
- $T2(n)=12n+5=O(n)$
- $T3(n)=4n2+2n+6=O(n2)$
- $T4(n)=2+(n−1)×5=O(n)$


### Classes de complexité

|       $O$       | Type de complexité |
| :-------------: | :----------------: |
|     $O(1)$      |     Constante      |
|   $O(log(n))$   |   Logarithmique    |
|     $O(√n)$     |      Racinaire     |
|     $O(n)$      |     Linéaire       |
| $O(n * log(n))$ |   Quasi-linéaire   |
|    $O(n^2)$     |    Quadratique     |
|    $O(n^3)$     |      Cubique       |
|    $O(n^k)$     |    Polynomiale     |
|    $O(a^n)$     |   Exponentielle    |
|     $O(n!)$     |    Factorielle     |



### Algorithmes de complexité constante

Algorithmes de complexité constante
Commençons par un exemple simple, soit celui d'une fonction prenant en paramètre le rayon d'une sphère, calculant le volume de cette sphère, et retournant cette valeur au sous-programme appelant. On aura le code proposé à droite.

L'instruction notée (0) est l'affectation d'une valeur à une constante. On peut compter celle-ci comme étant une opération (certains l'omettront, ce qui importe peu, comme nous le verrons plus bas).

L'instruction notée (1) est composée de cinq opérations arithmétiques et d'une affectation. On peut la compter comme six opérations ou comme une seule (ce qui importe peu aussi).

L'instruction notée (2), la production de la valeur résultante de l'exécution de la fonction, est aussi une opération.

```
Fonction volumeSphere(rayon : réel)
CONSTANTE PI
PI 3.14159 (0)
variable volume : réel

DEBUT
   volume = 4.0 / 3.0 * PI * rayon * rayon * rayon // (1)
   RETOURNE volume; // (2)
FIN

```

<!--
```
Fonction renvoieMax(tableau[], tailleTableau : entier) : réels
    variables compteur, noteMax : entiers
    
    compteur ← 0                              1
    noteMax ← tableau[0]                       1

    POUR compteur <- 0 à compteur < tailleTableau par pas de 1                  3n
        SI noteMax < tableau[compteur] ALORS                                    3n
            noteMax ← tableau[compteur]                                         3n
        FSI
    FPOUR

    RETOURNE noteMax                                                            1
```
-->
<!-- 9n +3 -->
Si on additionne tout ça, on arrive à deux opérations, si on ne compte pas l'affectation d'une valeur à la constante – opération (0) – et si on compte l'instruction (1) comme une seule opération, et à huit opérations si on compte les instructions de manière plus rigide. L'algorithme sera donc O(2) ou O(8), tout dépendant de la manière de compter les opérations.

L'important ici n'est pas la valeur exacte entre les parenthèses suivant le O, mais le fait que cette valeur soit constante.

Lorsqu'un algorithme est O(c) où c est une constante, on dit qu'il s'agit alors d'un algorithme en temps constant.
Une complexité constante est la complexité algorithmique idéale, puisque peu importe la taille de l'échantillon à traiter, l'algorithme prendra toujours un nombre fixé à l'avance d'opérations pour réaliser sa tâche.

Tous les algorithmes en temps constant font partie d'une classe nommée O(1). En général, qu'un algorithme soit O(3), O(17) ou O(100000), on dira de lui qu'il est en fait O(1) puisque la différence de performance entre deux algorithmes en temps constant peut être comblée par un simple remplacement matériel (utiliser un processeur plus rapide, par exemple).



## Algorithmes de complexité linéaire

Nous avons déjà vu un algorithme de complexité linéaire un peu plus haut.

-	Par complexité linéaire, ou O(n), on dénotera des algorithmes pour lesquels le nombre d'étapes à effectuer variera en proportion directe de la taille de l'échantillon à traiter : si l'échantillon croît par un facteur de 100, la complexité sera accrue elle aussi par un facteur de 100.

Pensez à un algorithme qui fait la somme des éléments d'un tableau (ici O(3+n×5))... 



```
Fonction somme_elements(tableau[] : tableau d'entiers) : entier
    Variables somme, compteur, N : entiers

    somme ← 0                 // Initialise la somme à 0
    N ← longueur(tableau)     // Obtient la taille du tableau

    POUR compteur ← 0 à compteur < N par pas de 1
        somme ← somme + tableau[compteur]   // Ajoute l'élément courant à la somme
    FPOUR

    RETOURNE somme

Fin Fonction

```

La simplification normale s'applique : on élimine l'addition de constantes, puis la multiplication par des constantes, pour réaliser que la croissance de la complexité dépend directement de la taille de l'échantillon. Il s'agit de la donnée intéressante du calcul.






















<!--

### Algorithmes de complexité logarithmique

Non, nous ne calculerons pas de logarithmes ici. N'empêche : la classe de complexité suivante est celle des algorithmes à complexité logarithmique.

Souvent, les algorithmes de ce genre auront la propriété suivante: on leur donne un échantillon de taille n à traiter, et ils font en sorte (dans une répétitive) de diminuer (de moitié, par exemple) à chaque itération[4] la partie de l'échantillon qu'il vaut la peine de traiter. On peut penser, à tout hasard, à une recherche dichotomique.

Exemple de recherche dichotomique

Supposons qu'on nous donne un tableau d'entiers triés (en ordre croissant, pour simplifier). Le fait que le tableau soit trié est important dans ce cas – l'algorithme n'a pas de sens sinon.

```
Constante INDICE_INVALIDE = -1

Fonction trouver_indice(tableau[], val : entier) : entier
    Variables N, i : entiers

    N ← longueur(tableau)   // Obtient la taille du tableau
    POUR i ← 0 à i < N par pas de 1
        SI tableau[i] = val ALORS
            RETOURNE i
        FSI
    FPOUR

    RETOURNE INDICE_INVALIDE

Début du programme principal
    Variables tab[] : tableau d'entiers

    tab ← [3, 4, 6, 8, 17, 22, 199, 201, 202]   // Tableau trié en ordre croissant

    Afficher "L'élément de valeur 4 se trouve à l'indice "
    Afficher trouver_indice(tab, 4)
Fin du programme principal
```
Supposons qu'on nous demande à quelle position de ce tableau se trouve un élément d'une valeur bien précise, et que le rôle de notre algorithme soit de retourner l'indice où se trouve ladite valeur – ou de retourner un indicateur d'erreur quelconque si l'élément ne s'y trouve pas.

Pour l'exécution d'un programme comme celui ci-dessus, on pourrait s'attendre à l'affichage suivant :

```
L'élément de valeur 4 se trouve à l'indice 1
```

...du fait que la valeur 4 constitue le deuxième élément du tableau tab[], et se trouve conséquemment à la position 1 dans ce tableau.




## Tableau multidimentiennelle / Matrice
```

-->