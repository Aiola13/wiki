---
title: Mémo
description: 
published: true
date: 2024-12-11T08:23:56.622Z
tags: python, mémo
editor: markdown
dateCreated: 2024-12-11T08:23:56.622Z
---

Mémo Syntaxe Python
===================

Récapitulation des principales syntaxes Python
----------------------------------------------

# Demander et afficher des informations

| Syntaxe | Description |
| --- | --- |
| `print("message")` | Affiche “message” dans la console |
| `v = input("message")` | Demande une valeur et la stocke dans `v` |

# Calculs

| Syntaxe | Description |
| --- | --- |
| `a + b` | Addition de a b |
| `a - b` | Soustraction de a et b |
| `a / b` | Division de a par b |
| `a * b` | Multiplication de a par b |
| `a % b` | Modulo (reste de division) de a par b |
| `a ** b` | Exponentiation de a par b |

Toutes ces opérations peuvent être appliquées directement sur une variable via la syntaxe du type `a += b` (additionner b à a et directement modifier la valeur de a avec le résultat).

# Types de variable et conversion

| Syntaxe | Description |
| --- | --- |
| `type(v)` | Renvoie le type de `v` |
| `int(v)` | Converti `v` en entier |
| `float(v)` | Converti `v` en float |
| `str(v)` | Converti `v` en string |

# Chaînes de caractères

| Syntaxe | Description |
| --- | --- |
| `chaine1 + chaine2` | Concatène les chaînes de caractères `chaine1` et `chaine2` |
| `chaine[n:m]` | Retourne les caractères de `chaine` depuis la position n à m |
| `chaine * n` | Retourne `chaine` concaténée `n` fois avec elle-meme |
| `len(chaine)` | Retourne la longueur de `chaine` |
| `chaine.replace(a, b)` | Renvoie `chaine` avec les occurences de `a` remplacées par `b` |
| `chaine.split(c)` | Créé une liste à partir de `chaine` en la séparant par rapport au caractère `c` |
| `chaine.strip()` | “Nettoie” `chaine` en supprimant les espaces et `\n` au début et à la fin |
| `\n` | Représentation du caractère ‘nouvelle ligne’ |

# Fonctions

```python=
    def ma_fonction(toto, tutu=3):
        une_valeur = toto * 6 + tutu
        return une_valeur
```   

Cette fonction :

* a pour nom `ma_fonction` ;
* a pour argument `toto` et `tutu` ;
* `tutu` est un argument optionnel avec comme valeur par défaut l’entier 3 ;
* `une_valeur` est une variable locale à la fonction ;
* elle retourne `une_valeur` ;

# Conditions

```python=
    if condition:
        instruction1
        instruction2
    elif autre_condition:
        instruction3
    elif encore_une_autre_condition:
        instruction4
    else:
        instruction5
        instruction6
``` 

## Opérateurs de conditions

| Syntaxe | Description |
| --- | --- |
| `a == b` | Egalité entre `a` et `b` |
| `a != b` | Différence entre `a` et `b` |
| `a > b` | `a` supérieur (strictement) à `b` |
| `a >= b` | `a` supérieur ou égal à `b` |
| `a < b` | `a` inférieur (strictement) à `b` |
| `a <= b` | `a` inférieur ou égal à `b` |
| `cond1 and cond2` | `cond1` et `cond2` |
| `cond1 or cond2` | `cond1` ou `cond2` |
| `not cond` | négation de la condition `cond` |
| `a in b` | `a` est dans `b` (chaîne, liste, set..) |

## Inline `ifs`

```python=
    parite = "pair" if n % 2 == 0 else "impair"
```  

# Exception, assertions

`try`/`except` permettent de tenter des instructions et d’attraper les exceptions qui peuvent survenir pour ensuite les gérer de manière spécifique :

```python=
    try:
       instruction1
       instruction2
    except FirstExceptionTime:
       instruction3
    except Exception as e:
       print("an unknown exception happened ! :" + e.str)
```

Les assertions permettent d’expliciter et de vérifier des suppositions faites dans le code :

```python=
    def une_fonction(n):
       assert isinstance(n, int) and is_prime(n), "Cette fonction fonctionne seulement pour des entiers premiers !"
```  

# Boucles

| Syntaxe | Description |
| --- | --- |
| `for i in range(0, 10)` | Itère sur `i` de 0 à 9 |
| `for element in iterable` | Itère sur tous les elements de iterable (liste, set, dict, …) |
| `for key, value in d.items()` | Itère sur toutes les clefs, valeurs du dictionnaire `d` |
| `while condition` | Répète un jeu d’instruction tant que `condition` est vraie |
| `break` | Quitte immédiatement une boucle |
| `continue` | Passe immédiatement à l’itération suivante d’une boucle |

```python
# Exemple avec une liste
for fruit in ['pomme', 'banane', 'mangue']:
    print(fruit)

# Exemple avec la fonction range()
for i in range(5):  # Itère de 0 à 4
    print(i)
    
# Exemple avec une condition
i = 0
while i < 5:
    print(i)
    i += 1  # Très important d'incrémenter i pour éviter une boucle infinie
```


# Structures de données

## Types de structure
|Nom | Syntaxe | Description |
| --- | --- | --- |
| Liste | `L = ["a", 2, 3.14 ]` | Suite ordonnée d’élément |
| Ensemble | `S = { "a", "b", 3 }` | Eléments unique, désordonné |
| Dictionnaire | `D = { "a": 2, "b": 4 }` | Ensemble de clé-valeurs, avec clés uniques) |
| Tuple | `T = (1,2,3)` | Suite d’élément non-mutables |

## Exemple d'utilisation
| Syntaxe | Description |
| --- | --- |
| `L[i]` | `i`-eme element d’une liste ou d’une tuple |
| `L[i:]` | Liste de tous les éléments à partir du `i`-eme |
| `L[i] = e` | Remplace le `i`-eme element par `e` dans une liste |
| `L.append(e)` | Ajoute `e` à la fin de la liste `L` |
| `S.add(e)` | Ajoute `e` dans le set `S` |
| `L.insert(i, e)` | Insère `e` à la position `i` dans la liste `L` |
| `chaine.join(L)` | Produit une string à partir de `L` en intercallant la string `chaine` entre les elements |

```python
# Création et manipulation de listes
L = ["a", 2, 3.14]  # Création d'une liste
print(L[1])          # Accède au deuxième élément de la liste, résultat: 2
L[1] = "b"           # Remplacement du deuxième élément
L.append(4)          # Ajout d'un élément à la fin de la liste
print(L)             # Affiche la liste modifiée

# Création et manipulation d'ensembles
S = {"a", "b", 3}    # Création d'un ensemble
S.add("c")           # Ajout d'un élément à l'ensemble
print(S)             # Affiche l'ensemble, l'ordre des éléments peut varier

# Création et manipulation de dictionnaires
D = {"a": 2, "b": 4} # Création d'un dictionnaire
D["c"] = 6           # Ajout d'une nouvelle paire clé-valeur
print(D["a"])        # Accède à la valeur associée à la clé "a", résultat: 2
print(D)             # Affiche le dictionnaire

# Création et manipulation de tuples
T = (1, 2, 3)        # Création d'un tuple
print(T[0])          # Accède au premier élément du tuple, résultat: 1
# T[0] = 4           # Cela produirait une erreur car les tuples sont immuables

# Utilisation de la méthode join sur une liste
chaine = "-"
L = ["a", "b", "c"]
resultat = chaine.join(L)  # Résultat: "a-b-c"
print(resultat)

```
# Fichiers

Ouvrir et lire un fichier :

```python=
    # Créé un contexte dans lequel le fichier
    # est ouvert en lecture en tant que 'f', 
    # et met son contenu dans 'content'
    
    with open("/un/fichier", "r") as f:  
        content = f.readlines()          
```

Ecrire dans un fichier :

```python=
    # Créé un contexte dans lequel le fichier
    # est ouvert en ré-écriture complète et
    # écrit le contenu de 'content' dedans.
    
    with open("/un/fichier", "w") as f:  
        f.write(content)                 
```                                       
    

(Le mode `'a'` (append) au lieu de `'w'` permet d’ouvrir le fichier pour ajouter du contenu à la fin plutôt que de le ré-écrire)


# Complexité des algorithmes
> La complexité d'un algorithme mesure la quantité de ressources (temps et mémoire) qu'il nécessite pour résoudre un problème. Il existe deux types principaux de complexité :
> - **Complexité temporelle** : le temps d'exécution par rapport à la taille de l'entrée.
> - **Complexité spatiale** : la quantité de mémoire requise par rapport à la taille de l'entrée.
> 
> ‎
{.is-success}

> La notation Big-O est utilisée pour exprimer la complexité en fonction de la taille de l'entrée :
{.is-info}


- **O(1)** : Complexité constante.
- **O(n)** : Complexité linéaire.
- **O(n²)** : Complexité quadratique.
- **O(log n)** : Complexité logarithmique.
- **O(n log n)** : Complexité quasi-linéaire.


<!--

1. Définition de l'algorithmie
L'algorithmie est la science des algorithmes, c'est-à-dire l'étude des méthodes de résolution de problèmes de manière structurée et logique. Un algorithme est une suite d'instructions précises permettant d'accomplir une tâche ou de résoudre un problème.

2. Propriétés d'un algorithme
Un bon algorithme doit respecter certaines propriétés :

Finitude : l'algorithme doit se terminer après un nombre fini d'étapes.
Précision : chaque étape doit être définie de manière claire et non ambiguë.
Entrées : il doit recevoir des données en entrée.
Sorties : il doit fournir des résultats attendus.
Efficacité : il doit être optimisé en termes de temps d'exécution et d'utilisation des ressources.
3. Représentation des algorithmes
Les algorithmes peuvent être représentés de différentes manières :

Pseudo-code : une description textuelle proche du langage naturel, facilitant la compréhension et l'écriture.
Organigrammes (ou flowcharts) : des diagrammes représentant graphiquement la suite d'instructions et les flux de contrôle.
Code : l'algorithme peut être directement traduit dans un langage de programmation (Python, C++, Java, etc.).
4. Types d'algorithmes
Il existe plusieurs types d'algorithmes selon la méthode utilisée :

Algorithmes séquentiels : les instructions sont exécutées dans l'ordre où elles sont écrites.
Algorithmes conditionnels : les instructions sont choisies selon une condition (si ... alors ... sinon ...).
Algorithmes itératifs : certaines instructions sont répétées un certain nombre de fois (boucles).
Algorithmes récursifs : l'algorithme s'appelle lui-même pour résoudre un sous-problème similaire.
5. Complexité des algorithmes
La complexité d'un algorithme mesure la quantité de ressources (temps et mémoire) qu'il nécessite pour résoudre un problème. Il existe deux types principaux de complexité :

Complexité temporelle : le temps d'exécution par rapport à la taille de l'entrée.
Complexité spatiale : la quantité de mémoire requise par rapport à la taille de l'entrée.
La notation Big-O est utilisée pour exprimer la complexité en fonction de la taille de l'entrée :

O(1) : Complexité constante.
O(n) : Complexité linéaire.
O(n²) : Complexité quadratique.
O(log n) : Complexité logarithmique.
O(n log n) : Complexité quasi-linéaire.
6. Structures de données courantes
Les algorithmes travaillent souvent avec des structures de données. Quelques-unes des structures les plus courantes :

Tableaux (array) : contiennent des éléments de même type, accessibles par leur index.
Listes chaînées (linked list) : chaque élément contient une référence vers l'élément suivant.
Piles (stack) : structure LIFO (Last In, First Out).
Files (queue) : structure FIFO (First In, First Out).
Arbres (tree) : structure hiérarchique avec des nœuds connectés par des arêtes.
Graphes (graph) : ensemble de nœuds reliés par des arêtes, avec ou sans orientation.
7. Exemples d'algorithmes célèbres
Tri : Tri à bulles (bubble sort), Tri rapide (quick sort), Tri fusion (merge sort).
Recherche : Recherche linéaire, Recherche dichotomique (ou binaire).
Parcours de graphes : Parcours en largeur (BFS), Parcours en profondeur (DFS).
Algorithmes de plus court chemin : Dijkstra, Bellman-Ford.
8. Pseudo-code d'exemple : Recherche binaire
Voici un exemple de pseudo-code pour un algorithme de recherche binaire dans un tableau trié :

text
Copier le code
Fonction RechercheBinaire(tableau, valeur) :
    Début = 0
    Fin = longueur(tableau) - 1

    Tant que Début ≤ Fin :
        Milieu = (Début + Fin) / 2
        Si tableau[Milieu] == valeur :
            Retourner Milieu
        Sinon Si tableau[Milieu] < valeur :
            Début = Milieu + 1
        Sinon :
            Fin = Milieu - 1

    Retourner -1 // valeur non trouvée
9. Conseils pour concevoir un algorithme
Décomposer le problème en sous-problèmes plus simples.
Écrire un pseudo-code avant de coder.
Tester l'algorithme avec des cas simples, puis avec des cas complexes.
Optimiser les performances si nécessaire (en fonction de la complexité).
-->





<!--
1. Définition de l'Algorithmie
L'algorithmie est la science qui consiste à concevoir et analyser des algorithmes. Un algorithme est une suite finie et ordonnée d'instructions permettant de résoudre un problème ou d'effectuer une tâche. Les algorithmes sont à la base de l'informatique, qu'il s'agisse de programmation, de traitement de données, de calculs ou de prise de décision automatique.

2. Propriétés d’un Algorithme
Un bon algorithme doit respecter plusieurs critères :

Finitude : l’algorithme doit avoir une fin.
Défini : chaque étape doit être clairement exprimée.
Efficace : il doit résoudre le problème en un temps raisonnable.
Lisibilité : il doit être compréhensible par les autres.
3. Les Structures Algorithmiques
Il existe trois structures fondamentales utilisées pour construire un algorithme :

Séquence : exécution d'instructions les unes après les autres.

pseudo
Copier le code
Lire A
Lire B
C ← A + B
Afficher C
Condition (ou sélection) : choix entre plusieurs alternatives.

pseudo
Copier le code
Si (A > B) Alors
    Afficher "A est plus grand"
Sinon
    Afficher "B est plus grand"
Fin Si
Boucle (ou répétition) : exécution répétée d’instructions.

pseudo
Copier le code
Tant que (i ≤ 10) faire
    Afficher i
    i ← i + 1
Fin Tant que
4. Notions de Base : Variables, Types et Opérations
Variable : espace de stockage pour une donnée.
Type de données : nature de la valeur (entier, réel, caractère, booléen).
Opérations : arithmétiques (+, -, *, /), comparaisons (=, >, <, etc.), logiques (ET, OU, NON).
5. Les Structures de Données
Les algorithmes s’appuient souvent sur des structures de données pour manipuler des informations :

Tableaux : ensemble d’éléments de même type.
Listes : ensemble dynamique d’éléments.
Piles : collection avec insertion et suppression en dernier entré premier sorti (LIFO).
Files : collection avec insertion en premier entré premier sorti (FIFO).
6. Les Algorithmes de Recherche
Recherche Séquentielle : parcours linéaire des éléments, utile pour les petites collections non triées.
Recherche Dichotomique : recherche rapide dans une liste triée. L'algorithme divise la liste par deux à chaque étape pour trouver l'élément.
7. Les Algorithmes de Tri
Les algorithmes de tri permettent d’organiser des données de manière ordonnée :

Tri par Insertion : insertion d'un élément à sa place correcte.
Tri par Sélection : recherche du plus petit élément pour l’insérer à sa place.
Tri à Bulles : échange successif des éléments adjacents mal placés.
Tri Rapide (QuickSort) : division de la liste autour d’un pivot.
8. Les Algorithmes Récursifs
La récursion consiste à résoudre un problème en le décomposant en sous-problèmes plus petits de même nature. Exemples classiques : factorielle, Fibonacci, recherche binaire récursive.

Exemple : Factorielle

pseudo
Copier le code
Fonction Factorielle(n)
    Si (n = 0) Alors
        Retourner 1
    Sinon
        Retourner n * Factorielle(n - 1)
    Fin Si
Fin Fonction
9. Complexité d’un Algorithme
Complexité temporelle : mesure le temps d’exécution en fonction de la taille des données (notation O() par exemple : O(n), O(log n), O(n²)).
Complexité spatiale : mesure la mémoire utilisée.
10. Conseils Pratiques
Décomposer le problème : divisez le problème en sous-problèmes simples.
Pseudo-code : écrivez l'algorithme sous forme de pseudo-code avant de coder.
Tester les cas limites : vérifiez le comportement pour les entrées extrêmes.
Analyser la complexité : considérez les aspects de performance dès la conception.
-->