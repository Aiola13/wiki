---
title: Les conditions itératives
description: 
published: 1
date: 2023-11-06T21:07:24.678Z
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

> Elle s'adapte parfaitement aux données grâce à la notion d'itérateur (expliqué plus tard)
> On peut traduire la boucle Python for element in collection: en français par “Pour chaque élément de ma collection répéter …”. Nous avons donc besoin d’une “collection” (en fait un iterateur) pour l’utiliser.
{.is-info}



### Syntaxe

```python
for element in sequence:
    # Bloc de code à exécuter pour chaque élément
```

> Chaque fois que la boucle tourne, element prend la valeur du prochain élément dans sequence, et le bloc de code sous la boucle est exécuté.
{.is-info}


### Exemple

```python
ma_liste = [7, 2, -5, 4]

for entier in ma_liste:
    print(entier)
```

```python
for i in range(5):  # i prendra les valeurs de 0 à 4
    print(i)
```

# Mots-clés continue et break

## Définition

> **continue** permet de passer immédiatement à l’itération suivante
{.is-success}


> **break** permet de sortir immédiatement de la boucle
{.is-success}

## Exemple

```python
for i in range(0,10):
    if i % 2 == 0:
        continue

    print("En ce moment, i vaut " + str(i))
```
> Affiche le message seulement pour les nombres impairs
{.is-warning}

---

```python
for i in range(0,10):
    if i == 7:
        break

    print("En ce moment, i vaut " + str(i))
```

> Affiche le message pour 0 à 6
{.is-warning}

# Notion d'itérateur

