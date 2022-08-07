---
title: Les fonctions
description: 
published: 1
date: 2022-08-07T15:29:31.652Z
tags: 
editor: markdown
dateCreated: 2022-08-07T15:29:31.652Z
---

# Les fonctions

Quelle surprise 😮 ! Le php permet aussi l'écriture de fonctions.
Elle peuvent : 
- prendre des arguments
- renvoyer une valeur
- ne pas respecter son prototypage (nbr de paramètre)

```php
<?php

function maFonction($toto)
{
  $toto += 15;
  return ($toto + 10);
}
echo maFonction(120).'<br />';
?>
```

## Prototypage

### Valeur par défaut des arguments

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
change($iNbr); //passage par valeur, mais la fonction la prend en référence
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
list($a, $b, $c) = trigo($iRayon); // affectation de chaque valeur du tableau dans des variables

echo "sin($rRayon)=$a, cos($rRayon)=$b, tan($rRayon)=$c";
?>
```


### Retour dans un type donné (PHP 7)

Comme expliqué plus haut, avec PHP 7 nous pouvons explicitement demandé que la fonction nous retourne un type donné.

```php
<?php
declare(strict_types=1); 

function addition(int $x, int $y):int
{
  return $x + $y;
}

echo addition(2, 5);
?>
```

# Prêt pour la prochaine partie ? 😉 [C'est par ici](./Objets.md)