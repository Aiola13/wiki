---
title: Instructions|Structures itératives
description: 
published: true
date: 2024-12-11T08:26:58.114Z
tags: boucles, loop
editor: markdown
dateCreated: 2024-12-11T08:26:58.114Z
---

# Définition

> Les instructions itératives, aussi connues sous le nom de boucles, sont utilisées pour répéter une même section de code plusieurs fois. Il y a deux types principaux de boucles en Python : for et while.
{.is-success}

# Syntaxe

## La boucle `while`

### Définition

> `while <condition>` : Continue à exécuter un bloc de code tant qu'une condition est vraie. . C’est une boucle simple qui teste à chaque tour (avec une sorte de if) si on doit continuer de boucler.
{.is-success}



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

> `for ...` : Utilisée pour parcourir les éléments d'une séquence (comme une liste, un tuple ou une chaîne de caractères) dans l'ordre où ils apparaissent. 
{.is-success}


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

# Notion d'itérateur (Avancés)

## Définition

> Un **itérateur** en Python est un objet qui permet de parcourir un conteneur, notamment des structures de données telles que les listes, tuples, dictionnaires et ensembles. C'est une abstraction qui prend en charge le protocole d'itération, qui consiste en les méthodes __iter__() et __next__().
{.is-success}


- La méthode __iter__() est appelée sur l'objet conteneur pour obtenir un itérateur de celui-ci.
- La méthode __next__() est appelée sur l'itérateur pour obtenir le prochain élément du conteneur. Lorsqu'il n'y a plus d'éléments à parcourir, __next__() déclenche une exception StopIteration pour signaler la fin de l'itération.

> Les itérateurs sont utilisés implicitement par les boucles for pour réaliser des itérations sur des collections sans avoir besoin de connaître la structure sous-jacente ni la manière dont les éléments sont stockés ou liés entre eux.
{.is-info}


## Métaphore

> Imaginons une boîte de chocolats avec des compartiments. Chaque compartiment contient un chocolat différent. Vous voulez les goûter tous, mais vous êtes masqué et ne savez pas combien il y en a ni comment ils sont organisés à l'intérieur.
> 
> Un itérateur serait comme un ami qui connaît parfaitement la boîte. Vous lui dites simplement "donne-moi le prochain chocolat", et il sait exactement où mettre la main pour vous en offrir un nouveau, jusqu'à ce qu'il n'y en ait plus. Vous n'avez pas besoin de savoir combien de compartiments il y a ni où ils se trouvent; votre ami s'occupe de tout. En Python, la boucle for joue le rôle de cet ami, parcourant chaque élément de la collection sans que vous ayez à gérer les détails.