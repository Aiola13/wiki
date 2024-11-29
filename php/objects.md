---
title: Les objets
description: 
published: 1
date: 2024-11-29T00:48:42.695Z
tags: objects, objets, php
editor: markdown
dateCreated: 2023-01-18T21:14:31.673Z
---

# La programmation Orientée Objet (POO)

## Mais qu'est-ce que sont les objets ? 🙄

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


## Qu'est-ce-qu'une classe alors ? 

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


## Mais concrètement, une classe, c'est quoi ?

> Une classe est **une entité** regroupant **des variables** (appelées **propriétés**, **attributs** ou/et **variables membres**) et **des fonctions** (appelées **méthodes**). Chacune de ces méthodes aura accès aux propriétés de cette entité. Dans le cas de la voiture, nous aurons une méthode peindre(). Cette fonction devra simplement modifier la propriété $couleur.
{.is-success}


> ## Exercice 1
> 
> Une voiture, comment pourrait-on définir une voiture ?
{.is-info}


## Pourquoi coder avec des objets et des class ? 

> **POO** (en anglais **OOP**) est l'abréviation de **Programmation Orientée Objet** (**Object-Oriented Programming**).
{.is-success}

> La programmation procédurale (non POO) consiste à écrire des procédures ou des
> fonctions qui effectuent des opérations sur les données, tandis que la programmation
> orientée objet consiste à créer des objets qui contiennent à la fois des données et des
> fonctions.
{.is-success}

> La POO présente plusieurs avantages par rapport à la programmation procédurale :
> - La POO est plus rapide et plus facile à exécuter
> - La POO fournit une structure claire pour les programmes
> - La POO aide à garder le code PHP DRY "Don't Repeat Yourself", et rend le code plus facile à maintenir, à modifier et à déboguer.
> - La POO permet de créer des applications entièrement réutilisables avec moins de code et un temps de développement plus court.
> 
> ‎ 
{.is-info}


> Rappel : le principe "Don't Repeat Yourself" (DRY) consiste à réduire la répétition du code.
> Vous devez extraire les codes qui sont communs à l'application, les placer à un seul endroit et les réutiliser au lieu de les répéter.
> 
> ‎ 
{.is-info}




## Convention de nommage

| Instructions          | How to write                | Exemple               |
| --------------------- | --------------------------- | --------------------- |
| Classes & Interfaces  | PascalCase (UpperCamelCase) | Car.php               |
| Méthodes et Variables | camelCase                   | getColor() / carColor |
| Constantes            | UpperCase                   | ALL_CAPS              |


> Méthodes et Variables : Alphanumériques uniquement, à l'exception de '\_' comme décrit ici. Les noms doivent décrire les données dans la variable ou le comportement de la méthode. Les variables ou méthodes déclarées avec des modificateurs de visibilité privé ou protégé doivent commencer par un \_.
{.is-info}


> Constantes : Alphanumériques et '\_' sont autorisés cependant '\_' doit être utilisé pour séparer les mots dans des constantes.
{.is-info}

## Déclaration d'une classe

> Une classe est déclarée grâce au mot-clé **class** suivi du nom de la classe (ce nom commence toujours par une majuscule)
> Toutes ses propriétés et méthodes sont placées à l'intérieur des accolades
{.is-success}

```php
<?php
  class Voiture // Déclaration de la classe Voiture
  {
  	// Code de la classe
  }
?>
```

```php
<?php
  class Fruit // Déclaration de la classe Fruit
  {
  	// Code de la classe
  }
?>
```


## Définition d'une classe

> La définition d'une classe implique de spécifier en détail les propriétés et les méthodes de la classe :
{.is-success}


<!--
```php
<?php
  class Voiture // Déclaration de la classe
  {
    // Déclaration des données membres (Private, Public & Protected)
    private $_couleur; // Déclaaration d'un attribut
    private $_type = "sport"; // initialisation de la donnée membre
    private $_marque; // initialisation de la donnée membre

    // Déclaration des fonctions membres (Méthodes)
    public function __construct($marque) // Constructeur
    {
      $this->_couleur = "noire";
      $this->_marque = $marque;
      // Le mot-clé "$this" faisant référence à l'objet est obligatoire
    }

    public function setCouleur($couleur)
    {
      $this->_couleur = $couleur;
    }

    public function getCouleur()
    {
      return $this->_couleur;
    }
  }
?>
```
-->


```php
<?php
  class Voiture // Déclaration de la classe
  {
    // Déclaration des données membres
    private $_couleur; // Déclaaration d'un attribut

		// Déclaration des méthodes
    public function getCouleur()
    {
      return $this->_couleur;
    }
  }
?>
```


```php
<?php
  class Fruit // Déclaration de la classe
  {
   	// Déclaration des propriétés
    public $name;
    public $color;
    
    // Méthodes
    function setName($name) {
    	$this->name = $name;
    }
    
    function getName() {
    	return $this->name;
    }
  }
?>
```

> ## Exercice 2
> Reprendre la classe Fruit de l’exemple, et ajouter deux méthodes supplémentaires pour
définir et obtenir la couleur.
{.is-info}

## Instanciation

> Maintenant que vous savez ce qu'est un objet et une classe, parlons de **l'instanciation** ...
{.is-warning}


> **L'instanciation** est le fait de créer un objet via une classe, ce qui créé une instance de la classe dont elle dépend. 
> Chaque objet possède toutes les propriétés et méthodes définies dans la classe,
> mais ils auront des valeurs de propriétés différentes.
> Les objets d'une classe sont créés à l'aide du mot-clé **new**.
{.is-success}



```php
<?php
$maVoiture = new Voiture("Infinity");
echo 'couleur de la voiture '.$maVoiture->getCouleur().'<br />';

// -> opérateur Objet
$maVoiture->setCouleur("blanche"); // appel d'une méthode
echo 'couleur de la voiture '.$maVoiture->getCouleur().'<br />';
?>
```

```php
<?php
$apple = new Fruit();
$banana = new Fruit();
$apple->setName('Apple');
$banana->setName('Banana');
echo $apple->getName();
echo "<br>";
echo $banana->getName();
?>
```


> ## Exercice 3
> Un véhicule possède les propriétés suivantes : marque, modèle, puissance, couleur. Créer
la classe Véhicule, et ajouter les propriétés et les méthodes permettant de les définir et d’y
accéder. Instancier deux objets appartenant à la classe Véhicule.
{.is-info}


## La pseudo-variable *$this*

> Le mot-clé $this est une pseudo-variable qui fait référence à l'objet courant, et n'est disponible qu'à l'intérieur des méthodes. 
{.is-success}

<!--
- Accès aux Propriétés de l'Objet : $this permet à une méthode d'accéder aux propriétés de l'instance de la classe dans laquelle elle est définie. Sans $this, il serait impossible pour les méthodes de savoir à quelles propriétés de l'objet elles doivent accéder, surtout lorsque plusieurs instances de la même classe existent et que chacune peut avoir des valeurs différentes pour ses propriétés.
- Appel des Méthodes de l'Objet : De la même manière que pour les propriétés, $this est utilisé pour appeler d'autres méthodes au sein de la même instance. Cela permet d'organiser le code en unités logiques qui peuvent interagir les unes avec les autres au sein d'un même objet, facilitant ainsi la réutilisation du code et sa maintenance.
- Clarté et Précision du Code : L'utilisation de $this clarifie le code en montrant explicitement que la propriété ou la méthode appartient à l'instance actuelle de la classe. Cela rend le code plus lisible et plus facile à comprendre, surtout pour quelqu'un d'autre ou lors d'une révision future du code.
- Distinction entre Variables Locales et Propriétés de l'Objet : Dans les méthodes d'une classe, il peut y avoir des variables locales qui ont le même nom que les propriétés de l'objet. L'utilisation de $this permet de distinguer clairement les propriétés de l'objet des variables locales de la méthode.
- Implémentation de l'Encapsulation : $this aide à mettre en pratique le principe d'encapsulation en programmation orientée objet. L'encapsulation permet de masquer les détails d'implémentation internes d'un objet et d'exposer uniquement ce qui est nécessaire à l'extérieur à travers des méthodes publiques, $this étant utilisé pour manipuler les données internes de l'objet.
-->

## Le constructeur

> **Un constructeur** est une méthode spéciale d'une classe qui est automatiquement appelée et permet d'initialiser les propriétés d'un objet lors de sa création.
En PHP, le constructeur est défini avec la méthode magique **__construct()**.
{.is-success}


```php
<?php
  class Fruit {
    public $name;
    public $color;
    
    function __construct($name) {
    	$this->name = $name;
  	}
    
    function get_name() {
    	return $this->name;
  	}
  }
  
  
  $apple = new Fruit("Apple");
  echo $apple->get_name();
 ?>
```

> ## Exercice 4
> Ecrire le constructeur de la classe Véhicule.
{.is-info}

## Le destructeur

> **Un destructeur** est une autre méthode spéciale qui est automatiquement appelée lorsqu'un objet est sur le point d'être détruit, c'est-à-dire lorsque toutes les références à un objet sont supprimées ou lorsque l'exécution du script se termine. Le destructeur est utile pour libérer des ressources ou effectuer certaines tâches de nettoyage juste avant que l'objet ne soit détruit. En PHP, le destructeur est défini avec la méthode magique **__destruct()**. 
{.is-success}

```php
<?php
  class Fruit {
    public $name;
    public $color;
    
    function __construct($name) {
    	$this->name = $name;
  	}
    
    function __destruct() {
			echo "The fruit is {$this->name}.";
		}
	}
  
  $apple = new Fruit("Apple");
 ?>
```

> ## Exercice 5
> Ecrire le destructeur de la classe Véhicule. Mettre en évidence son action.
{.is-info}


## L'Encapsulation et les Modificateurs d'accès / de visibilité

> On peut définir comment, où et par qui sont lu les propriétés et les méthodes.
> Cette action s'appelle **L'encapsulation** et permet donc de rendre le code visible où non, en mettant en place une visibilité d'un attribut ou une méthode via 3 mots clés qui sont des modificateurs d'accès :
> - **public** : la propriété ou la méthode est accessible de partout. C'est le paramètre par défaut, mais aussi le moins sécurisé.
> - **protected** : la propriété ou la méthode est accessible à l'intérieur de la classe et par les classes dérivées de cette classe. (Nous abordons cette notions plus tard)
> - **private** : la propriété ou la méthode est accessible UNIQUEMENT au sein de la classe.
> 
> Nous l'appelons également "Visibilité" ou "Portée" des variables.
> 
> ‎ 
{.is-info}
{.is-success}

```php
<?php
  class Fruit {
    public $name;
    protected $color;
    private $weight;
    
    function set_name($n) { // une méthode publique (default)
    	$this->name = $n;
    }
    
    protected function set_color($n) {
    	$this->color = $n;
    }
    
    private function set_weight($n) {
    	$this->weight = $n;
    }
  }
  
  $mango = new Fruit();
  $mango->name = 'Mango'; // OK
  $mango->color = 'Yellow'; // ERROR
  $mango->weight = '300'; // ERROR
  $mango->set_name('Mango'); // OK
  $mango->set_color('Yellow'); // ERROR
  $mango->set_weight('300'); // ERROR
?>
```

> ## Exercice 6
> Modifiez votre classe Véhicule de la manière suivante : 
> - Marque et Modèle sont des propriétés privées, la puissance est protégée, et la couleur est publique.
> - Initialisez les propriétés avec un constructeur.
> - Modifiez la couleur sans créer de méthode. Que se passe-t-il?
> - Modifiez la puissance sans créer de méthode. Que se passe-t-il?
> - Modifiez la marque sans créer de méthode. Que se passe-t-il?
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
> Résultat attendu : seules 4 méthodes doivent être accessibles depuis l’extérieur, lesquelles
et pourquoi?
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



<!--
## Héritage
Mais qu'est-ce que l'héritage ? En sois, ce concepte n'est pas compliqué à comprendre. En effet, on reçoit tous l'héritage de nos ancêtres à un moment donné.
C'est la même idée ici. Vous pouvez créer des classes qui héritent d'autres classes.
Immaginons que vous ayez plusieurs voitures (il n'existe pas qu'une seule et unique sorte de voiture, sinon la vie serait bien platonique), il existe des voitures qui ont toutes les mêmes caractérisques de bases (couleur, marque), mais certaines voitures ont des spécificités. C'est le cas par exemple d'une voiture de Luxe qui est "Belle".
```php
<?php
  class VoitureLuxe extends Voiture // Déclaration de la sous-classe qui hérite de Voiture
  {
    
    private $_belle; 

    public function __construct() // constructeur de la classe VoitureLuxe
    {
      parent::__construct();  // :: Opérateur de résolution de portée, indiquant qu'on utilise le constructeur de la classe parent.
      $this->_belle=TRUE();
    }

   
  }
?>
```

L'opérateur de résolution de portée 
parent `::` membre de la classe parent
self `::` membre de la même classe

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

## Composition
La composition est le fait qu'une classe soit composé d'une autre classe. Simple ... non ? 🤔
Reprenons l'exemple d'une voiture, qui est composée de 4 roues. 

```php
<?php
 
class Roue 
{
   private $_diametre;
    private $_marque;
     
    public function __construct($marque, $diametre){
        $this->_marque=$marque;
        $this->_diametre=$diametre;
    }
     
    public function __toString(){
        return "Roue marque ".$this->_marque." et de diametre ".$this->_diametre."<br/>";
    }
}
 
class Voiture
{
    private $_roues;
 
    const AvantGauche   = 0;
    const AvantDroit    = 1;
    const ArriereGauche = 2;
    const ArriereDroit  = 3;
 
    //
 
    public function changerRoue($roue, $position)
    {
        $this->_roues[$position] = $roue;
    }
 
    public function getRoue($position)
    {
        return $this->_roues[$position];
    }
}
 
$voiture = new Voiture;
$voiture->changerRoue(new Roue("Dunlop", 60), Voiture::AvantGauche);
$voiture->changerRoue(new Roue("Michelin", 80), Voiture::ArriereGauche);
echo $voiture->getRoue(Voiture::ArriereGauche)->getMarque();
echo $voiture->getRoue(Voiture::AvantGauche)->getMarque();
```

## Static
Une propriété **static** est une propriété qui ne va pas appartenir à une instance particulière, mais à une classe dans la quelle elle a été définie.
Elle va donc avoir la même définition et la même valeur pour toutes les instances d'une classen et nous allons pouvoir y accéder sans avoir besoin d'instancier une classe.

Prenons l'exemple d'un Administrateur qui aurait une liste d'Utilisateur banni.

```php
<?php
    class Admin extends Utilisateur{
        protected static $_ban;
        public const ABONNEMENT = 5;
        
        public function __construct($n, $p, $r){
            $this->_user_name = strtoupper($n);
            $this->_user_pass = $p;
            $this->_user_region = $r;
        }
        
        public function setBan(...$b){
            foreach($b as $banned){
                self::$_ban[] .= $banned;
            }
        }
        public function getBan(){
            echo 'Utilisateurs bannis : ';
            foreach(self::$ban as $valeur){
                echo $valeur .', ';
            }
        }
        
        public function setPrixAbo(){
            if($this->_user_region === 'Sud'){
                return $this->_prix_abo = self::ABONNEMENT;
            }else{
                return $this->_prix_abo = parent::ABONNEMENT / 2;
            }
        }
    }
?>

```
-->

---
# Prêt pour la prochaine partie ? 😉 [C'est par ici](/php/plus)