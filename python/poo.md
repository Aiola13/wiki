---
title: Les Classes et Objets : La POO
description: 
published: true
date: 2024-12-11T08:29:33.070Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:29:33.070Z
---

# Courte Introduction
> L’orienté objet est **un paradigme de programmation** inventé dans les années 80 et popularisé dans les années 90. Aujourd’hui il est incontournable bien qu’il commence aussi à être critiqué.
> 
> Il permet d’organiser un programme de façon standard et ainsi d’éviter des erreurs d’architectures comme **le spaghetti code**
{.is-success}


# Mais qu'est-ce que sont les objets ? 🙄

> Mais si, vous savez ce que c'est .... Si si réféchissez ... vous en avez tout autour de vous... un canapé, une table, une chaise ... Bous avez compris ...
> En programmation c'est la même chose. 
{.is-success}


> L'exemple que je peux vous donner c'est une voiture, imaginons dans notre code un Objet **VOITURE**.
> 
> Cette voiture à :
> - une couleur
> - une marque
> - un type ... 
> 
> ‎
{.is-info}

> Ses caractérisques correspondent à des valeurs, des variables.
> Mais elle a aussi des capacités, des actions qu'elle peut effectuer, comme être repeinte, être réparé, avancer, tourner ... ce qu'on nomme des **méthodes** (nom donné aux fonctions dans une classe).
> 
> Toutes ces informations sont contenues dans une **classe**.
{.is-success}


# Qu'est-ce-qu'une classe alors ? 

> Les classes contiennent **la définition des objets** que l'on va créer. 
{.is-success}


> Un exemple très simple : les gâteaux et leur moule. 
> Le moule est : 
>  - unique
>  - Il peut produire une quantité infinie de gâteaux. 
> 
> ‎ 
{.is-info}

 
> Dans ce cas-là, **les gâteaux sont les objets** et **le moule est la classe** : le moule va définir la forme du gâteau. La classe contient donc le plan de fabrication d'un objet et on peut s'en servir autant qu'on veut afin d'obtenir une infinité d'objets.
{.is-success}


# Mais concrètement, une classe, c'est quoi ?

> Une classe est **une entité** regroupant **des variables** (appelées **propriétés**, **attributs** ou/et **variables membres**) et **des fonctions** (appelées **méthodes**). Chacune de ces méthodes aura accès aux propriétés de cette entité. Dans le cas de la voiture, nous aurons une méthode peindre(). Cette fonction devra simplement modifier la propriété $couleur.
{.is-success}


> ## Exercice 1
> 
> Une voiture, comment pourrait-on définir une voiture ?
{.is-info}


# Pourquoi coder avec des objets et des class ? 

> **POO** (en anglais **OOP**) est l'abréviation de **Programmation Orientée Objet** (**Object-Oriented Programming**).
{.is-success}

> La programmation procédurale (non POO) consiste à écrire des procédures ou des
> fonctions qui effectuent des opérations sur les données, tandis que la programmation
> orientée objet consiste à créer des objets qui contiennent à la fois des données et des
> fonctions.
{.is-success}

> La POO présente plusieurs avantages par rapport à la programmation procédurale :
> - Elle est plus rapide et plus facile à exécuter
> - Elle fournit une structure claire pour les programmes
> - Elle aide à garder le code PHP DRY "Don't Repeat Yourself", et rend le code plus facile à maintenir, à modifier et à déboguer.
> - Elle permet de créer des applications entièrement réutilisables avec moins de code et un temps de développement plus court.
> 
> ‎ 
{.is-info}


> Rappel : le principe "Don't Repeat Yourself" (DRY) consiste à réduire la répétition du code.
> Vous devez extraire les codes qui sont communs à l'application, les placer à un seul endroit et les réutiliser au lieu de les répéter.
> 
> ‎ 
{.is-info}


<!--
La POO est critique pour garder un code structuré et compréhensible quand la complexité d’un projet augmente.

Rassembler ce qui va ensemble pour s’y retrouver
Maintenir les variables isolées à l’intérieur d’un “scope” pour évitées qu’elles ne soient modifiée n’importe quand et n’importe comment et qu’il y ai des conflits de nom.
Fournir une façon d’architecturer un programme que tout le monde connait à peu près
Fournir un moyen efficace de programmer en évitant la répétition et favorisant la réutilisation
Créer des “boîtes noires” utilisables sans connaître leur fonctionnement interne (bien et pas bien à la fois). C’est à dire une façon de se répartir le travail entre développeurs (chacun sa boîte qu’on maîtrise).
-->


# Convention de nommage

| Instructions          | How to write                | Exemple               |
| --------------------- | --------------------------- | --------------------- |
| Classes & Interfaces  | PascalCase (UpperCamelCase) | Car.php               |
| Méthodes et Variables | snake_case                  | get_color() 					|


> Méthodes et Variables : Alphanumériques uniquement, à l'exception de '\_' comme décrit ici. Les noms doivent décrire les données dans la variable ou le comportement de la méthode. Les variables ou méthodes déclarées avec des modificateurs de visibilité privé ou protégé doivent commencer par un \_.
{.is-info}


# Déclaration d'une classe

> Une classe est déclarée grâce au mot-clé **class** suivi du nom de la classe (ce nom commence toujours par une majuscule)
> Toutes ses propriétés et méthodes sont placées à l'intérieur des accolades
{.is-success}

```python
class Cercle:
```

# Définition d'une classe

> La définition d'une classe implique de spécifier en détail les propriétés et les méthodes de la classe :
{.is-success}


```python
class Circle:

   def __init__(self, center, radius, color="black", thickness=0.1): #center, 
       self.center = center 				#centre
       self.radius = radius 				#rayon
       self.color = color 					#color
       self.thickness = thickness 	#épaisseur

   def move(self, dx=0, dy=0):
       self.center = (self.center[0]+dx, self.center[1]+dy)
```

> ## Exercice 2
> Reprendre la classe Circle de l’exemple, et ajouter deux méthodes supplémentaires pour
définir et obtenir la couleur.
{.is-info}

# Instanciation

> Maintenant que vous savez ce qu'est un objet et une classe, parlons de **l'instanciation** ...
{.is-warning}


> **L'instanciation** est le fait de créer un objet via une classe, ce qui créé une instance de la classe dont elle dépend. 
> Chaque objet possède toutes les propriétés et méthodes définies dans la classe,
> mais ils auront des valeurs de propriétés différentes.
{.is-success}



```python
circle1 = Circle((3, 5), 2, "red")
circle2 = Circle((-4, 2), 6, "blue", thickness=1)

circle1.move(dy=2)
print(circle1.center)
```


> ## Exercice 3
> Un véhicule possède les propriétés suivantes : marque, modèle, puissance, couleur. Créer
la classe Véhicule, et ajouter les propriétés et les méthodes permettant de les définir et d’y
accéder. Instancier deux objets appartenant à la classe Véhicule.
{.is-info}


# La pseudo-variable *`self`*

> Le mot-clé **self** est une pseudo-variable (appelé aussi **variable d'instance**) qui fait référence à l'objet courant (l’objet en train d’être manipulé). Elle doit être passé en paramètre de toutes les méthodes de la classe, et n'est disponible qu'à l'intérieur de la classe. 
{.is-success}

<!--
- Accès aux Propriétés de l'Objet : $this permet à une méthode d'accéder aux propriétés de l'instance de la classe dans laquelle elle est définie. Sans $this, il serait impossible pour les méthodes de savoir à quelles propriétés de l'objet elles doivent accéder, surtout lorsque plusieurs instances de la même classe existent et que chacune peut avoir des valeurs différentes pour ses propriétés.
- Appel des Méthodes de l'Objet : De la même manière que pour les propriétés, $this est utilisé pour appeler d'autres méthodes au sein de la même instance. Cela permet d'organiser le code en unités logiques qui peuvent interagir les unes avec les autres au sein d'un même objet, facilitant ainsi la réutilisation du code et sa maintenance.
- Clarté et Précision du Code : L'utilisation de $this clarifie le code en montrant explicitement que la propriété ou la méthode appartient à l'instance actuelle de la classe. Cela rend le code plus lisible et plus facile à comprendre, surtout pour quelqu'un d'autre ou lors d'une révision future du code.
- Distinction entre Variables Locales et Propriétés de l'Objet : Dans les méthodes d'une classe, il peut y avoir des variables locales qui ont le même nom que les propriétés de l'objet. L'utilisation de $this permet de distinguer clairement les propriétés de l'objet des variables locales de la méthode.
- Implémentation de l'Encapsulation : $this aide à mettre en pratique le principe d'encapsulation en programmation orientée objet. L'encapsulation permet de masquer les détails d'implémentation internes d'un objet et d'exposer uniquement ce qui est nécessaire à l'extérieur à travers des méthodes publiques, $this étant utilisé pour manipuler les données internes de l'objet.
-->

<!-- https://www.docstring.fr/blog/la-verite-sur-self/ -->


# Le constructeur *`__init__`*

> **Un constructeur** est une méthode spéciale d'une classe qui est automatiquement appelée et permet d'initialiser les propriétés d'un objet lors de sa création.
En python, le constructeur est défini avec la méthode magique **\_\_init__**.
{.is-success}

<!--
__init__ et deplacer sont des méthodes. Elles agissent généralement sur les attributs de l’objet mais pas nécessairement.
Les attributs et méthodes de la classe sont “dans” chaque instance d’objet (ici chaque cercle). On dit que la classe est un namespace (ou espace de nom). Chaque variable centre est isolée dans son cercle et on peut donc réutiliser plusieurs fois le nom centre pour chaque cercle. Par contre pour y accéder on doit préciser le cercle concerné avec la syntaxe cercle1.centre.

De même on utilise les methodes en faisant un_objet.la_methode(...)
Attention à l’indentation !!
-->


```python
class Circle:

   def __init__(self, center, radius, color="black", thickness=0.1):
       self.center = center  # centre
       self.radius = radius  # rayon
       self.color = color  # color
       self.thickness = thickness  # épaisseur

   def move(self, dx=0, dy=0):
       self.center = (self.center[0]+dx, self.center[1]+dy)


circle1 = Circle((3, 5), 2, "red")
circle2 = Circle((-4, 2), 6, "blue", thickness=1)

```

> ## Exercice 4
> Ecrire le constructeur de la classe Véhicule.
{.is-info}

# Le destructeur *`__del__`*


> **Un destructeur** est une autre méthode spéciale qui est automatiquement appelée lorsqu'un objet est sur le point d'être détruit, c'est-à-dire lorsque toutes les références à un objet sont supprimées ou lorsque l'exécution du script se termine. Le destructeur est utile pour libérer des ressources ou effectuer certaines tâches de nettoyage juste avant que l'objet ne soit détruit. **En python, les destructeurs ne sont pas aussi nécessaires que en C++**, car Python dispose d'un ramasse-miettes qui gère automatiquement la gestion de la mémoire mais on peut le définir avec la méthode magique **\_\_del__**. 
{.is-success}

```python
class Circle:

   def __init__(self, center, radius, color="black", thickness=0.1):
       self.center = center  # centre
       self.radius = radius  # rayon
       self.color = color  # color
       self.thickness = thickness  # épaisseur

   def __del__(self):
        print("je suis le destructeur")
        
circle1 = Circle()
# Affichera à la fin du programme "je suis le destructeur"
```

> ## Exercice 5
> Ecrire le destructeur de la classe Véhicule. Mettre en évidence son action.
{.is-info}


# L'Encapsulation

> L'encapsulation est un concept qui permet de limiter l'accès à certaines données dans un objet, afin de les protéger. Autrement dit, on empêche l'accès direct à certains attributs d'un objet depuis l'extérieur de celui-ci.
> 
> Dans des langages comme C# ou PHP, on utilise le mot-clé private pour cacher ces données. Cependant, en Python, il n'existe pas de mot-clé private. À la place, les développeurs Python suivent une convention très simple : les attributs ou méthodes précédés d'un underscore _, comme _attribut, sont traités comme privés et ne devraient pas être utilisés directement hors de la classe.
> 
> Cela repose sur la responsabilité du développeur de respecter cette convention lorsqu'il travaille avec des objets.
{.is-success}

<!--Les développeurs pallient cette limite en appliquant un ensemble de règles de bon usage 
(voir par exemple : https://google.github.io/styleguide/pyguide.html). -->


> ## Exercice 6
> Modifiez votre classe Véhicule de la manière suivante : 
> - Marque et Modèle sont des propriétés privées, la puissance est protégée, et la couleur est publique.
> - Initialisez les propriétés avec un constructeur.
> - Modifiez la couleur sans créer de méthode. 
> - Modifiez la puissance sans créer de méthode. 
> - Modifiez la marque sans créer de méthode.
> - Créez des méthodes d’accès pour lire les propriétés depuis l’extérieur.
> 
> ‎ 
{.is-info}



> ## Exercice 7
> Créer une classe Légume avec les propriétés suivantes : nom, poids, poidsMur, legumeMur.
> Le poids initial est à 0, legumeMur est un booléen à false, les autres propriétés sont libres.
> - Ajouter une méthode arroser() qui augmente le poids.
> - Ajouter une méthode engrais() qui augmente le poids.
> - Créer une méthode qui augmente le poids, seulement si la plante portant le légume est arrosée, ou nourrie avec de l’engrais (modifier les fonctions précédentes).
> - Quand le poids dépasse le poids mûr, alors legumeMur devient vrai.
> - Créer une méthode qui permet de savoir si le légume est mûr, ou non.
> - Créer une méthode qui permet de connaître le poids actuel.
> Écrire un script qui utilise un objet un objet Légume, et permet de le faire grandir !
> Rendre ce script réutilisable pour cultiver plusieurs légumes.
> 
> ‎ 
{.is-info}


> ## Exercice 8
> Créer une classe Pokémon avec les propriétés suivantes :
> - name
> - type1
> - type2
> - attack
> - hp
> - defence
> Les valeurs de toutes ces propriétés sont libres.
> - Ajouter une méthode pour récupérer les types du pokémon
> - Ajouter une méthode pour récupérer les points de vie
> - Ajouter une méthode qui permet d'attaquer un autre pokémon
> - Faire en sorte qu'une méthode gère les hp
> Répéter l'action de faire combattre pour définir un gagnant.
> 
> ‎ 
{.is-info}

# L'héritage

> Mais qu'est-ce que l'héritage ? En sois, ce concepte n'est pas compliqué à comprendre. En effet, on reçoit tous l'héritage de nos ancêtres (des gènes) à un moment donné.
> C'est la même idée ici. Vous pouvez créer des classes qui héritent d'autres classes.
> Immaginons que vous ayez plusieurs voitures (il n'existe pas qu'une seule et unique sorte de voiture, sinon la vie serait bien platonique), il existe des voitures qui ont toutes les mêmes caractérisques de bases (couleur, marque), mais certaines voitures ont des spécificités. C'est le cas par exemple d'une voiture de Luxe qui est "Belle" ou une voiture Electrique qui est "Electrique" (vous l'avez pas vu venir).
{.is-success}


```python
  class Car:
    def __init__(self):
        # Initialisation spécifique à la classe Car
        pass

class LuxuryCar(Car):  # Déclaration de la sous-classe qui hérite de Car
    def __init__(self):  # Constructeur de la classe LuxuryCar
        super().__init__()  # Appel du constructeur de la classe parente
        self._beautiful = True  # Attribut privé (selon convention Python avec un seul underscore)


```

```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

class ElectricCar(Car):  # Hérite de Car
    def __init__(self, make, model, battery_size):
        super().__init__(make, model)
        self.battery_size = battery_size
```

```python
tesla = ElectricCar("Tesla", "Model S", 85)
print(tesla.make, tesla.model, tesla.battery_size)  # Affiche "Tesla Model S 85"
```

> ## Exercice 9
> En réutilisant la classe précédente, créer une sous-classe de Pokémon nommée FirePokemon pour les Pokémon de type feu :
> 
> Ajouter une propriété firePower qui représente la puissance de feu spéciale du Pokémon.
> Ajouter une méthode flameAttack qui utilise firePower pour infliger des dégâts supplémentaires basés sur le type du Pokémon attaqué.
> Créer une sous-classe de Pokémon nommée WaterPokemon pour les Pokémon de type eau :
> 
> Ajouter une propriété waterPower.
> Ajouter une méthode waterSplash qui utilise waterPower pour infliger des dégâts, avec des effets bonus contre les Pokémon de type feu.
> Créer une méthode displayInfo dans la classe Pokémon qui affiche toutes les informations du Pokémon, y compris les propriétés spécifiques des sous-classes.
> 
> Instancier quelques Pokémon de feu et d'eau, puis les faire combattre en utilisant leurs attaques spéciales pour voir qui est le plus fort.
> 
> ‎ 
{.is-info}


# La fonction **`super()`**

> La fonction super est généralement utilisée pour obtenir la classe parente sans avoir besoin de la nommer explicitement.
> 
> On l'utilise donc généralement pour faire de la délégation, notamment à l'intérieur de la méthode __init__ dans le cas d'une classe qui hérite d'une autre classe :
{.is-success}

```python
class Employee:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname

class Boss(Employee):
    def __init__(self, name, surname):
        # Sans super
        # Employee.__init__(self, name=name, surname=surname)
        super().__init__(name=name, surname=surname)
        self.big_boss = True
        
 
boss = Boss(name="John", surname="Smith")
print(boss.name, boss.surname)
```


On utilise ici super pour ne pas avoir à écrire explicitement le nom de la classe dont Boss hérite (ici, Employee).

La ligne :

```python
Employee.__init__(self, name=name, surname=surname)
```

Est donc équivalente à :

```python
super().__init__(name=name, surname=surname)
```

> À noter que cette fonction peut être utilisée en dehors de la méthode **\_\_init__**.
> 
> Par exemple dans le code ci-dessous, on **surcharge** la méthode parle de la classe Employee dans la classe Boss pour y ajouter un print.
{.is-warning}


On utilise la fonction super pour appeler la méthode parle de la classe parente :

```python
class Employee:
    def __init__(self, name, surname):
        self.name = name
        self.surname = surname

    def parle(self):
        print("Je m'appelle", self.name)

class Boss(Employee):
    def __init__(self, name, surname):
        # Sans super
        # Employee.__init__(self, name=name, surname=surname)
        super().__init__(name=name, surname=surname)
        self.big_boss = True

    def parle(self):
        super().parle()  # On pourrait à la place écrire Employee.parle(self)
        print("...et je suis le Boss 😎")

patrick = Employee(name="Patrick", surname="Tremblay")
boss = Boss(name="John", surname="Smith")

patrick.parle()
boss.parle()
```


# La Surcharge 

> On appelle **Surcharge** une propriété ou une méthode d'une classe lorsqu'on la redéfinit.
> Pour surcharger une méthode, il faut la redéclarer en utilisant le même nom.
{.is-success}

```python
class Utilisateur:
    def __init__(self, n, p):
        self._user_name = n
        self._user_pass = p

    def get_nom(self):
        # Méthode pour renvoyer le nom de l'utilisateur actuel.
        return self._user_name

class Admin(Utilisateur):
    def __init__(self, n, p):
        super().__init__(n, p)
        self._ban = []

    def get_nom(self):
        # Méthode surchargée qui renvoie le nom de l'administrateur en majuscules.
        return self._user_name.upper()

    def set_ban(self, b):
        self._ban.append(b)

    def get_ban(self):
        print(f'Utilisateurs bannis par {self._user_name}: ', end='')
        print(', '.join(self._ban))

# Example of usage:
admin = Admin("JohnDoe", "secret123")
admin.set_ban("user1")
admin.set_ban("user2")
admin.get_ban()

```

> ## Exercice 10
> En réutilisant les classes précédente, modifier la méthode d'attaque dans la classe Pokémon pour qu'elle prenne en compte le type de l'attaque
> Modifier la méthode d'attaque dans la classe Pokémon pour qu'elle prenne en compte le type de l'attaque.
> Faire combattre différents types de Pokémon
> ‎ 
{.is-info}


<!--
# La Composition et l'Agrégation




# Le Polymorphisme

```python
class Utilisateur:
    def __init__(self, n, p):
        self._user_name = n
        self._user_pass = p

    def get_nom(self):
        # Méthode pour renvoyer le nom de l'utilisateur actuel.
        return self._user_name

class Admin(Utilisateur):
    def __init__(self, n, p):
        super().__init__(n, p)
        self._ban = []

    def get_nom(self):
        # Méthode surchargée qui renvoie le nom de l'administrateur en majuscules.
        return self._user_name.upper()

    def set_ban(self, b):
        self._ban.append(b)

    def get_ban(self):
        print(f'Utilisateurs bannis par {self._user_name}: ', end='')
        print(', '.join(self._ban))

# Example of usage:
admin = Admin("JohnDoe", "secret123")
admin.set_ban("user1")
admin.set_ban("user2")
admin.get_ban()
```
-->
<!--
La fonction super est également utilisée de façon beaucoup plus complexe pour pouvoir manipuler le « MRO » (Method Resolution Order ou « ordre de résolution des méthodes » en français).

Si vous souhaitez en savoir plus sur cette utilisation de la fonction super, je vous recommande la lecture de cet excellent article.   https://www.stashofcode.fr/comment-marche-fonction-super-de-python/ -->

<!--
# Le Polymorphisme



## Surcharge
On appelle **Surcharge** une propriété ou une méthode d'une classe lorsqu'on la redéfinit.
Pour surcharger une méthode, il faut la redéclarer en utilisant le même nom, le même nombre de paramètre et qu'elle soit en public ou protected.

A noter tout de même, que la Surcharge dans les autres langages signifie écrirer différentes versions d'une même méthode avec un nombre différents de paramètres.

```php

<?php
    class Utilisateur{
        protected $_user_name;
        protected $_user_pass;
        
        public function __construct($n, $p){
            $this->_user_name = $n;
            $this->_user_pass = $p;
        }
        
        public function getNom(){ // Méthode getNom() qui renvoi le nom de l'utilisateur actuel
            return $this->_user_name;
        }
    }

    class Admin extends Utilisateur{
        protected $_ban;
        
        public function getNom(){ // Méthode getNom() surcharger, qui modifie légèrement son fonctionnement en renvoyant le nom de l'Admin en majuscule.
            return strtoupper($this->_user_name);
        }
        
        public function setBan($b){
            $this->_ban[] .= $b;
        }
        public function getBan(){
            echo 'Utilisateurs bannis par '.$this->_user_name. ' : ';
            foreach($this->_ban as $valeur){
                echo $valeur .', ';
            }
        }
    }
?>

```
-->