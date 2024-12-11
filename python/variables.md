---
title: Les variables
description: 
published: true
date: 2024-12-11T08:24:51.344Z
tags: python, variables
editor: markdown
dateCreated: 2024-12-11T08:24:51.344Z
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
>>> y = 3.14 # Réel | Float
>>> y
3.14
>>> a = "bonjour" # Chaîne de caractères | String
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

| Type               | Nom                          | Exemple                    |
|--------------------|------------------------------|----------------------------|
| Entier       | int, integer                | `42`, `-7`                 |
| Flottant (Réel)   | Nombre à virgule flottante, float   | `3.14`, `-0.001`           |
| Chaîne (str)       | Chaîne de caractères, string, str       | `"Bonjour"`, `'Python'`    |
| Booléen (bool)     | Valeur de vérité, bool, boolean            | `True`, `False`            |
| Liste (list)       | Collection modifiable        | `[1, 'deux', 3.0]`         |
| Tuple (tuple)      | Collection immuable          | `(1, 'deux', 3.0)`         |
| Dictionnaire (dict)| Paires clé-valeur            | `{'nom': 'Alice', 'age': 30}`|
| Ensemble (set)     | Ensemble de valeurs uniques  | `{1, 2.3, 'python'}`       |

```python
42            # Entier / integer               / int
3.1415        # Réel                           / float
"Marius"        # Chaîne de caractère (string)   / str
True / False  # Booléen                        / bool
None          # ... "rien" / aucun (similar à `null` dans d'autres langages)
```
---

# Exercice 1

> Déclarer trois types de variables et les afficher
{.is-info}

# Exercice 2

>  Corriger les erreurs des lignes suivantes
> 
> Fonctionnement attendu :
> Les chaînes de caractères doivent être correctement affichées et les variables ne doivent plus générer d’erreurs
{.is-info}

```python
a = -2..5
b = true
c = falce
d = Bonjour tout le monde

print('Hello World !")
print('Je m'appelle Gilbert.')
print("Je dis souvent "du coup" mais du coup c’est pas génial.")
print(Oui, je suis très philosophe.)
```
---

# Conversion de type

> La conversion de type, souvent appelée "cast" ou "transtypage", consiste à changer le type d'une variable ou d'une valeur en un autre type.
{.is-success}

> Python est un langage à typage dynamique, ce qui signifie que le type des variables est déterminé à l'exécution et non à l'avance. Cependant, Python est aussi fortement typé, ce qui implique que le type d'une variable est important et que Python ne convertira pas automatiquement les types de manière inattendue (conversion explicite vs implicite)
{.is-warning}


```python
int("3")      -> 3
str(3)        -> "3"
float(3)      -> 3.0
int(3.14)     -> 3
str(3.14)     -> "3.14"
float("3.14") -> 3.14
int(True)     -> 1
int("trois")  -> Erreur / Exception
```

# Nommage

> En Python, les noms de variables peuvent être composés de lettres majuscules (A-Z), minuscules (a-z), chiffres (0-9) et du caractère souligné (_). 
{.is-success}

> Cependant, il est important de se rappeler que Python distingue les majuscules des minuscules, ce qui signifie que "toto" et "Toto" seraient considérés comme deux variables distinctes. De plus, un nom de variable ne doit jamais commencer par un chiffre.
{.is-warning}


```python 
# Exemple de variables valides
mon_nom = "John"
age_du_capitaine = 52
_nombre2 = 300

# Exemples de sensibilité à la casse
Toto = "Un prénom"
toto = "Un autre prénom différent de Toto"

# Exemples de noms de variables invalides (ils ne seront pas exécutés)
# 2nombre = 500  # Cela va provoquer une erreur car ça commence par un chiffre
# mon-nom = "John"  # Cela va provoquer une erreur car il contient un tiret
```
# Comparaison de différentes instructions

Faire un calcul sans l’afficher ni le stocker nul part:
```
6*7
```

Faire un calcul et l’afficher dans la console:
```
print(6*7)
```

Faire un calcul et stocker le résultat dans une variable r pour le réutiliser plus tard
```
r = 6*7
```

# Interactivité basique

Dans un terminal il est possible de demander une information à l’utilisateur avec `input(“message”).

```python
reponse = input("Combien font 6 fois 7 ?")
```

> ce que renvoie input() est une chaîne de caractère !
{.is-warning}



# Exercice 3

> Ecrire votre algorithme sur les opérations en python.
> 
> Fonctionnement attendu :
> Le résultat doit contenir deux demandes de valeurs, puis afficher le résultat de chaque opération : addition, soustraction,
> multiplication, division et modulo.
{.is-info}

> Rappel : input renvoie toujours des string.
{.is-warning}








# Résumé

- Caractères autorisés : caractères alphanumériques (a-zA-Z0-9) et _.
- Les noms sont sensibles à la casse : toto n’est pas la même chose que Toto!
- (Sans commencer par un chiffre)