---
title: Les structures de données
description: 
published: 1
date: 2023-02-17T07:22:09.021Z
tags: 
editor: markdown
dateCreated: 2023-02-17T07:07:50.843Z
---


# Définition
> Les structures de données permettent de stocker des séries d'information et d'y accéder (plus ou moins) facilement et rapidement. 
{.is-success}



# Les listes

> Une liste est une structure de données qui contient une série de valeurs, une collection d'éléments **ordonnés** référencé par un indice. Python autorise la construction de liste contenant des valeurs de types différents (par exemple entier et chaîne de caractères), ce qui leur confère une grande flexibilité. 
{.is-success}


```python
animaux_favoris = [ "girafe", "chenille", "lynx" ]
fibonnaci = [ 1, 1, 2, 3, 5, 8 ]
stuff = [ 3.14, 42, "bidule", ["a", "b", "c"] ]
```

## Accès à element particulier ou a une "tranche"

```python
animaux_favoris[1]      ->  "chenille"
animaux_favoris[-2:]    ->  ["chenille", "lynx"]
```


## Longueur

```python
len(animaux_favoris)    -> 3
```

## Plage et liste

```python
list(range(10)) 
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
```python
list(range(0, 1000, 200)) 
[0, 200, 400, 600, 800]
```

## Minimum, Maximum et Somme

```python
liste = list(range(10))
sum(liste) 
min(liste) 
max(liste) 
```



## Tester qu'un élément est (ou n'est pas) dans une liste

```python
"lynx" in animaux_favoris   # -> True
"Mewtwo" not in animaux_favoris   # -> True
```


```python
animaux_favoris = [ "girafe", "chenille", "lynx" ]
```


### Iteration

```python
for animal in animaux_favoris:
    print(animal + " est un de mes animaux préférés !")
```


### Iteration avec index

```python
print("Voici la liste de mes animaux préférés:")
for i, animal in enumerate(animaux_favoris):
    print(str(i+1) + " : " + animal)
```


```python
animaux_favoris = [ "girafe", "chenille", "lynx" ]
```


### Modification d'un élément

```python
animaux_favoris[1] = "papillon"
```

### Ajout à la suite, à la fin d'une liste

```python
animaux_favoris.append("coyote")
```

### Insertion, concatenation

```python
animaux_favoris.insert(1, "sanglier")
animaux_favoris += ["lion", "moineau"]
```


## Exemple de manip classique : filtrer une liste pour en construire une nouvelle

```python
animaux_favoris = [ "girafe", "chenille", "lynx" ]

# Création d'une liste vide
animaux_starting_with_c = []

# J'itère sur la liste de pokémons favoris
for animal in animaux_favoris:

   # Si le nom de l'animal actuel commence par c
   if animal.startswith("c"):

      # Je l'ajoute à la liste
      animaux_starting_with_d.append(animal)
```


À la fin, `animaux_starting_with_c` contient:

```python
["girafe"]
```


### Transformation de string en liste

```python
"Hello World".split()    -> ["Hello", "World"]
```

### Transformation de liste en string

```python
' | '.join(["a", "b", "c"])      -> "a | b | c"
```



# Les dictionnaires

> Une collection **non-ordonnée** (apriori) de **clefs** a qui sont associées des **valeurs**
{.is-success}


```python
phone_numbers = { "Alice":   "06 93 28 14 03",
                  "Bob":     "06 84 19 37 47",
                  "Charlie": "04 92 84 92 03"  }
```

## Accès à une valeur

```python
phone_numbers["Charlie"]        -> "04 92 84 92 03"
phone_numbers["Marius"]           -> KeyError !
phone_numbers.get("Marius", None) -> None
```

## Modification d'une entrée, ajout d'une nouvelle entrée

```python
phone_numbers["Charlie"] = "06 25 65 92 83"
phone_numbers["Deborah"] = "07 02 93 84 21"
```


## Tester qu'une clef est dans le dictionnaire

```python
"Marius" in phone_numbers    # -> False
"Bob" not in phone_numbers # -> False
```

```python
phone_numbers = { "Alice":   "06 93 28 14 03",
                  "Bob":     "06 84 19 37 47",
                  "Charlie": "04 92 84 92 03"  }
```

## Iteration sur les clefs

```python
for prenom in phone_numbers:     # Ou plus explicitement: phone_numbers.keys()
    print("Je connais le numéro de "+prenom)
```


## Iteration sur les valeurs

```python
for phone_number in phone_numbers.values():
    print("Quelqu'un a comme numéro " + phone_number)
```


## Iterations sur les clefs et valeurs

```python
for prenom, phone_number in phone_numbers.items():
    print("Le numéro de " + prenom + " est " + phone_number)
```


# Construction plus complexes

Liste de liste, liste de dict, dict de liste, dict de liste, ...

```python
contacts = { "Alice":  { "phone": "06 93 28 14 03",
                         "email": "alice@megacorp.eu" },

             "Bob":    { "phone": "06 84 19 37 47",
                         "email": "bob.peterson@havard.edu.uk" },

             "Charlie": { "phone": "04 92 84 92 03" } }
```


```python
contacts = { "Alice":  { "phone": "06 93 28 14 03",
                         "email": "alice@megacorp.eu" },

             "Bob":    { "phone": "06 84 19 37 47",
                         "email": "bob.peterson@harvard.edu.uk" },

             "Charlie": { "phone": "04 92 84 92 03" } }
```


## Recuperer le numero de Bob

```python
contacts["Bob"]["phone"]   # -> "06 84 19 37 47"
```


## Ajouter l'email de Charlie

```python
contacts["Charlie"]["email"] = "charlie@orange.fr"
```


## Ajouter Deborah avec juste une adresse mail

```python
contacts["Deborah"] = {"email": "deb@hotmail.fr"}
```



# Les sets

Les `set`s sont des collections d'éléments **unique** et **non-ordonnée**

```python
chat = set(["c", "h", "a", "t"])        # -> {'h', 'c', 'a', 't'}
chien = set(["c", "h", "i", "e", "n")   # -> {'c', 'e', 'i', 'n', 'h'}
chat - chien                            # -> {'a', 't'}
chien - chat                            # -> {'i', 'n', 'e'}
chat & chien                            # -> {'h', 'c'}
chat | chien                            # -> {'c', 't', 'e', 'a', 'i', 'n', 'h'}
chat.add("z")                           # ajoute `z` à `chat`
```



# Les tuples

Les tuples permettent de stocker des données de manière similaire à une liste, mais de manière **non-mutable**.
Generalement itérer sur un tuple n'a pas vraiment de sens...

Les tuples permettent de **grouper des informations ensembles**.
Typiquement : des coordonnées de point.

```python
xyz = (2,3,5)
xyz[0]        # -> 2
xyz[1]        # -> 3
xyz[0] = 5    # -> Erreur!
```

Autre exemple `dictionnaire.items()` renvoie une liste de tuple `(clef, valeur)` :

```python
[ (clef1, valeur1), (clef2, valeur2), ... ]
```


## Générateurs

(Pas vraiment une structure de données, mais c'est lié aux boucles ...)

- Une fonction qui renvoie **des** résultats "au fur et à mesure" qu'ils sont demandés ...
- Se comporte comme un itérateur
- Peut ne jamais s'arrêter ...!
- Typiquement, évite de créer des listes intermédiaires


### exemple SANS generateur

```python
mes_animaux = { "girafe": 300,    "coyote": 50,
                 "chenille": 2,       "cobra": 45
                 # [...]
               }

def au_moins_un_metre(animaux):

    output = []
    for animal, taille in animaux.items():
        if taille >= 100:
            output.append(animal)

    return output

for animal in au_moins_un_metre(mes_animaux):
   ...
```

### exemple AVEC generateur

```python
mes_animaux = { "girafe": 300,    "coyote": 50,
                 "chenille": 2,       "cobra": 45
                 # [...]
               }

def au_moins_un_metre(animaux):

    for animal, taille in animaux.items():
        if taille >= 100:
            yield animal

for animal in au_moins_un_metre(mes_animaux):
   ...
```

Il n'est pas nécessaire de créer la liste intermédiaire `output`


### Un autre exemple

```python
def factorielle():

   n = 1
   acc = 1

   while True:
       acc *= n
       n += 1

       yield acc
```

### Ex Structures de données

0 : Écrire une fonction qui retourne le plus grand élément d'une liste (ou d'un set) de nombres, et une autre fonction qui retourne le plus petit. Par exemple, `plus_grand([5, 9, 12, 6, -1, 4])` retournera 12.

```python
plus_grand([5, 9, 12, 6, -1, 4]) == 12
plus_grand([-6, -19, -2]) == -2
plus_petit([5, 9, 12, 6, -1, 4]) == -1
plus_petit([-6, -19, -2]) == -19
```

1 : Écrire une fonction qui retourne le mot le plus long parmis une liste de mot donnée en argument.

```python
plus_long(["Paris", "Amsterdam", "Londres"]) == "Amsterdam"
plus_long(["Choucroute", "Pizza", "Tarte flambée"]) == "Tarte flambée"
```

2 : Écrire une fonction qui calcule la somme d'une liste de nombres.

```python
somme([3, 4, 5]) == 12
somme([0, 7, -3]) == 4
```

3 : Écrire une fonction qui retourne seulement les entiers pairs d'une liste

4 : Constituez une liste semaine contenant les 7 jours de la semaine. 

- À partir de cette liste, comment récupérez-vous seulement les 5 premiers jours de la semaine d'une part, et ceux du week-end d'autre part ? Utilisez pour cela l'indiçage. 

- Cherchez un autre moyen pour arriver au même résultat (en utilisant un autre indiçage). 

- Trouvez deux manières pour accéder au dernier jour de la semaine. 

- Inversez les jours de la semaine en une commande. 


5 : Créez 4 listes hiver, printemps, ete et automne contenant les mois correspondants à ces saisons. Créez ensuite une liste saisons contenant les listes hiver, printemps, ete et automne. Prévoyez ce que renvoient les instructions suivantes, puis vérifiez-le dans l'interpréteur : 

- saisons[2] 

- saisons[1][0] 

- saisons[1:2] 

- saisons[:][1]. Comment expliquez-vous ce dernier résultat ? 

6 : Affichez la table de multiplication par 9 en une seule commande avec les instructions range() et list(). 

7: Répondez à la question suivante en une seule commande. Combien y a-t-il de nombres pairs dans l'intervalle [2, 10000] inclus ? 

8 : Soit la liste de nombres [8, 3, 12.5, 45, 25.5, 52, 1]. Triez les nombres de cette liste par ordre croissant, sans utiliser la fonction sort(). Les fonctions et méthodes min(), .append() et .remove() vous seront utiles. 

9 : Soit la liste de nombres liste = [5, 1, 1, 2, 5, 6, 3, 4, 4, 4, 2]. 

À partir de liste, créez une nouvelle liste sans les doublons, triez-la et affichez-la. 

10 : Trouvez le nombre mystère qui répond aux conditions suivantes : 

- Il est composé de 3 chiffres. 
- Il est strictement inférieur à 300. 
- Il est pair. 
- Deux de ses chiffres sont identiques. 
- La somme de ses chiffres est égale à 7. 

On vous propose d'employer une méthode dite « brute force », c'est-à-dire d'utiliser une boucle et à chaque itération de tester les différentes conditions. 


11 : Voici le début du triangle de Pascal : 

```
1 
1 1 
1 2 1 
1 3 3 1 
1 4 6 4 1 
1 5 10 10 5 1 
[...] 
```

Déduisez comment une ligne est construite à partir de la précédente. Par exemple, à partir de la ligne 2 (1 1), construisez la ligne suivante (ligne 3 : 1 2 1) et ainsi de suite. 

Implémentez cette construction en Python. Généralisez à l'aide d'une boucle. 

11 : Utilisez le dictionnaire `example_dict` et boucler sur ce dictionnaire pour afficher quelque chose comme:

```python
Sebastian est né.e en 1979
Barclay est né.e en 2000
Vivien est né.e en 1955

example_dict=[{'name': 'Sebastian', 'email': 'Donec.felis.orci@consectetueripsumnunc.edu', 'country': '1979'}, {'name': 'Barclay', 'email': 'aliquet.metus.urna@neceleifend.co.uk', 'country': '2000'}, {'name': 'Vivien', 'email': 'pharetra@a.com', 'country': '1955'}, {'name': 'Britanney', 'email': 'eu.tellus.Phasellus@arcuvelquam.ca', 'country': '1961'}, {'name': 'Reese', 'email': 'tortor.dictum.eu@egestasSed.ca', 'country': '1951'}, {'name': 'Keegan', 'email': 'libero.nec@cursuset.co.uk', 'country': '1998'}, {'name': 'Ezekiel', 'email': 'tempus.mauris.erat@aclibero.org', 'country': '1951'}, {'name': 'Odessa', 'email': 'massa.Quisque.porttitor@felis.net', 'country': '1925'}, {'name': 'Elijah', 'email': 'luctus.vulputate.nisi@nunc.com', 'country': '1963'}, {'name': 'Hilel', 'email': 'lectus.pede.et@aliquetsem.ca', 'country': '1982'}, {'name': 'Callie', 'email': 'et.euismod.et@aliquetmagnaa.net', 'country': '1984'}, {'name': 'India', 'email': 'Duis.sit.amet@Phaselluslibero.com', 'country': '1938'}, {'name': 'Lane', 'email': 'amet@turpis.ca', 'country': '1922'}, {'name': 'Alexis', 'email': 'sagittis.placerat@nibhdolor.net', 'country': '1927'}, {'name': 'Micah', 'email': 'lorem.eget.mollis@SeddictumProin.com', 'country': '1914'}, {'name': 'Rigel', 'email': 'sollicitudin@eratinconsectetuer.org', 'country': '1941'}, {'name': 'Avram', 'email': 'tincidunt.vehicula@vulputate.org', 'country': '1919'}, {'name': 'Dieter', 'email': 'ornare.lectus.justo@Integeridmagna.org', 'country': '1937'}, {'name': 'Sarah', 'email': 'cubilia.Curae.Phasellus@non.net', 'country': '1946'}, {'name': 'Graham', 'email': 'elit.Curabitur.sed@maurisIntegersem.edu', 'country': '1931'}, {'name': 'Daquan', 'email': 'fermentum.convallis.ligula@porttitorinterdum.co.uk', 'country': '1934'}, {'name': 'Nell', 'email': 'purus@lectusconvallisest.org', 'country': '1997'}, {'name': 'Ocean', 'email': 'ut@Nuncquisarcu.net', 'country': '2006'}, {'name': 'Cruz', 'email': 'Aenean.euismod.mauris@idmollisnec.edu', 'country': '1950'}, {'name': 'Hyacinth', 'email': 'amet@Nunc.edu', 'country': '1929'}]
```

12 : Transformer le programme précédent pour n'afficher que les personnes ayant une adresse mail finissant par `.edu`.

13 : Ecrire une fonction `compte_lettres` qui prends en argument une (grande) chaîne de caractère et retourne un dictionnaire avec un compte des occurences des lettres. Par exemple `compte_lettres("hello")` retournera `{"h":1, "l": 2, "o": 1, "e":1 }`. Utiliser cette fonction sur Lorem Ipsum ("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt [...]")

