---
title: Instructions|Structures conditionnelles
description: 
published: true
date: 2024-12-11T08:26:24.210Z
tags: conditions
editor: markdown
dateCreated: 2024-12-11T08:26:24.210Z
---

# Définition
> Les instructions conditionnelles, souvent appelées "conditions", sont comme des embranchements sur une route pour un programme : elles permettent à votre code de prendre des décisions. En Python, ces décisions se basent sur la vérité ou la fausseté d'une expression, ce qu'on appelle une condition.
{.is-success}

# Syntaxe générale

> La structure la plus basique d'une condition en Python utilise le mot-clé if. Voici comment cela fonctionne :
{.is-info}


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

# Exemple

```python
age = 18
if age < 18:
    print("Vous êtes mineur.")
elif age == 18:
    print("Vous venez de devenir majeur.")
else:
    print("Vous êtes majeur.")
```


# Lien avec les booléens

> Les conditions comme age < 18 sont en fait transformées en booléen lorsque la ligne est interprétée.
{.is-info}

```python
a_est_egal_a_18 = ( age == 18)

if age_est_egal_a_18:
    [...]
else:
    [...]
```

# Écrire des conditions

```python
angle == pi      # Égalité
angle != pi      # Différence
angle > pi       # Supérieur
angle >= pi      # Supérieur ou égal
angle < pi       # Inférieur
angle <= pi      # Inférieur ou égal
```

# Combiner des conditions

```python
x = 2

print("x > 0:", x > 0) # vrai
print("x > 0 and x == 2:", x > 0 and x == 2) # vrai et vrai donne vrai
print("x > 0 and x == 1:", x > 0 and x == 2) # vrai et faux donne faux
print("x > 0 or x == 1:", x > 0 or x == 1) # vrai ou faux donne vrai
print("not x == 1:", not x == 1) # non faux donne vrai
print("x > 0 or not x == 1:", x > 0 or not x == 1) # vrai ou (non faux) donne vrai ou vrai donne vrai
```

# Conditions “avancées”

:construction:Ecriture en cours:construction:




