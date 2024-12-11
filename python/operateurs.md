---
title: Les instructions
description: 
published: true
date: 2024-12-11T08:25:13.563Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:25:13.563Z
---

> ⚠️ Rappel sur les instructions
{.is-warning}


# Les instructions

## Les opérateurs :

### Les opérateurs arithmétiques

| Signe |               Opération               |
| :---: | :-----------------------------------: |
|  `–`  |     (unaire) Changement de signe      |
|  `+`  |               Addition                |
|  `-`  |             Soustraction              |
|  `*`  |            Multiplication             |
|  `/`  |               Division                |
|  `%`  | Modulo (reste de la division entière) |
|  `**`  | Exposant |

```python
2 + 3   # Addition
2 - 3   # Soustraction
2 * 3   # Multiplication
2 / 3   # Division
2 % 3   # Modulo
2 ** 3  # Exponentiation

>>> x = 45
>>> x + 2
47
>>> x - 2
43
>>> x * 3
135
>>> y = 2.5
>>> x - y
42.5
>>> (x * 10) + y
452.5
```

### La concaténation de chaînes

> L'opérateur d'addition « + » concatène (assemble) deux chaînes de caractères.
{.is-success}


```python
# Déclaration de deux chaînes de caractères
premiere_chaine = "Bonjour, "
deuxieme_chaine = "le monde!"

# Concaténation des chaînes
chaine_concatenee = premiere_chaine + deuxieme_chaine

# Affichage du résultat
print(chaine_concatenee)
```


### La multiplication de chaînes

> L'opérateur de multiplication « * » entre un nombre entier et une chaîne de caractères duplique (répète) plusieurs fois une chaîne de caractères.
{.is-success}


> Les opérateurs « + » et « * » se comportent différemment s'il s'agit d'entiers ou de chaînes de caractères : 2 + 2 est une addition alors que "2" + "2" est une concaténation. On appelle ce comportement **redéfinition des opérateurs**.
{.is-warning}

### Les opérateurs logiques (et binaires)

|   Signe    |      Opération      |
| :--------: | :-----------------: |
|    `!`     |     NON logique     |
| `&&` `AND` |     ET logique      |
| `||` `OR`  |     OU logique      |
|   `XOR`    | OU exclusif logique |


### Les opérateurs relationnels (de comparaison)

| Signe |          Opération           |
| :---: | :--------------------------: |
| `==`  |           Egalité            |
| `is`	| Identité  Comparaison de référence/identité de l'objet |
| `!=`  |          Différent           |
|`is not`| Différent (identité)	Comparaison de référence/identité de l'objet  |
|  `<`  |    Strictement Inférieur     |
| `<=`  |      Inférieur ou égal       |
|  `>`  |    Strictement Supérieur     |
| `>=`  |      Supérieur ou égal       |

> L'opérateur `is` vérifie si les deux variables pointent vers le même objet (pas seulement si elles sont équivalentes, mais si elles sont réellement la même entité en mémoire).
{.is-info}


> /!\ Une référence est une copie de l'adresse mémoire de la variable.
> {.is-warning}



### Cas particulier de l'affectation

|   Signe    |         Opération         |   Equivalent    |
| :--------: | :-----------------------: | :-------------: |
|  `$a = 1`  |   Affectation par copie    |        \        |
| `$a += $b` |          Affectation additionnelle         | `$a = $a + $b`  |
| `$a -= $b` |         Affectation soustractive          | `$a = $a -* $b` |
| `$a *= $b` |         Affectation multiplicative         | `$a = $a * $b`  |


> /!\ Python ne possède pas d'opérateur d'incrémentation (++) ou de décrémentation (--) comme dans d'autres langages tels que C, C++, ou PHP. À la place, on utilise += 1 ou -= 1.
{.is-info}

```python
a = [1, 2, 3]
b = a
print(b is a) # True
print(b == a) # True
#Dans cet exemple, a et b réfèrent au même objet. Par conséquent, l'opérateur is renvoie True.


a = [1, 2, 3]
b = [1, 2, 3]
print(b is a) # False
print(b == a)  # True
#Dans cet exemple, a et b ont la même valeur, mais réfèrent à des objets différents. L'opérateur is renvoie False, contrairement à l'opérateur ==
```

### Règles des priorités des expressions

![regles-priorite-operateurs_(small).png](/images/php/regles-priorite-operateurs_(small).png)

## La conversion de type

```python
>>> i = 3
>>> str(i)
'3'
>>> i = '456'
>>> int(i)
456
>>> float(i)
456.0
>>> i = '3.1416'
>>> float(i)
3.1416



int("3")      -> 3
str(3)        -> "3"
float(3)      -> 3.0
int(3.14)     -> 3
str(3.14)     -> "3.14"
float("3.14") -> 3.14
int(True)     -> 1
int("trois")  -> Erreur / Exception
```