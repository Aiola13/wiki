---
title: Les tableaux | Arrays
description: 
published: 1
date: 2024-11-29T00:46:53.736Z
tags: array, php, tableaux
editor: markdown
dateCreated: 2023-01-18T21:12:06.462Z
---

# Les Tableaux

> En PHP, les tableaux : 
> - sont dynamiques, leur taille peut évoluer.
> - peuvent contenir des éléments de types différents
> 
> ‎
{.is-info}


> Il existe deux types de tableaux ...


## Les Tableaux Indicés (index)

> C'est une liste d'éléments repérés par une position unique, son indice commençant par zéro.
{.is-success}


### Déclaration

#### Initialisation avec la syntaxe `array`

```php
$tCouleurs = array("rouge", "vert", "bleu");
$t = array("Texte", 2020, 20.5, $nom);
```
#### Initialisation avec la syntaxe courte

```php
$tMarques = ["Ford", "MG", "Seat", "Tesla", "Volkswagen"];
```
#### Initialisation au fut et à mesure :beer:

```php
$tPrenoms[] = "Julien";
$tPrenoms[] = "Mike";
$tPrenoms[] = "Loïc";

$tNom[0] = "Emeriau";
$tNom[1] = "Payet";
$tNom[2] = "Durand";
```

### Parcours

Un tableau peut être parcouru grâce aux boucles vus précédemment.
Cependant il existe une boucle particulièrement interessante : `Foreach`

```php
$tab= array("Ottawa", "Montréal", "Québec", "Chicoutimi");

foreach($tab as $element)
{
  echo $element.'<br />';
}
```

La variable `$element` prend pour valeurs successives tous les éléments du tableau *tab

### Quelques fonctions

|             Fonctions              |                     Utilisation                      |
| :--------------------------------: | :--------------------------------------------------: |
|           `count($tab)`            |       retourne le nombre d'éléments du tableau       |
|       `in_array($var, $tab)`       | renvoi `VRAI` si la valeur `$var` existe dans `$tab` |
|            `sort($tab)`            |     trie alphanumérique des éléments du tableau      |
| `array_merge($tab1, $tab2, $tab3)` |         concatène les tableaux en arguments          |
|         `array_rand($tab)`         |            retourne un élément au hasard             |

```php
// count()
$tab = ["Ottawa", "Montréal", "Québec"];
echo count($tab); // Affichera 3

// in_array()
$tab = ["rouge", "vert", "bleu"];
$couleur = "rouge";
if (in_array($couleur, $tab)) {
    echo "$couleur se trouve dans le tableau";
}

//sort()
$tab = ["Ottawa", "Montréal", "Québec"];
sort($tab);
print_r($tab); // Les villes seront triées alphabétiquement

//array_merge()
$tab1 = ["rouge", "vert"];
$tab2 = ["bleu", "jaune"];
$tab3 = ["violet", "orange"];
$result = array_merge($tab1, $tab2, $tab3);
print_r($result); // Fusionnera tous les tableaux en un seul

// array_rand()
$tab = ["rouge", "vert", "bleu", "jaune"];
$cle = array_rand($tab);
echo $tab[$cle]; // Affichera une couleur aléatoire du tableau
```

## Les Tableaux Associatifs

> C'est une liste d'éléments repérés par un identifiant arbitraire unique appelé **clé** qui est de type `string`.
> Il est aussi appelé _dictionaire_ ou _hashtable_ en PHP.
{.is-success}

<!-- https://stackoverflow.com/questions/3134296/hash-tables-vs-associative-arrays -->

### Déclaration

```php
//Syntaxe pseudo-code
$tableau = array[key => value];
$tableau[key] = value;

//Exemple 1
$tPersonne = array("Nom" => "Durand", "Prenom" => "Loïc");

//Exemple 2
$tPersonne["Nom"] = "Durand";
$tPersonne["Prenom"] = "Loïc";
```

### Parcours

```php
$tPersonne = array("Nom" => "Durand", "Prenom" => "Loïc");

//Exemple 1
foreach($tPersonne as $element)
{
  echo $element.'<br />';
}
// Ici on accède directement aux éléments du tableau sans passer par les clés.

//Exemple 2
foreach($tPersonne as $key => $element)
{
  echo $key.' : '.$element.'<br />';
}
// Ici on accède simultanément aux clés et aux éléments du tableau.
```

La variable `$element` prend pour valeurs successives tous les éléments du tableau *tab

### Quelques fonctions

|         Fonctions          |                                     Utilisation                                      |
| :------------------------: | :----------------------------------------------------------------------------------: |
| `array_count_values($tab)` | retourne un tableau contenant les valeurs comme clés et leurs fréquence comme valeur |
|     `array_keys($tab)`     |                  retourne un tableau contenant les clés du tableau                   |
|    `array_values($tab)`    |                 retourne un tableau contenant les valeurs du tableau                 |
| `array_search($val, $tab)` |                     retourne la clé associée à la valeur `$val`                      |

```php
// array_count_values()
$tab = ["a", "b", "a", "c", "b", "a"];
print_r(array_count_values($tab));
// Affichera Array ( [a] => 3, [b] => 2, [c] => 1 )

// array_keys()
$tab = ["Nom" => "Durand", "Prenom" => "Loïc"];
print_r(array_keys($tab));
// Affichera Array ( [0] => Nom, [1] => Prenom )

// array_values()
$tab = ["Nom" => "Durand", "Prenom" => "Loïc"];
print_r(array_values($tab));
// Affichera Array ( [0] => Durand, [1] => Loïc )

// array_search()
$tab = ["Nom" => "Durand", "Prenom" => "Loïc"];
$cle = array_search("Loïc", $tab);
echo $cle; // Affichera 'Prenom'

```

## BONUS - Les Tableaux à n dimensions

> Les tableaux à `n dimensions` référe à la capacité de structurer des données en plusieurs niveaux de profondeur. Un tableau à "n dimensions" peut être pensé comme un tableau de tableaux (de tableaux, et ainsi de suite, selon le nombre de dimensions). Chaque niveau de profondeur représente une nouvelle dimension. Les tableaux unidimensionnels (1D) contiennent des éléments simples, les tableaux bidimensionnels (2D) contiennent des tableaux de tableaux, et cela continue à augmenter en profondeur avec chaque dimension supplémentaire.
{.is-success}

### Construction

```php
$tDep[13] = array("Marseille", "Aix", "Arles", "Salon");
$tDep[84] = array("Avignon", "Orange", "Carpentras", "Cavaillon");
$tDep[30] = array("Nîmes", "Alès", "Bagnols-sur-Cèze", "Beaucaire");
```

### Parcours

```php
foreach($tDep as $dep => $tVille)
{
  echo '<p><em>'.$dep.'</em><br />';
  foreach($tVille as $ville)
  {
    echo $ville.'<br />';
  }
  echo '</p>';
}
```

### Visuel {.tabset}
#### Visuel
```
  Array
  {
    [13] => Array
      {
        [0] => Marseille
        [1] => Arles
        [2] => Aix
        [3] => Salon
      }

    [84] => Array
      {
        [0] => Avignon
        [1] => Orange
        [2] => Carpentras
        [3] => Cavaillon
      }

    [30] => Array
      {
        [0] => Nîmes
        [1] => Alès
        [2] => Bagnols-sur-Cèze
        [3] => Beaucaire
      }
  }
  ```

#### Résultat
	|                  |
  | ---------------- |
  | **13**           |
  | Marseille        |
  | Arles            |
  | Aix              |
  | Salon            |
  |                  |
  | **84**           |
  | Avignon          |
  | Orange           |
  | Carpentras       |
  | Cavaillon        |
  |                  |
  | **30**           |
  | Nîmes            |
  | Alès             |
  | Bagnols-sur-Cèze |
  | Beaucaire        |


#### Autres exemples 

##### Jours spéciaux

```php
$donnees = [
    2023 => [
        "Janvier" => ["01" => "Nouvel An", "06" => "Épiphanie"],
        "Février" => ["14" => "Saint-Valentin"]
    ],
    2024 => [
        "Janvier" => ["01" => "Nouvel An"]
    ]
];

foreach ($donnees as $annee => $mois) {
    echo "Année: $annee\n";
    foreach ($mois as $nomMois => $jours) {
        echo "\tMois: $nomMois\n";
        foreach ($jours as $jour => $evenement) {
            echo "\t\t$jour: $evenement\n";
        }
    }
}
```

##### Horaires cinéma

```php
$cineInfos = [
    "Paris" => [
        "Salle 1" => [
            "10:00" => "Film A",
            "13:00" => "Film B",
            "16:00" => "Film C"
        ],
        "Salle 2" => [
            "11:00" => "Film D",
            "14:00" => "Film E"
        ]
    ],
    "Lyon" => [
        "Salle 1" => [
            "10:30" => "Film A",
            "13:30" => "Film F"
        ],
        "Salle 3" => [
            "12:00" => "Film G",
            "15:00" => "Film H"
        ]
    ]
];
```

# Les tableaux Globaux

> Ces tableaux sont particuliers à PHP, ils seront définies dans la prochaine partie.
{.is-info}


|    Array    |                                        Utilisation                                        |       Exemple        |
| :---------: | :---------------------------------------------------------------------------------------: | :------------------: |
| `$GLOBALS`  | Contient une référence sur chaque variable, les clés sont les noms des variables globales |   $GLOBALS['var1']    |
| `$_SERVER`  |        Les variables fournies par le serveur, ou liées à l'environnement du scirpt        | $_SERVER['PHP_SELF'] |
|   `$_GET`   |       Les variables fournies au script via la chaîne de requête URL en méthode GET        |     $_GET['id']      |
|  `$_POST`   |       Les variables fournies au script via la chaîne de requête URL en méthode POST       |    $_POST['nom']     |
|  `$_FILES`  |          Les variables fournies par le protocole HTTP suite à un téléchargement           | $_FILES['fichier1']  |
| `$_SESSION` |               Les variables enregistrées dans la session attachée au script               |  $_SESSION['var2']   |

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/php/superglobal)