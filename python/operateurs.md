---
title: Les instructions
description: 
published: 1
date: 2023-11-05T14:22:35.700Z
tags: 
editor: markdown
dateCreated: 2023-11-05T13:57:42.448Z
---

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
```

### La concaténation de chaînes

Le « + »

```python
# Déclaration de deux chaînes de caractères
premiere_chaine = "Bonjour, "
deuxieme_chaine = "le monde!"

# Concaténation des chaînes
chaine_concatenee = premiere_chaine + deuxieme_chaine

# Affichage du résultat
print(chaine_concatenee)
```

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
| `===` | Identité    (valeur et type) |
| `!=`  |          Différent           |
| `!==` | Différent  (valeur ou type)  |
|  `<`  |    Strictement Inférieur     |
| `<=`  |      Inférieur ou égal       |
|  `>`  |    Strictement Supérieur     |
| `>=`  |      Supérieur ou égal       |
| `>=`  |      Supérieur ou égal       |
| `<=>` |      Combiné    (PHP 7)      |

### Cas particulier de l'affectation

|   Signe    |         Opération         |   Equivalent    |
| :--------: | :-----------------------: | :-------------: |
|  `$a = 1`  |   Afffection par copie    |        \        |
| `$b = &$a` | Affectation par référence |        \        |
| `$a += $b` |          Egalité          | `$a = $a + $b`  |
| `$a -= $b` |         Identité          | `$a = $a -* $b` |
| `$a *= $b` |         Différent         | `$a = $a * $b`  |
|   `$a++`   |      Incrémentation       |  `$a = $a + 1`  |

/!\ Une référence est une copie de l'adresse mémoire de la variable.

### Règles des priorités des expressions

![regles-priorite-operateurs_(small).png](/images/php/regles-priorite-operateurs_(small).png)


# Ex.1.1 Calculs dans l’interpréteur
À l’aide de python, calculer le résultat des opérations suivantes :
- 567×72
- 33⁴
- 98.2/6
- ((7×9)⁴)/6
- vrai et non (faux ou non vrai)