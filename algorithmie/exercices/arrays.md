---
title: Exercice : Les tableaux | listes
description: 
published: true
date: 2024-12-08T10:25:14.454Z
tags: 
editor: markdown
dateCreated: 2024-12-08T10:25:14.454Z
---

# Exercice 5.1
Écrire un algorithme qui déclare et remplisse un tableau de 7 valeurs numériques en les mettant toutes à zéro.

# Exercice 5.2
Écrire un algorithme qui déclare et remplisse un tableau contenant les six voyelles de l’alphabet latin.

# Exercice 5.3
Écrire un algorithme qui déclare un tableau de 9 notes, dont on fait ensuite saisir les valeurs par l’utilisateur.

# Exercice 5.4
Que produit l’algorithme suivant ?

```
Variables : Tableau Nb[5]: Entier
						i: Entier
Début
Pour i ← 0 à 5
	Nb[i] ← i * i
FinPour
Pour i ← 0 à 5
	Afficher(Nb[i])
FinPour
Fin
```

Peut-on simplifier cet algorithme avec le même résultat ?


# Exercice 5.5
Que produit l’algorithme suivant ?

```
Variables : Tableau N[6]: Entier
						i, k: Entier
Début
N[0] ← 1
Pour k ← 1 à 6
	N[k] ← N[k-1] + 2
FinPour
Pour i ← 0 à 6
	Afficher(N[i])
FinPour
Fin
```

Peut-on simplifier cet algorithme avec le même résultat ?

# Exercice 5.6
Que produit l’algorithme suivant ?

```
Variables : Tableau Suite[7]: Entier
						i: Entier
Début
Suite[0] ← 1
Suite[1] ← 1
Pour i ← 2 à 7
	Suite[i] ← Suite[i-1] + Suite[i-2]
FinPour
Pour i ← 0 à 7
	Afficher(Suite[i])
FinPour
Fin
```

# Exercice 5.7
Écrivez la fin de l’algorithme 6.3 afin que le calcul de la moyenne des notes soit effectué et affiché à l’écran.


# Exercice 5.8
Écrivez un algorithme permettant à l’utilisateur de saisir un nombre quelconque de valeurs, qui devront être stockées dans un tableau. L’utilisateur doit donc commencer par entrer le nombre de valeurs qu’il compte saisir. Il effectuera ensuite cette saisie. Enfin, une fois la saisie terminée, le programme affichera le nombre de valeurs négatives et le nombre de valeurs positives.

# Exercice 5.9
Écrivez un algorithme calculant la somme des valeurs d’un tableau (on suppose que le tableau a été préalablement saisi).

# Exercice 5.10
Écrivez un algorithme constituant un tableau, à partir de deux tableaux de même longueur préalablement saisis. Le nouveau tableau sera la somme des éléments des deux tableaux de départ.


# Exercice 5.10
Écrivez un algorithme constituant un tableau, à partir de deux tableaux de même longueur préalablement saisis. Le nouveau tableau sera la somme des éléments des deux tableaux de départ.

![image.png](/images/python/exercices/image.png)

# Exercice 5.11
Toujours à partir de deux tableaux précédemment saisis, écrivez un algorithme qui calcule le schtroumpf des deux tableaux. Pour calculer le schtroumpf, il faut multiplier chaque élément du tableau 1 par chaque élément du tableau 2, et additionner le tout. Par exemple si l'on a :

![image2.png](/images/python/exercices/image2.png)

Le Schtroumpf sera :
3 * 4 + 3 * 8 + 3 * 7 + 3 * 12 + 6 * 4 + 6 * 8 + 6 * 7 + 6 * 12 = 279

# Exercice 5.12
Écrivez un algorithme qui permette la saisie d’un nombre quelconque de valeurs, sur le principe de l’ex 6.8. Toutes les valeurs doivent être ensuite augmentées de 1, et le nouveau tableau sera affiché à l’écran.

# Exercice 5.13
Écrivez un algorithme permettant, toujours sur le même principe, à l’utilisateur de saisir un nombre déterminé de valeurs. Le programme, une fois la saisie terminée, renvoie la plus grande valeur en précisant quelle position elle occupe dans le tableau. On prendra soin d’effectuer la saisie dans un premier temps, et la recherche de la plus grande valeur du tableau dans un second temps.

# Exercice 5.14
Toujours et encore sur le même principe, écrivez un algorithme permettant à l’utilisateur de saisir les notes d'une classe. Le programme, une fois la saisie terminée, renvoie le nombre de ces notes supérieures à la moyenne de la classe.
