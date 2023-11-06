---
title: Les conditions itératives
description: 
published: 1
date: 2023-11-06T20:55:16.471Z
tags: 
editor: markdown
dateCreated: 2023-11-06T20:43:13.915Z
---

# Définition

> Les instructions itératives, aussi connues sous le nom de boucles, sont utilisées pour répéter une même section de code plusieurs fois. Il y a deux types principaux de boucles en Python : for et while.
{.is-success}

# Syntaxe

## La boucle `while`

### Définition

`while <condition>` : Continue à exécuter un bloc de code tant qu'une condition est vraie. . C’est une boucle simple qui teste à chaque tour (avec une sorte de if) si on doit continuer de boucler.


### Syntaxe

```python
while condition:
    # Bloc de code à exécuter tant que la condition est vraie
```

> Avant chaque tour de boucle, Python évalue la condition. Si elle est True, le code sous la boucle est exécuté. Si elle est False, la boucle s'arrête.
{.is-info}


### Exemple


```python
i = 0
while i < 5:  # La boucle s'exécute tant que i est inférieur à 5
    print(i)
    i += 1  # Très important d'ajouter une opération qui change la condition

```
 
## La boucle `for`

### Définition

`for ...` : Utilisée pour parcourir les éléments d'une séquence (comme une liste, un tuple ou une chaîne de caractères) dans l'ordre où ils apparaissent.


### Syntaxe

```python
for element in sequence:
    # Bloc de code à exécuter pour chaque élément
```

> Chaque fois que la boucle tourne, element prend la valeur du prochain élément dans sequence, et le bloc de code sous la boucle est exécuté.
{.is-info}


### Exemple

```python
for i in range(5):  # i prendra les valeurs de 0 à 4
    print(i)
```