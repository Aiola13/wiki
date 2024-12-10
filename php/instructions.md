---
title: Instructions
description: 
published: true
date: 2024-12-10T20:34:35.395Z
tags: php, instructions, instruction
editor: markdown
dateCreated: 2024-12-10T20:34:35.395Z
---

# Les instructions

> Pour plus d'informations, Merci de vous rendre dans la partie _Algorithmique_.
> Ici ce ne sera qu'un simple rappel avec les spécificités du PHP.
{.is-warning}


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
|  `**`  | Exponentiation |

```php
// Changement de signe
$a = 5;
echo -$a; // Affichera -5

// Addition
echo 2 + 3; // Affichera 5

// Soustraction
echo 5 - 2; // Affichera 3

// Multiplication
echo 2 * 3; // Affichera 6

// Division
echo 6 / 2; // Affichera 3

// Modulo
echo 5 % 2; // Affichera 1 (car 5 divisé par 2 laisse un reste de 1)

// Exponentiation
echo 5 ** 2; // Affichera 25

```

### La concaténation de chaînes

Le « . » (le point)

```php
$part1 = "Hello, ";
$part2 = "world!";
echo $part1 . $part2; // Affichera "Hello, world!"
```

### Les opérateurs logiques (et binaires)

|   Signe    |      Opération      |
| :--------: | :-----------------: |
|    `!`     |     NON logique     |
| `&&` `AND` |     ET logique      |
| `||` `OR`  |     OU logique      |
|   `XOR`    | OU exclusif logique |

```php
// NON logique
$a = true;
echo !$a; // Affichera ''

// ET logique
echo true && false; // Affichera ''

// ET logique
echo true and false; // Affichera ''

// OU logique
echo true || false; // Affichera '1'

// OU logique
echo true or false; // Affichera '1'

// OU exclusif logique
echo true XOR false; // Affichera '1'

// OU exclusif logique
echo true XOR true; // Affichera ''

```

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

```php
// Egalité
echo (5 == 5); // Affichera '1' (true)

// Identité
echo (5 === "5"); // Affichera '' (false), car les types sont différents

// Différent
echo (5 != 7); // Affichera '1' (true)

// Strictement Inférieur
echo (5 < 7); // Affichera '1' (true)

// Inférieur ou égal
echo (5 <= 5); // Affichera '1' (true)

// Strictement Supérieur
echo (5 > 4); // Affichera '1' (true)

// Supérieur ou égal
echo (5 >= 5); // Affichera '1' (true)

// Combiné (PHP 7)
echo (1 <=> 2); // Affichera '-1' (1 est inférieur à 2)

```

### Cas particulier de l'affectation

|   Signe    |         Opération         |   Equivalent    |
| :--------: | :-----------------------: | :-------------: |
|  `$a = 1`  |   Afffection par copie    |        \        |
| `$b = &$a` | Affectation par référence |        \        |
| `$a += $b` |          Addidtion          | `$a = $a + $b`  |
| `$a -= $b` |         Soustraction          | `$a = $a -* $b` |
| `$a *= $b` |         Multiplication         | `$a = $a * $b`  |
|   `$a++`   |      Incrémentation       |  `$a = $a + 1`  |

/!\ Une référence est une copie de l'adresse mémoire de la variable.


```php
// Affectation par copie
$a = 1;
echo $a; // Affichera '1'

// Affectation par référence
$b = &$a;
$a = 2;
echo $b; // Affichera '2' car $b fait référence à $a

// Egalité avec addition
$a += 2; // Equivalent à $a = $a + 2;

// Incrémentation
$a++;
echo $a; // Si $a valait 2 avant, il vaut maintenant 3

```


<!-- https://www.w3schools.com/php/php_operators.asp -->

### Règles des priorités des expressions

![regles-priorite-operateurs_(small).png](/images/php/regles-priorite-operateurs_(small).png)

# Boucles et Conditions

[comment]: #'CONDITIONS'

## Structure Alternative et de choix

### Structure Alternative

```php
if($a == $b)
{
  echo "A est égal à B";
}
elseif($a > $b)
{
  echo "A est supérieur à B";
}
else
{
  echo "A est inférieur à B";
}
```
### Structure de Choix Multiple

```php
switch($a)
{
  case $b : echo "A est égal à B";
            break

  case >$b: echo "A est supérieur à B";
            break;

  default : echo "A est inférieur à B";
            break
}
```

### Opérateur ternaire

> L'opérateur ternaire est une forme abrégée d'une structure conditionnelle `if...else...`.
{.is-success}


```php
// syntaxe
// (condition) ? valeur_si_vraie : valeur_si_fausse;

$var = 2;
echo ($var > 3) ? 'plus grand<br />' : 'plus petit<br />';
```

### Opérateur de coalescence nulle (??)

> L'opérateur de coalescence nulle permet de retourner la première valeur définie et non null dans une chaîne de variables ou d'expressions.
{.is-success}

Cet opérateur vérifie les valeurs de gauche à droite. Dès qu'il rencontre une valeur qui n'est ni undefined ni null, il retourne cette valeur. Si toutes les valeurs sont undefined ou null, il retourne la valeur_par_défaut.

```php
// syntaxe
// (Définie) ?? (Définie) ?? (Définie) ?? "valeur_par_défaut";
$sMaCouleur = $bleu ?? $pink ?? $purple ?? "Pas de couleur";
```

Cet opérateur vérifie les valeurs de gauche à droite. Dès qu'il rencontre une valeur qui n'est ni undefined ni null, il retourne cette valeur. Si toutes les valeurs sont undefined ou null, il retourne la valeur_par_défaut.

[comment]: #'BOUCLES'

## Structures de répétition

### While

```php
$i = 0;
while($i <= 10)
{
  echo "-$i-";
  $i++;
}
```

### Do - While

```php
$i = 0;
do
{
  echo "-$i-";
  $i++;
} while($i <= 10)
```

### For

```php
for($i = 0; $i <= 10; $i++)
{
  echo "-$i-";
}
```


### Foreach (Array)

Nous le verrons plus en détail lorsque nous parlerons des tableaux :) 

```php
$aAgePersonne = array("Loïc" => 29, "Julien" => 30, "Stanislas" => 30);

foreach($aAgePersonne as $nom => $age)
{
  echo "$nom a $age ans. <br />";
}
```

## Mots-clés

### CONTINUE
`continue` permet de sortir de l'itération en cour et de passer à la suivante.

```php
for (var i = 0; i < 10; i++) {
	if (i <= 5) {
		continue;
	}
	echo "- ";
}
```

### BREAK
`break` permet de sortir de la boucle en cours.

```php
for (var i = 0; i < 10; i++) {
	if (i <= 5) 
  {
		echo $i;
	}
  else
  {
    break;
  }
	echo "- ";
}
```


---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/php/array)