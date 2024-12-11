---
title: La gestion de fichier
description: 
published: true
date: 2024-12-11T08:29:06.614Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:29:06.614Z
---

> Une grande partie de l'information est stockée sous forme de texte dans des fichiers. Pour traiter cette information, vous devez le plus souvent lire ou écrire dans un ou plusieurs fichiers. Python possède pour cela de nombreux outils qui vous simplifient la vie.
{.is-success}

# Lire

Prenons l'exemple d'un fichier **"zoo.txt"** comprenant : 

```txt
girafe
tigre
singe
souris
```

## Lire "brutalement" | la méthode `readlines()`

```python
mon_fichier = open("zoo.txt", "r") # -> Ouvre le fichier en lecture seule
contenu_du_fichier = mon_fichier.readlines() # -> enregistre le contenu du fichier dans une variable
mon_fichier.close() # -> Ferme le fichier

for ligne in contenu_du_fichier:
    print(ligne)
```

Attention à bien distinguer:

- le nom du fichier (`zoo.txt`) et son chemin d'accès absolu (``)
- le vrai fichier qui existe sur le disque
- la variable / objet Python (dans l'exemple, nommée `mon_fichier`) qui est une interface pour interagir avec ce fichier
- la fonction open() ouvre seulement le fichier (un peu comme lorsqu'on ouvre un livre, mais qu'on ne l'a pas encore lu)


## Lire, avec une "gestion de contexte"

```python
with open("zoo.txt", "r") as mon_fichier:
    contenu_du_fichier = mon_fichier.readlines()

for ligne in contenu_du_fichier:
    print(ligne)
```

### Explications

- `open("fichier", "r")` ouvre un fichier en lecture
- `with ... as ...` ouvre un contexte, à la fin duquel le fichier sera fermé automatiquement
- `mon_fichier.readlines()` permet d'obtenir une liste de toutes les lignes du fichier

<details> 
  <summary>Que sont les "contextes ?"</summary>

L'instruction with repose sur le protocole de gestion des contextes, qui est défini par deux méthodes spéciales : __enter__ et __exit__.

Un objet implémentant ces deux méthodes est appelé un objet de contexte.

Lorsqu'un objet de contexte est utilisé dans une déclaration with, la méthode __enter__ est appelée au début du bloc, et la méthode __exit__ est appelée à la fin.

Prenons l'exemple d'un fichier :

```python
with open('mon_fichier.txt', 'r') as fichier:
    contenu = fichier.read()
```
  
Lorsque le bloc with commence, la méthode open est appelée, et retourne un objet fichier.

Cet objet implémente les méthodes __enter__ et __exit__.

La méthode __enter__ est alors appelée, et le fichier est ouvert.

À la fin du bloc with, la méthode __exit__ est appelée, et le fichier est fermé automatiquement.

Créer vos propres objets de contexteformat_paragraph La bonne nouvelle, c'est que vous pouvez créer vos propres objets de contexte en définissant les méthodes __enter__ et __exit__ dans votre classe.

Par exemple, voici comment créer un objet de contexte pour mesurer le temps d'exécution d'un bloc de code :

```python
import time

class Chronometre:
    def __enter__(self):
        self.debut = time.time()
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        self.fin = time.time()
        self.duree = self.fin - self.debut
        print(f"Temps écoulé : {self.duree:.2f} secondes")

with Chronometre() as chrono:
    # Bloc de code dont vous souhaitez mesurer le temps d'exécution
    liste = [i**2 for i in range(100000)]
```
Dans cet exemple, la méthode __enter__ enregistre l'heure de début, et la méthode __exit__ enregistre l'heure de fin et affiche la durée.

</details>

## Lire "délicatement" | la méthode `read()`

> Il existe d'autres méthodes que .readlines() pour lire (et manipuler) un fichier. Par exemple, la méthode .read() lit tout le contenu d'un fichier et renvoie une chaîne de caractères unique.
{.is-success}

```python
with open("zoo.txt", "r") as mon_fichier:
     mon_fichier.read() 									 # -> 'girafe\ntigre\nsinge\nsouris\n'
```

## Lire "délicatement" | la méthode `readline()`

> La méthode .readline() (sans s à la fin) lit une ligne d'un fichier et la renvoie sous forme de chaîne de caractères. À chaque nouvel appel de .readline(), la ligne suivante est renvoyée. Associée à la boucle while.
{.is-success}



```python
with open("zoo.txt", "r") as mon_fichier:
     ligne = mon_fichier.readline()
     while ligne != "":
         print(ligne)
         ligne = mon_fichier.readline()  	# -> girafe

																		# -> tigre

                                    # -> singe

                                    # -> souris
```



## Itérations directe sur le fichier

> Python essaie de vous faciliter la vie au maximum. Voici un moyen à la fois simple et élégant de parcourir un fichier.
{.is-success}


```python
with open("zoo.txt", "r") as mon_fichier:
     for ligne in mon_fichier:
         print(ligne)							# -> girafe

																		# -> tigre

                                    # -> singe

                                    # -> souris

```
> L'objet mon_fichier est « itérable », ainsi la boucle for va demander à Python d'aller lire le fichier ligne par ligne.
{.is-success}


## Lire de manière générale 




- `mon_fichier.readlines()` renvoie une **liste** contenant les lignes une par une
- `mon_fichier.readline()` renvoie une ligne du fichier à chaque appel.
- `mon_fichier.read()` renvoie une (grande) **chaîne** contenant toutes les lignes concaténées

- Attention, si je modifie la variable` ... je ne modifie pas vraiment le fichier sur le disque ! Pour cela, il faut explicitement demander à *écrire* dans le fichier.


# Ecrire

## En remplacant tout !

```python
with open("/home/alex/test", "w") as f:
    f.write("Plop")
```

## À la suite (« append »)

```python
with open("/home/alex/test", "a") as f:
    f.write("Plop")
```


# Fichiers et exceptions

```python
try:
    with open("/some/file", "r") as f:
        lines = f.readlines()
except:
    raise Exception("Impossible d'ouvrir le fichier en lecture !")
```



# Un autre exemple

```python
try:
    with open("/etc/shadow", "r") as f:
        lines = f.readlines()
except PermissionError:
    raise Exception("Pas le droit d'ouvrir le fichier !")
except FileNotFoundError:
    raise Exception("Ce fichier n'existe pas !")
```


# Récap des droits d'accès à un fichier

| Mode | Description                                                                                   |
|------|-----------------------------------------------------------------------------------------------|
| 'r'  | Ouvre le fichier en lecture seule. C'est le mode par défaut si aucun mode n'est spécifié.    |
| 'w'  | Ouvre le fichier en écriture seulement. Crée le fichier s'il n'existe pas ou le tronque.     |
| 'x'  | Crée un nouveau fichier et l'ouvre pour l'écriture. Échoue si le fichier existe déjà.         |
| 'a'  | Ouvre le fichier en écriture. Tout ce qui est écrit est ajouté à la fin sans tronquer le fichier. |
| 'b'  | Ouvre le fichier en mode binaire. Peut être combiné avec d'autres modes (ex: 'rb', 'wb').     |
| 't'  | Ouvre le fichier en mode texte (par défaut). Peut être combiné avec d'autres modes (ex: 'rt', 'wt'). |
| '+'  | Ouvre le fichier pour la mise à jour (lecture et écriture). Peut être combiné (ex: 'r+', 'w+'). |


# Exercices 1

> Lire une liste d'utilisateurs 
> Créer une fonction `liste_users` qui lit le fichier `liste_utilisateurs.txt` et affiche cette liste dans le terminal.
{.is-info}


```txt
Yuki
Ji-Hoon
Emily
Amina
Élise
Maximilian
Sofia
Carlos
Anastasia
Liam
Priya
Mingyu
Lara
Gustavo
Nour
Sven
Tariro
Finn
Anouk
Iker
```

# Exercices 2

> Moyenne des notes
> Le fichier notes.txt contient des notes obtenues par des étudiants pour un cours. Chaque ligne du fichier ne contient qu'une note.
> 
> Créer un fichier notes.txt.
{.is-info}


```txt
13.5
17
9.5
12
14
6
5.5
8.5
10.5
29
14
9
15.5
11.5
16
18
13
12.5
15.5
17
```

> Créez une fonction qui lit chaque ligne de ce fichier, extrait les notes sous forme de float et les stocke dans une liste.
{.is-info}

> Terminez le script en calculant et affichant la moyenne des notes.
{.is-info}


# Exercice 3

> Dans le code Python, écrire un modèle d'email comme:
{.is-info}


```python
modele = """
Bonjour {prenom} !
Voici en pièce jointe les billets pour votre voyage en train vers {destination}.
"""
```

> Ecrire une fonction `generer_email` qui remplace dans `modele` les chaines `{prenom}`et `{destination}` par des arguments fourni à la fonction, et enregistre le résultat dans un fichier `email_{prenom}.txt`. Par exemple, `generer_email("Alex", "Strasbourg")` générera le texte et sauvegardera le résultat dans `email_Alex.txt`.
{.is-info}


# Exercice 4

> Ouvrez un fichier CSV et écrivez un programme qui compte le nombre de lignes et le nombre de colonnes qu'il contient.
{.is-info}


```csv
1,2,3,4,5,6,7,8,9
3,3,3,3,3,3,3,3,3
5,5,5,5,5,5,5,5,5
7,7,7,7,7,7,7,7,7
9,9,9,9,9,9,9,9,9
```

# Exercice 5

> Écrivez une fonction qui prend en entrée un nom de fichier CSV et une valeur, et écrit la valeur dans une colonne donnée pour chaque ligne du fichier. La sixième colonne ne doit contenir que des “6”.
{.is-info}


# Exercice 6

> Ouvrez un fichier CSV et écrivez un programme qui calcule la somme des valeurs d'une colonne donnée.
{.is-info}



# Exercice 7 (Bonus)

> Écrivez un programme qui prend en entrée deux noms de fichiers textes, et qui compare le contenu des deux fichiers ligne par ligne. Le programme doit afficher le numéro de la première ligne où les deux fichiers diffèrent, ou un message indiquant que les fichiers sont identiques. Faites la comparaison avec le fichier txt et le csv, puis entre les versions d’origine de vos fichiers et celles qui ont été modifiées.
{.is-info}



# Exercice 8 : Application de cryptographie

> Objectif : 
> Disposer d’une application en mode console qui peut créer un fichier contenant des données cryptées OU qui peut décrypter un fichier.
> 
> Fonctionnement attendu : 
> Proposer un menu à l’utilisateur contenant les choix suivants : chiffrer un fichier / déchiffrer un fichier / sortir de l’application.
> - Chiffrer un fichier proposera de chiffrer un fichier et pour cela il demandera le chemin d'accès complet, le type de chiffrement parmi le chiffre de césar ou vigenère, puis la clef de chiffrement souhaitée, et enfin le chemin du nouveau fichier à créer.
> - Déchiffrer un fichier proposera de Déchiffrer un fichier, pour cela il demandera le chemin d’accès au fichier à déchiffrer, le type de chiffrement parmi le chiffre de césar ou vigenère, la clé de chiffrement et le chemin complet de sauvegarde du fichier chiffré.
> - Sortir de l’application mettra fin à l’application.
{.is-info}


