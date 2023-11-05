---
title: Les variables
description: 
published: 1
date: 2023-11-05T11:29:11.644Z
tags: 
editor: markdown
dateCreated: 2023-02-13T19:04:08.369Z
---

```python
message = "Je connais la réponse à l'univers, la vie et le reste"
reponse = 6 * 7

print(message)
print(reponse)
```

![sorcery.jpg](/images/python/sorcery.jpg)


# Définition

> Une variable c’est une sorte de boîte, étiquetée, où l’on peut stocker de l’information pour la consulter ou la modifier plus tard.

> Une variable est donc une zone de la mémoire de l'ordinateur dans laquelle une valeur est stockée. Cette variable est définie par un nom, un type et sa valeur (Voir cours algorithmie).
{.is-success}

> Pour l'ordinateur, il s'agit en fait d'une adresse, c'est-à-dire d'une zone particulière de la mémoire, où une valeur est stockée.
{.is-info}

Pour notre exemple ci-dessus
![memory2.png](/images/python/memory2.png)

![schema_memoire_ram_avec_donnees.jpg](/images/python/schema_memoire_ram_avec_donnees.jpg){.align-center}

En Python, la déclaration d'une variable et son initialisation (cad la première valeur que l'on va stocker dedans) se font en même temps. 

```python=
>>> x = 2 # Déclaration + Initialisation de x avec 2
>>> x 
2
```

Précision de la ligne 1 : 
- Déclaration implicite, Python a « deviné » que la variable était un entier. On dit que Python est un langage au typage dynamique.
- Python a alloué (réservé) l'espace en mémoire pour y accueillir un entier. Chaque type de variable prend plus ou moins d'espace en mémoire. Python a aussi fait en sorte qu'on puisse retrouver la variable sous le nom x.
- Enfin, Python a assigné la valeur 2 à la variable x.

```python
x = 42     # déclare (implicitement) une variable et assigne une valeur
x = 3.14   # ré-assigne la variable avec une autre valeur
y = x + 2  # déclare une autre variable y, à partir du contenu de x
print(y)   # affichage du contenu de y
```

Dans d'autres langages (en C par exemple), il faut coder ces différentes étapes une par une. Python étant un langage dit de haut niveau, la simple instruction x = 2 a suffi à réaliser les 3 étapes en une fois !

# Les types de variables

```python=
>>> y = 3.14
>>> y
3.14
>>> a = "bonjour"
>>> a
'bonjour'
>>> b = 'salut'
>>> b
'salut'
>>> c = """girafe"""
>>> c
'girafe'
>>> d = '''lion'''
>>> d
'lion'

```
