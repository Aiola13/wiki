---
title: Les fonctions
description: 
published: 1
date: 2023-11-06T21:47:26.387Z
tags: 
editor: markdown
dateCreated: 2023-11-06T21:27:03.487Z
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

