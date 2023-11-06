---
title: Instructions conditionnelles
description: 
published: 1
date: 2023-11-06T20:33:12.192Z
tags: 
editor: markdown
dateCreated: 2023-11-06T20:32:54.403Z
---

# Les instructions conditionnelles (Structures alternatives)

> Les instructions conditionnelles, souvent appelées "conditions", sont comme des embranchements sur une route pour un programme : elles permettent à votre code de prendre des décisions. En Python, ces décisions se basent sur la vérité ou la fausseté d'une expression, ce qu'on appelle une condition.
{.is-success}


La structure la plus basique d'une condition en Python utilise le mot-clé if. Voici comment cela fonctionne :

```python
if condition1:
    # Bloc de code pour la condition1 vraie
elif condition2:
    # Bloc de code pour la condition2 vraie
else:
    # Bloc de code si aucune des conditions précédentes n'est vraie
```

> La condition est une expression qui peut être vraie (True) ou fausse (False). Si elle est vraie, le bloc de code indenté sous le if s'exécutera. Si elle est fausse, Python ignorera ce bloc et continuera avec le reste du programme
{.is-success}

> Attention à l’indentation !
{.is-warning}

> Tout n’est pas nécessaire, par exemple on peut simplement mettre un if ou un if et un else :
{.is-info}

```python
if condition:
    # Bloc de code qui s'exécute si la condition est vraie
```

```python
if condition:
    # Bloc de code qui s'exécute si la condition est vraie
else:
    # Bloc de code qui s'exécute si la condition est fausse
```

> Vous pouvez ajouter autant de elif que nécessaire entre if et else.
{.is-warning}

## Exemple

```python
age = 18
if age < 18:
    print("Vous êtes mineur.")
elif age == 18:
    print("Vous venez de devenir majeur.")
else:
    print("Vous êtes majeur.")
```



