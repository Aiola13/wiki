---
title: Les fonctions
description: 
published: true
date: 2024-12-11T08:27:38.856Z
tags: function, functions, fonction, fonctions
editor: markdown
dateCreated: 2024-12-11T08:27:38.856Z
---

# Définition

> Donner un nom à un ensemble d’instructions pour créer de la modularité et de la sémantique
{.is-success}


> Imaginez une fonction comme une petite usine qui fait une tâche spécifique pour vous. Vous lui donnez quelque chose (les "arguments"), elle travaille dessus, et puis elle vous donne quelque chose en retour (le "résultat" ou "return value").
{.is-info}


> Par exemple, si nous avons une fonction qui s'appelle ajouter_deux_nombres, vous lui donnez deux nombres, elle les ajoute, et elle vous donne le résultat.
{.is-info}


# Syntaxe

```python
def ma_fonction(arg1, arg2):
    instruction1
    instruction2
    ...
    return resultat
```

![fonction.png](/images/python/fonction.png){.align-center}

On peut ensuite utiliser la fonction avec les arguments souhaitées et récupérer le resultat :

```python
mon_resultat = ma_fonction("pikachu", "bulbizarre")
autre_resultat = ma_fonction("salameche", "roucoups")
```

# Exemples

## Calculs mathématiques
```python
sqrt(2)        -> 1.41421 (environ)
cos(3.1415)    -> -1 (environ)
```

## Générer ou aller chercher des données

```python
nom_du_departement(67)        -> "Bas-rhin"
temperature_actuelle("Lyon")  -> Va chercher une info sur internet et renvoie 12.5
```

## Convertir, formatter, filtrer, trier des données …

```python
int("3.14")                     -> 3
normalize_url("toto.com/pwet/") -> https://toto.com/pwet
sorted(liste_de_prenoms)     -> renvoie la liste triée alphabétiquement
```

## **Afficher / demander des données **

```python
print("un message")
input("donne moi un chiffre entre 1 et 10 ?")
```

# Exemple concret

```python
def aire_triangle(base, hauteur):
    return base * hauteur / 2

A1 = aire_triangle(3, 5)      # -> A1 vaut 15 !
A2 = aire_triangle(4, 2)      # -> A2 vaut 8 !
```

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    return 3.1415 * rayon_carree

A3 = aire_disque(6)           # -> A3 vaut (environ) 113 !
```

```python
def aire_triangle(base, hauteur):
    return base * hauteur / 2

A1 = aire_triangle(3, 5)      # -> A1 vaut 7.5 !
A2 = aire_triangle(4, 2)      # -> A2 vaut 8 !
```

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    return 3.1415 * rayon_carree

A3 = aire_disque(6)           # -> A3 vaut (environ) 113
```

```python
def volume_cylindre(rayon, hauteur):
    return hauteur * aire_disque(rayon)

V1 = volume_cylindre(6, 4)   # -> A4 vaut (environ) 452
```


# Comment écrire une fonction

## Définition de la fonction

> Vous commencez par définir votre fonction avec le mot-clé **def**, suivi du nom de la fonction et des parenthèses qui peuvent contenir des arguments.
{.is-success}


```python
def ajouter_deux_nombres(nombre1, nombre2):
```

## Corps de la fonction

> Ensuite, vous écrivez le corps de la fonction : ce qu'elle doit faire avec ces arguments. Ici, nous voulons ajouter deux nombres.
{.is-success}


```python
    resultat = nombre1 + nombre2
    return resultat
```

## Utilisation de la fonction

> Après avoir défini la fonction, vous pouvez l'utiliser autant de fois que vous le souhaitez en l'appelant par son nom et en lui passant des arguments.
> 
{.is-success}

```python
somme = ajouter_deux_nombres(3, 4)
print(somme)  # Cela va afficher 7
```

# Éléments de syntaxe

## Les arguments

> Un argument est une donnée que vous passez à la fonction afin qu'elle puisse l'utiliser. Lorsque vous créez une fonction, vous définissez ce dont elle a besoin pour fonctionner en spécifiant des arguments.
{.is-success}


```python
def aire_disque(rayon):
    # [ ... ]
```

- Une fonction est un traitement générique. On ne connait pas à l’avance la valeur précise qu’aura un argument, et généralement on appelle la fonction pleins de fois avec des arguments différents…
- En définissant la fonction, on travaille donc avec un argument “abstrait” nommé ici rayon
- Le nom rayon en tant qu’argument de la fonction n’a de sens qu’a l’intérieur de cette fonction !
- En utilisant la fonction, on fourni la valeur pour rayon, par exemple: aire_disque(6).

## Les variables locales

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    # [ ... ]
```

- Les variables créées dans la fonction sont locales: elles n’ont de sens qu’a l’intérieur de la fonction
- Ceci dit, cela ne m’empêche pas d’avoir des variables aussi nommées rayon ou rayon_carree dans une autre fonction ou dans la portée globale (mais ce ne sont pas les mêmes entités)


## Le return

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    return 3.1415 * rayon_carree
```

- return permet de récupérer le résultat de la fonction
- C’est ce qui donne du sens à A = aire_disque(6) (il y a effectivement un résultat à mettre dans A)
- Si une fonction n’a pas de return, elle renvoie None
- return quitte immédiatement la fonction


## Erreur classique : Utiliser print au lieu de return

# Tabs {.tabset}
## Ici, rien ne s'affiche

> Ici, rien ne s'affiche
{.is-danger}

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    return 3.1415 * rayon_carree

A = aire_disque(6)      # A vaut bien quelque chose
                        # mais nous ne demandons pas de l'afficher ...
```

## Solution naïve 

> Solution naïve : remplacer le return par un print
{.is-danger}

> A part dans quelques cas, comme pour débugguer
{.is-info}

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    print(3.1415 * rayon_carree)    # Affiche le résultat dans la console

A = aire_disque(6)   # Mais maintenant A vaut None
                     # car la fonction n'a pas utilisé `return`
```

## Solution

> Solution que l'on préférera
{.is-success}

```python
def aire_disque(rayon):
    rayon_carree = rayon ** 2
    return 3.1415 * rayon_carree

A = aire_disque(6)   # Stocker le résultat dans A
print(A)             # Demander d'afficher A dans la console
```


# Exercice 1 

> Écrire une fonction annee_naissance qui prends en argument un age et retourne l’année de naissance (+/- 1) sachant que nous sommes en 2024. Par exemple, annee_naissance(33) retounera l’entier 1991.
{.is-info}


# Exercice 2

> Ecrire une fonction centrer prend en argument une chaîne de caractère, et retourne une nouvelle chaîne centrée sur 40 caractères. 
Par exemple print(centrer("Python")) affichera :
{.is-info}

```
|                Python                |
```

> Ajouter un argument optionnel pour gérer la largeur au lieu du 40 “codé en dur”. Par exemple print(centrer("Python", 20)) affichera :
{.is-info}
```
|      Python      |
```

	
> Créer une fonction encadrer qui utilise la fonction centrer pour produire un texte centré et encadré avec des ####. Par exemple, print(encadrer("Python", 20)) affichera :
{.is-info}
```
####################
|      Python      |
####################
```

---

<!--La fonction ajouter_deux_nombres prend deux arguments, les ajoute, et retourne la somme. Vous n'avez pas besoin de savoir comment elle calcule la somme, tout ce qui compte c'est qu'elle vous donne le bon résultat.

C'est comme commander un café dans un café : vous dites au barista ce que vous voulez (vous "appelez la fonction" avec des "arguments"), et vous obtenez un café (le "résultat").

Les fonctions sont très utiles car elles vous permettent de réutiliser du code sans avoir à le réécrire à chaque fois, ce qui rend votre code plus propre, plus facile à lire, et moins sujet aux erreurs. -->



