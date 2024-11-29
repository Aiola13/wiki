---
title: Les fonctions
description: 
published: 1
date: 2024-11-29T00:47:47.096Z
tags: fonctions, functions, php
editor: markdown
dateCreated: 2023-01-18T21:13:47.816Z
---

# Les fonctions

> Quelle surprise 😮 ! Le php permet aussi l'écriture de fonctions.
> Elles peuvent : 
> - prendre des arguments
> - renvoyer une valeur
> - être flexibles par rapport à son prototypage (nbr de paramètre)
> 
> ‎
{.is-success}

```php
<?php
// Cette fonction prend un nombre en entrée, lui ajoute 15 puis 10 et retourne le résultat
function maFonction($toto)
{
  $toto += 15;
  return ($toto + 10);
}
echo maFonction(120).'<br />'; // Affiche 155
?>
```

## Définition & Prototypage

### Valeur par défaut des arguments

> Les valeurs par défaut des arguments permettent de rendre la fonction plus flexible et d'éviter des erreurs si certains arguments ne sont pas fournis lors de l'appel.
{.is-success}


```php
<?php

function setColor($color = "black")
{
  echo $color.'<br />';
}

//appel de la fonction

$sCouleur = 'red';
setColor(); // sans valeur de paramètre => Retourne Black
setColor('rouge'); // retourne rouge
setColor($sCouleur); // passage de la variable en paramètre => retourne red
?>
```

### Passage de paramètre par référence


```php
<?php

function change(&$var) // force le passage systématique par référence
{
  $var += 100; // incrémentation de +100
}

$iNbr = 12; // vaut 12
change($iNbr); // la variable est passée par référence, permettant à la fonction de modifier sa valeur originale
echo $iNbr; // vaut donc 112
?>
```


### Retour de plusieurs valeurs par une fonction

Nous avons vu en algo, que pour récupérer plusieurs valeurs retours d'une fonction, on utilisait un tableau. 
Il y a un autre moyen, la procédure `list()`.

```php
<?php

function trigo($iNbr) 
{
  return array(sin($iNbr), cos($iNbr), tan($iNbr)); // retourne un tableau
}

$rRayon = 12;
list($a, $b, $c) = trigo($rRayon); // affectation de chaque valeur du tableau dans des variables

echo "sin($rRayon)=$a, cos($rRayon)=$b, tan($rRayon)=$c";
?>
```


### Retour dans un type donné (PHP 7)

Comme expliqué plus haut, avec PHP 7 nous pouvons explicitement demandé que la fonction nous retourne un type donné.

```php
<?php
// Active le mode strict pour la vérification des types
// Cela signifie que PHP sera plus strict sur les types de données - les arguments passés
// à une fonction et les valeurs de retour de cette fonction doivent correspondre exactement aux types déclarés.
declare(strict_types=1); 

// Définit une fonction nommée 'addition' qui prend deux paramètres, $x et $y, tous deux de type 'int' (entier),
// et retourne un résultat également de type 'int'.
// La déclaration ': int' après les parenthèses indique le type de la valeur retournée par la fonction.
function addition(int $x, int $y):int
{
  return $x + $y;
}

echo addition(2, 5);
?>
```

# Prêt pour la prochaine partie ? 😉 [C'est par ici](./Objets.md)