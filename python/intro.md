---
title: Introduction
description: 
published: true
date: 2024-12-11T08:24:23.348Z
tags: introduction, intro
editor: markdown
dateCreated: 2024-12-11T08:24:23.348Z
---

![python_design.png](/images/python/python_design.png){.align-center}

# C'est quoi Python, un serpent 🐍 un cousin de snake dans Metal Gear Solid ? 🤔

> Le langage de programmation **Python** a été créé en 1989 par Guido van Rossum, aux Pays-Bas, dans le cadre d'un projet de programmation de loisir qui devait l'occuper pendant la semaine de Noël. Le nom Python rend hommage à la série télévisée Monty Python's Flying Circus, dont G. van Rossum est un grand fan. La première version publique de ce langage a été publiée en 1991.
{.is-success}

<details> 
  <summary>L'histoire moins condensée ?</summary>
   À l'époque, Guido travaille en tant que développeur dans un laboratoire de recherche du gouvernement à Amsterdam. Il passe ses journées à faire des mathématiques, des calculs sur des trucs complexes et à notamment faire des recherches sur les computer sciences.

Dans ce laboratoire, son premier travail est d'assister une équipe dans la création d'un nouveau langage de programmation qui s'appelle ABC, aujourd'hui disparu.
  
Insatisfait d'ABC (qui est une sorte de mélange entre un script shell et le langage C, pas interprété et très verbeux) pour sa complexité et son manque d'efficacité, Guido décide de créer son propre langage. S'inspirant de C, Perl, et ABC, il ambitionne de développer un outil pour améliorer sa productivité et celle de son équipe. En trois mois, il jette les bases de ce qui deviendra Python, un langage qui transcendera largement ses objectifs initiaux. 🚀
</details>


![guido-1920x1000-1920x1000.webp](/images/python/guido-1920x1000-1920x1000.webp){.align-center}

<center>

|![guido.jpg](/images/python/guido.jpg){.align-center}|![monty-pythons_flying-circus.jpg](/images/python/monty-pythons_flying-circus.jpg =800x)|
|:-------------:|:----:|

</center>




> La dernière version de **Python** est la **version 3**. Plus précisément, la **version 3.12.2**, qui a été publiée le 6 Février 2024. 

> La version 2 de Python est désormais obsolète et a cessé d'être maintenue depuis 2020. DON'T TOUCH !
{.is-warning}

> La Python Software Foundation est l'association qui organise le développement de Python et anime la communauté de développeurs et d'utilisateurs.

## Pourquoi l'utiliser ? Ya les Grafcets qui existent !

Pourquoi Python :
- Il est **multi-plateforme**, il fonctionne sur la quasi totalité des systèmes d'exploitations (Windows, Mac OS X, Linux, Android ...) et machines (Raspberry Pi jusqu'aux supercalculateurs)
- Il est **gratuit** et **Open Source**. Vous pouvez l'installer sur autant d'ordinateurs que vous voulez (même sur votre téléphone !)
- C'est un **langage de haut niveau**. Il demande relativement peu de connaissance sur le fonctionnement d'un ordinateur pour être utilisé
- C'est un **langage interprété**. Un script Python n'a pas besoin d'être compilé pour être exécuté, contrairement à des langages comme le C ou le C++. Donc très utile pour le prototypage rapide
- Il est **orienté objet**. C'est-à-dire qu'il est possible de concevoir en Python des entités qui miment celles du monde réel (un atome, un personnage etc.)
- Il est relativement **simple** à prendre en main avec un syntaxe légère et flexible (typage dynamique)
- Il est très utilisé !!! (Google, NSA, Youtube, Netflix, NASA ...)

## Installation et configuration de Python

> Pour l'installation sur Windows vous pouvez passer par l'installateur officiel via le site [python.org](https://python.org), via un gestionnaire de paquet tel que [Chocolatey](https://chocolatey.org) ou [Winget](https://github.com/microsoft/winget-cli), ou encore en utilisant la distribution [Miniconda](https://docs.conda.io/en/latest/miniconda.html) qui intégre tout le nécessaire pour l'utilisation de Python.
{.is-success}


> Miniconda est un installateur minimal gratuit et un gestionnaire de paquet pour conda développé par **Anaconda®**. Cette version contient Python et tous les paquets dont il dépend, et un petit nombre d'autres paquets utiles, incluant pip, zlib et quelques autres. Vous pouvez utiliser la commande conda install pour installer plus de 720 paquets conda supplémentaires depuis le dépôt d'Anaconda.
{.is-info}


Résumé : 
- Linux : Inclus
- OSX : Inclus (à mettre à jour depuis python.org ou via homebrew)
- Windows : Installation sur python.org
- Windows 10 & 11 : Fais parti de WSL (Windows Subsystem Linux)🎉 
- Intégré sur les cartes type Raspberry Pi, Banana Pi…

Généralement il faut lancer python3 explicitement ! (et non python car sinon cela lance python2) pour utiliser python3.

## Introduction au shell

> Un **shell** est **un interpréteur de commandes** interactif permettant d'interagir avec l'ordinateur. On utilisera le shell pour lancer l'interpréteur Python. {.is-success}

|![shell_linux.png](/images/python/shell_linux.png)|![shell_windows.png](/images/python/shell_windows.png)|
|:-------------:|:----:|

Pour approfondir la notion de shell, allez voir le cours sur mon wiki.
- du shell Unix fonctionnant sous Mac OS X et Linux ;
- du shell PowerShell fonctionnant sous Windows.

Un shell possède toujours une invite de commande, c'est-à-dire un message qui s'affiche avant l'endroit où on entre des commandes. Cette invite de commande est souvent représentée par le symbole dollar <kbd>$</kbd> ou le chevron <kbd>></kbd>.

Par exemple, si on vous demande de lancer l'instruction suivante :
```python
$ python3
```

il faudra taper seulement python3 sans le $ ni l'espace après le $.

## Êtes-vous prêt à vous faire piquer ? Premier contact !

Le Python est un langage interprété, c'est-à-dire que chaque ligne de code est lue puis interprétée afin d'être exécutée par l'ordinateur. 

### En interactif

Pour Windows :
```python
PS C:\Users\Lisa> python3
Python 3.11.1 (tags/v3.11.1:a7a450f, Dec  6 2022, 19:58:39) [MSC v.1934 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Pour Unix : 
```python
Lisa@LISA:~
$ python3
Python 3.11.1 (tags/v3.11.1:a7a450f, Dec  6 2022, 19:58:39) [MSC v.1934 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Les blocs : 
- PS C:\Users\Lisa> pour Windows,
- Lisa@LISA:~ pour Linux.

représentent l'invite de commande de vitre **shell**. L'endroit où vous communiquez avec l'ordinateur.

Le triple chevron >>> est l'invite de commande (prompt en anglais) de l'interpréteur Python. Ici, Python attend une commande que vous devez saisir au clavier.

```python
>>> variable = "Hello World"
>>> print(variable)
Hello World
```

## Les commentaires

Tout ce qui suit le caractère # est ignoré par Python jusqu'à la fin de la ligne et est considéré comme un commentaire.

Les commentaires doivent expliquer votre code dans un langage humain. 


> Le croisillon (number sign or hash in english), ou carré au Canada, est un signe typographique noté ‹ # › et souvent confondu avec le symbole musical dièse transcrit ‹ ♯ ›.
{.is-warning}


```python
# Votre premier commentaire en  Python.
print("Hello world!")
```

## Bloc d'instructions et indentation

En programmation, il est courant de répéter un certain nombre de choses ou d'exécuter plusieurs instructions si une condition est vraie, par exemple. 

> Pour indiquer cela, on décalera vers la droite ces deux instructions par rapport à la ligne précédente. 
> Ce décalage est appelé **indentation**, et l'ensemble des lignes indentées constitue **un bloc d'instructions**. En pratique, l'indentation en Python doit être homogène avec 4 espaces.
{.is-info}


```python
for i in range(5):
# les deux instructions suivantes sont indentées de la même manière
# cela signifie qu'elles font partie du même bloc d'instructions
    print("Bonjour")
    print("Comment vas-tu?")
print("Au revoir")
```


```python
x = 5
if x > 0:
    print("x est positif")
    print("x est plus grand que zéro")
else:
    print("x est négatif")
```