---
title: Les notions supplémentaires indispensables
description: Le petit plus
published: 1
date: 2023-02-02T07:12:09.536Z
tags: 
editor: markdown
dateCreated: 2023-01-18T21:15:11.409Z
---

# Transtypage
**Le transtypage** (on parle aussi de **coercition**, de **cast** ou de **conversion de type**), et le fait de convertir une valeur d'un type (source) dans un autre (cible).

## Transtypage : Règles de conversion

> Chaîne de caractères ➡ Nombres 

Et oui, il est compliqué d'additionner Marcel et 5.1 😜

```php
echo "3" + 1; //Affiche 4
echo 1 + "3 petits cochons"; //Affiche 4
echo 1 + "-1.3e3"; // Affiche -1299
echo 1 + "marcel"; // Affiche 1
```

Comme se passe le transtypage de certainnes données Marcel ? (Go allume le camion)

> Tous types ➡ Booléen

```php
FALSE; //false
NULL; //false
$string = ""; //false
$string = 0; //false
$array = []; //false
```

> Les autres données seront donc vraies
{.is-warning}


> Tous types ➡ Chaîne de caractères
```php
echo true; //Affiche 1
echo false; //Affiche "" (Et non le caractère 0)
echo 10; //Affiche 10, représentation classique en base décimal
```
> La conversion sans fonctions spécifiques d'un tableau ou d'un objet en chaîne de caractères, provoquera une erreur en php.
{.is-warning}

<!-- Tous types ➡ Booléen
      - false : 
        - CONSTANTE FALSE et NULL
        - Chaîne vide ou contenant juste un zéro
        - Nnombre zéro
        - Tableau vide
        - Objet avec aucun champ défini
      - true : les autres données

    - Tous types ➡ Chaîne de caractères
      - Depuis booléen : 
          - true ➡ "1"
          - false ➡ "" (Et non le caractère 0)
      - Depuis un entier : représntation classique en base dic.
      - Depuis un tableaux et objets : affichage du type Array ou Object -->

## Transtypage : Forcer une conversion

- En le spécifiant (cast) :
```php
$var = (int)"12"; //$var contient un nombre
$var = (string)12; //$var contient un string
```
- en utilisant la fonction settype() :
```php
$var = 12;
settype($var, 'integer');
settype($var, 'string');
```
- En utilisant les fonctions dédiées : 
  - Pour les nombres : intval(...), floatval(...), doubleval(...)
  - Pour les chaînes de caractères : strval(...)
```php
$var = intval("12"); //$var contient le nombre 12
$var = strval(12); //$var contient la chaîne "12"
```

> Mais quelle est la meilleure méthode à utiliser me direz-vous ? 🤔

Je vais vous laisser faire votre propres avis ;), en allant voir la documentation. 👿

https://www.php.net/manual/fr/language.types.type-juggling.php


## Include & Require

> Les instructions **include** & **require** en PHP permet d'insérer le contenu d'un fichier PHP dans un autre fichier PHP avant son exécution par le serveur. 
{.is-success}

L'avantage est que vous pouvez créer un fichier *d'en-tête*, *de pied de page*, ect... et les mettre à jour indépendamment des autres.

Les deux instructions sont indentiques, sauf en cas d'échec :

- **include** génère un avertissement (*E_WARNING*) et le script continue (include_once)
- **require** produira une erreur fatale (E_COMPILE_ERROR) et stoppera l'éxécution du script (require_once)

## Syntaxe

```php
include 'filename'; ou require 'filename';
```

## Exemple

On veut inclure un fichier `vars.php` et notre pied de page standard appelé `footer.php` dans un autre fichier :


```php
<?php
  $color = 'red';
  $car = 'Ferrari';
?>
```

```php
<?php
echo "<a href=’https://www.php.net/’><p>Copyright &copy; 2001" . date("Y") . " The PHP Group</p></a>";
?>
```

```php
<html>
<body>

<h1>Welcome to my home page!</h1>
<?php include 'vars.php';
  		echo "I have a $color $car.";
?>
<p>Some text.</p>
<p>Some more text.</p>
<?php include_once 'footer.php';?>

</body>
</html> 
```

# Fonctions de Rappel (Callback Functions)
 
> une fonction de rappel en PHP est une fonction qui peut être passée en argument à une autre fonction. Toute fonction existante peut être utilisée comme fonction de rappel. 
{.is-success}

## exemple

**`array_map`** utilise une fonction de rappel pour appliquer une transformation à chaque élément d'un tableau. Ici, la fonction de rappel nous permet de calculer la longueur de chaque chaîne du tableau.

```php
<?php
  function my_callback($item) {
    return strlen($item);
  }

  $strings = ["apple", "orange", "banana", "coconut"];
  $lengths = array_map("my_callback", $strings);
  print_r($lengths);
?> 
```

> Depuis PHP 7, il est possible de passer des fonctions anonymes comme fonctions de rappel.
{.is-warning}

```php
<?php
  $strings = ["apple", "orange", "banana", "coconut"];
  $lengths = array_map( function($item) { return strlen($item); } , $strings);
  print_r($lengths);
?> 
```

## Définir vos propres fonctions de rappel

```php
<?php
  function exclaim($str) {
    return $str . "! ";
  }

  function ask($str) {
    return $str . "? ";
  }

  function printFormatted($str, $format) {
    // Appel de la fonction rappel $format 
    echo $format($str);
  }

  // Passe "exclaim" & "ask" en tant que fonctions de rappel à printFormatted()
  printFormatted("Hello world", "exclaim");
  printFormatted("Hello world", "ask");
?>
```


# Gestion des fichiers

> Soyez prudent lorsque vous manipulez des fichiers !
> 
> Vous pouvez faire beaucoup de dégâts si vous faites quelque chose de mal. Les erreurs les plus courantes sont : l'édition d'un mauvais fichier, le remplissage d'un disque dur avec des données inutiles et la suppression du contenu d'un fichier par accident.
{.is-warning}

## readfile() - Lire|Ouvrir un fichier

> La fonction readfile() lit un fichier et l'écrit dans le tampon de sortie.
{.is-success}


Supposons que nous ayons un fichier texte appelé "webdictionary.txt", stocké sur le serveur, qui ressemble à ceci :

```text
AJAX = Asynchronous JavaScript and XML
CSS = Cascading Style Sheets
HTML = Hyper Text Markup Language
PHP = PHP Hypertext Preprocessor
SQL = Structured Query Language
SVG = Scalable Vector Graphics
XML = EXtensible Markup Language
```

Le code PHP pour lire le fichier et l'écrire dans le tampon de sortie est le suivant (la fonction readfile() renvoie le nombre d'octets lus en cas de succès) :
```php
<?php
echo readfile("webdictionary.txt");
?> 
```

La fonction readfile() est utile si tout ce que vous voulez faire est d'ouvrir un fichier et de lire son contenu.

## fopen() - Ouvrir|Créer un fichier

> Une meilleure méthode pour ouvrir des fichiers est d'utiliser la fonction fopen(). Cette fonction vous donne plus d'options que la fonction readfile(). 
{.is-success}

Reprenons le fichier texte précédent, "webdictionary.txt"  : 

```text
AJAX = Asynchronous JavaScript and XML
CSS = Cascading Style Sheets
HTML = Hyper Text Markup Language
PHP = PHP Hypertext Preprocessor
SQL = Structured Query Language
SVG = Scalable Vector Graphics
XML = EXtensible Markup Language
```

Le premier paramètre de fopen() contient le nom du fichier à ouvrir et le second paramètre précise dans quel mode le fichier doit être ouvert. L'exemple suivant génère également un message si la fonction fopen() ne parvient pas à ouvrir le fichier spécifié :
```text
<?php
	$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);
?> 
```
Le fichier peut être ouvert dans l'un des modes suivants :
- r : Ouvre un fichier en lecture seule. Le pointeur de fichier commence au début du fichier.
- w : Ouvrir un fichier en écriture seulement. Efface le contenu du fichier ou crée un nouveau fichier s'il n'existe pas. Le pointeur du fichier commence au début du fichier.
- a : Ouvre un fichier en écriture seulement. Les données existantes dans le fichier sont préservées. Le pointeur de fichier commence à la fin du fichier. Crée un nouveau fichier si le fichier n'existe pas.
- x : Crée un nouveau fichier en écriture seulement. Retourne FALSE et une erreur si le fichier existe déjà.
- r+ : Ouvre un fichier en lecture/écriture. Le pointeur de fichier commence au début du fichier.
- w+ : Ouvre un fichier en lecture/écriture. Efface le contenu du fichier ou crée un nouveau fichier s'il n'existe pas. Le pointeur de fichier commence au début du fichier.
- a+ : Ouvre un fichier en lecture/écriture. Les données existantes dans le fichier sont préservées. Le pointeur de fichier commence à la fin du fichier. Crée un nouveau fichier si le fichier n'existe pas.
- x+ : Crée un nouveau fichier en lecture/écriture. Renvoie FALSE et une erreur si le fichier existe déjà.



> La fonction fopen() est également utilisée pour créer un fichier. C'est peut-être un peu confus, mais en PHP, un fichier est créé en utilisant la même fonction que celle utilisée pour ouvrir les fichiers.
{.is-success}


Si vous utilisez fopen() sur un fichier qui n'existe pas, il le créera, à condition que le fichier soit ouvert en écriture (w) ou en ajout (a).

L'exemple ci-dessous crée un nouveau fichier appelé "testfile.txt". Le fichier sera créé dans le même répertoire que celui où se trouve le code PHP :
<?php
  $myfile = fopen("testfile.txt", "w") 
?> 

## fread() - Lire un fichier ouvert

> La fonction fread() lit depuis un fichier ouvert.
{.is-success}

Le premier paramètre de fread() contient le nom du fichier à lire et le second paramètre spécifie le nombre maximum d'octets à lire.

Le code PHP suivant lit le fichier "webdictionary.txt" jusqu'à la fin :

```php
<?php
    fread($myfile,filesize("webdictionary.txt"));
?> 
```

## fclose() - Fermer un fichier

La fonction fclose() est utilisée pour fermer un fichier ouvert.

C'est une bonne pratique de programmation que de fermer tous les fichiers après les avoir utilisés. Vous ne voulez pas qu'un fichier ouvert se balade sur votre serveur en consommant des ressources !

La fonction fclose() requiert le nom du fichier (ou une variable qui contient le nom du fichier) que nous voulons fermer :
<?php
  $myfile = fopen("webdictionary.txt", "r");
  // du code à exécuter....
  fclose($myfile);
?>

## fgets() - Lire une seule ligne

La fonction fgets() est utilisée pour lire une seule ligne d'un fichier.

L'exemple ci-dessous affiche la première ligne du fichier "webdictionary.txt" :
<?php
  $myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
  echo fgets($myfile);
  fclose($myfile);
?> 

## feof() - Vérifier la fin du fichier

La fonction feof() vérifie si la "fin du fichier" (EOF) a été atteinte.

La fonction feof() est utile pour lire en boucle des données de longueur inconnue.

L'exemple ci-dessous lit le fichier "webdictionary.txt" ligne par ligne, jusqu'à ce que la fin du fichier soit atteinte :
<?php
  $myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
  // Affiche une ligne jusqu’à la fin du fichier
  while(!feof($myfile)) {
    echo fgets($myfile) . "<br>";
  }
  fclose($myfile);
?> 

## getc() - Lire un seul caractère

La fonction fgetc() est utilisée pour lire un seul caractère dans un fichier.

L'exemple ci-dessous lit le fichier "webdictionary.txt" caractère par caractère, jusqu'à ce que la fin du fichier soit atteinte :
<?php
  $myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
  // Output one character until end-of-file
  while(!feof($myfile)) {
    echo fgetc($myfile);
  }
  fclose($myfile);
?> 

## fwrite() - Écrire dans un fichier

La fonction fwrite() est utilisée pour écrire dans un fichier.

Le premier paramètre de fwrite() contient le nom du fichier à écrire et le second paramètre est la chaîne à écrire.

L'exemple ci-dessous écrit quelques noms dans un nouveau fichier appelé "newfile.txt" :
<?php
  $myfile = fopen("newfile.txt", "w") or die("Unable to open file!");
  $txt = "John Doe\n";
  fwrite($myfile, $txt);
  $txt = "Jane Doe\n";
  fwrite($myfile, $txt);
  fclose($myfile);
?> 

Remarquez que nous avons écrit deux fois dans le fichier "newfile.txt". Chaque fois que nous avons écrit dans le fichier, nous avons envoyé la chaîne $txt qui contenait d'abord "John Doe" et ensuite "Jane Doe". Après avoir fini d'écrire, nous avons fermé le fichier à l'aide de la fonction fclose().

Si nous ouvrons le fichier "newfile.txt", il ressemblera à ceci :
Jean Dupont
Jane Doe
Écrasement du contenu du fichier
Maintenant que "newfile.txt" contient des données, nous pouvons montrer ce qui se passe lorsque nous ouvrons un fichier existant pour l'écrire. Toutes les données existantes seront EFFACÉES et nous commencerons avec un fichier vide.

Dans l'exemple ci-dessous, nous ouvrons notre fichier existant "newfile.txt", et nous y écrivons de nouvelles données :
<?php
  $myfile = fopen("newfile.txt", "w") or die("Unable to open file!");
  $txt = "Mickey Mouse\n";
  fwrite($myfile, $txt);
  $txt = "Minnie Mouse\n";
  fwrite($myfile, $txt);
  fclose($myfile);
?> 

Si nous ouvrons maintenant le fichier "newfile.txt", John et Jane ont disparu, et seules les données que nous venons d'écrire sont présentes :
Mickey Mouse
Minnie Mouse


# Sécurisation

## Introduction

> Il existe beaucoup de méthodes de cryptage. Cela peut aller des algorithmes de chiffrement (pouvant être décryptés avec l’algorithme et la clé adéquate) aux algorithmes de hachage. Ce sont plutôt ces derniers que l’on a tendance à utiliser aujourd’hui.
{.is-success}


Dans le cas général, le chiffrement utilise une clé. C’est une suite de lettres (ou une phrase) qui est connue des deux parties.

Une fois que le pirate a obtenu l’accès direct à votre base de données (en contournant le serveur web), les données sensibles, stockées dans votre base sont accessibles directement, à moins 	que les données de la base ne soient protégées par la base. Chiffrer les données est une bonne solution pour réduire cette menace, mais très peu de bases de données offrent ce type de chiffrement.

Il existe de nombreuses fonctions Php qui permettent de générer un algorithme permettant ainsi de chiffrer un mot de passe. Cependant, ces fonctions ont fini par devenir obsolètes avec le temps car leurs chiffrements ont fini par être découverts ! 	C’est le lot de toutes protections informatiques quelles qu'elles soient !

Parmi ces fonctions, nous avons :
    • crypt() : Hachage à sens unique (indéchiffrable)
    • password_hash() :Crée une table de hachage pour un mot de passe
    • sha1() : Calcule le sha1 d’une chaîne de caractères
    • md5() : Calcule le md5 d’une chaîne
  	
L’utilisation de bcrypt(), qui est une fonction de hachage, reste la meilleure pratique actuellement acceptée pour le hachage des mots de passe, mais un grand nombre de développeurs utilisent encore des algorithmes plus anciens et plus faibles comme MD5 et SHA1.

Certains développeurs n’utilisent même pas de sel lors du hachage. L’API de hachage de PHP, à partir de la version 5.5, favorise l’utilisation de bcrypt tout en cachant sa complexité, dans le but d’étendre son utilisation.

Cette API de hachage de mot de passe expose quatre fonctions simples:
    • password_hash() : utilisée pour hacher le mot de passe.
    • password_verify() : utilisée pour vérifier un mot de passe par rapport à son hachage.
    • password_needs_rehash() : utilisée lorsqu’un mot de passe doit être modifié.
    • password_get_info() : renvoie le nom de l’algorithme de hachage et diverses options utilisées lors du hachage.
    
    
## Les fonctions traditionnelles de hachage md5() et sha1()

### La fonction MD5
La fonction md5() est une fonction intégrée en PHP qui est utilisée pour calculer le hachage MD5 d’une chaîne. Elle utilise, comme son nom l’indique, l’algorithme MD5 : Message-Digest de RSA Data Security, Inc. Pour calculer le hachage MD5 d’un fichier, on utilise la fonction md5_file().

#### Exemple de hash avec md5()
```php
<!DOCTYPE html>
<html>
<body>
  
  <?php
    $str = "totoasticot";
    $md5 = md5($str);
    echo $md5;
    // Affiche 0ed1b3eba9bca90289205ef70def99e0 
  ?>
  
</body>
</html>
```

La variable $md5 contient alors une chaîne unique, composée de caractères hexadécimaux et d’une longueur de 32 caractères, soit: 0ed1b3eba9bca90289205ef70def99e0.

Il n’est pas recommandé d’utiliser cette fonction pour sécuriser les mots de passe, en raison de la nature rapide de cet algorithme de hachage.

### La fonction SHA1
#### Syntaxe
```
sha1 ( string $str [, bool $raw_output = FALSE ] ) : string
```

str: La chaîne d’entrée.
raw_output: Si le paramètre optionnel raw_output est passé à TRUE, le sha1 est retourné sous forme binaire brute avec une taille de 20 caractères, sinon, il est retourné sous la forme d’un nombre hexadécimal d'une taille de 40 caractères.

#### Exemple de hash avec sha1()
```php
<!DOCTYPE html>
<html>
<body>
  
  <?php
    $str = "totoasticot";
    $sha1 = sha1($str);
    echo $sha1;
    // Affiche d3659a03108f13ec762aeb16baf63e968d1cb647
  ?>
  
</body>
</html>
```

La variable *$sha1* contient ici une chaîne unique, composée de caractères hexadécimaux et d’une longueur de 40 caractères.

Il n’est pas recommandé d’utiliser cette fonction pour sécuriser les mots de passe, en raison de la nature rapide de cet algorithme de hachage.
Pourquoi les fonctions traditionnelles de hachage comme md5() et sha1() sont-elles inappropriées aux mots de passe ?
Les algorithmes de hachage comme MD5, SHA1 et SHA256 sont destinés à être rapides et efficaces. Avec les équipements informatiques modernes, il est devenu facile d’attaquer par force brute la sortie de ces algorithmes pour retrouver la chaîne originale. C’est la raison pour laquelle de nombreux experts en sécurité considèrent ces algorithmes comme faibles et les déconseillent fortement pour hacher un mot de passe utilisateur.

## Les nouvelles fonctions de hachage
La nouvelle API de hachage de mot de passe expose quatre fonctions simples:
    • password_hash() : utilisée pour hacher le mot de passe.
    • password_verify() : utilisée pour vérifier un mot de passe par rapport à son hachage.
    • password_needs_rehash() :  utilisée lorsqu’un mot de passe doit être retravaillé. (On modifie son algorithme ou son hash).
    • password_get_info() : renvoie le nom de l’algorithme de hachage et diverses options utilisées lors du hachage.

### password_hash()
La fonction password_hash() crypte dynamiquement une information et c’est la fonction recommandé pour le hachage des mots de passe. Lorsque vous devez hacher un mot de passe avec cette fonction, alimentez-le simplement dans la fonction et il renverra le hachage que vous pouvez stocker dans votre base de données.

```
$hash = password_hash($password, PASSWORD_DEFAULT);
```

#### Syntaxe

```
string password_hash( string $password , integer $algo [, array $options ])
```

    • password : Le mot de passe utilisateur.
    • algo : Une constante de l’algorithme de mot de passe représentant l’algorithme à utiliser lors du hachage du mot de passe.
    • options : Un tableau associatif contenant les options. Voir aussi les constantes de l’algorithme de mot de passe pour une documentation sur les options supportées pour chaque algorithme. Si omis, un salt aléatoire sera créé et le cost par défaut sera utilisé.

Cette fonction reçoit toujours deux paramètres :
    • la chaîne de caractère : dans notre cas, il s’agit du mot de passe
    • l’option de hashage : nous avons trois options de hashage :
        ◦ PASSWORD_DEFAULT : Utilisation de l'algorithme bcrypt (par défaut depuis PHP 5.5.0). Notez que cette constante est conçue pour changer dans le temps, au fur et à mesure que des algorithmes plus récents et plus forts sont ajoutés à PHP. Pour cette raison, la longueur du résultat issu de cet algorithme peut changer dans le temps, il est donc recommandé de stocker le résultat dans une colonne de la base de données qui peut contenir au moins 60 caractères (255 caractères peut être un très bon choix).
        ◦ PASSWORD_BCRYPT : Utilisation de l'algorithme CRYPT_BLOWFISH pour créer la clé de hachage. Ceci va créer une clé de hachage standard crypt() utilisant l'identifiant "$2y$". Le résultat sera toujours une chaîne de 60 caractères, ou false si une erreur survient.
        ◦ PASSWORD_ARGON2I - Utilise l'algorithme de hachage Argon2i pour créer le hachage. Cet algorithme est seulement disponible si PHP a été compilé avec le support d'Argon2 
        ◦ PASSWORD_ARGON2ID - Utilise l'algorithme de hachage Argon2id pour créer le hachage. Cet algorithme est seulement disponible si PHP a été compilé avec le support d'Argon2 

### password_verify ()
Vérifie que le hachage fourni correspond bien au mot de passe fourni. La fonction password_verify() prend un mot de passe ordinaire et la chaîne hachée comme ses deux arguments. Il retourne true si le hachage correspond au mot de passe spécifié.

```php
<!DOCTYPE html>
<html>
<body>
  
<?php
  if (password_verify($password, $hash)) {
      // Success!
  }
  else {
      // Invalid credentials
  }
?>
</body>
</html>
```

#### Syntaxe
```password_verify ( string $password , string $hash ) : bool```

### password_needs_rehash()
Vérifie que le hachage fourni est conforme à l’algorithme et aux options spécifiées. Retourne true si le hachage doit être régénéré pour correspondre aux paramètres algo et options fournis, ou false sinon.

```php
<?php
$password = 'rasmuslerdorf';
$hash = '$2y$10$YCFsG6elYca568hBi2pZ0.3LDL5wjgxct1N8w/oLR/jfHsiQwCqTS';

// Le paramètre cost peut évoluer avec le temps en fonction des améliorations matérielles.
$options = array('cost' => 11);

// Vérifions d'abord que le mot de passe correspond au hachage stocké
if (password_verify($password, $hash)) {
    // Le hachage correspond, on vérifie au cas où un nouvel algorithme de hachage serait disponible ou si le coût a été changé
    if (password_needs_rehash($hash, PASSWORD_DEFAULT, $options)) {
        // On crée un nouveau hachage afin de mettre à jour l'ancien
        $newHash = password_hash($password, PASSWORD_DEFAULT, $options);
    }
    // On connecte l'utilisateur
}
?>
```

password_get_info ()
password_get_info() accepte un hachage et renvoie un tableau associatif de trois éléments:
    • algo – une constante qui identifie un algorithme particulier
    • algoName – le nom de l’algorithme utilisé
    • options – diverses options utilisées lors de la génération du hachage









---


# Comprendre les failles


La sécurité, c'est bien. :+1:

Mais la comprendre, c'est mieux ! :muscle:

Voici les failles les plus communes : 

- [Injection SQL](./details/injection_sql.md)
- [Attaque par force brute (ou Brute Force)](./details/brute_force.md)
- [Cross-Site Scripting (ou XSS)](./details/xss.md)
- [Cross-Site Request Forgery (ou CSRF)](./details/csrf.md)

Pour chacune de ces failles, on va d'abord se mettre dans la peau du pirate en tentant d'attaquer un site mal protégé, puis on verra comment se prémunir.


## Notions générales de sécurité

- Objectif de la sécurité informatique : empêcher les accès & comportements non-autorisés.
- Il faut définir les comportements autorisés, et partir d'une base où tous les accès sont fermés, pour n'autoriser ensuite au cas-par-cas que les comportements autorisés (principe de la whitelist). Ne surtout pas travailler dans le sens inverse (tous accès ouverts par défaut et bloquer au cas-par-cas — principe de la blacklist).
  - Exemple : bloquer l'accès à toutes les pages d'un site, sauf le formulaire de login, puis autoriser l'accès si login OK. Éventuellement laisser l'accès libre à certaines pages spécifiques et bien identifiées.
- Un système sécurisé à 100% ça n'existe pas ! Partir du principe qu'il y aura toujours des [vulnérabilités](https://fr.wikipedia.org/wiki/Vuln%C3%A9rabilit%C3%A9_(informatique))/failles — c'est ce qu'on constate depuis qu'on s'intéresse au sujet et ça n'a pas de raisons de changer.
- La sécurité, ce n'est pas que la lutte contre les intrusions, le vol ou la destruction de données. Un affichage malencontreux d'une donnée sensible peut-être désastreux (ex. affichage du mot de passe de ses clients « par hasard » dans une page mal conçue, ou rendue publique par erreur ; affichage du mot de passe, en clair, dans le mail de confirmation d'inscription ; etc.)
- La sécurité doit être une activité multi-factorielle / multi-niveaux. Il y a des failles aussi bien sur la couche physique (ex. l'accès aux machines) que sur la partie serveur (vulnérabilités, bugs…), la partie cliente (navigateurs mal protégés, cybercafé, WiFi…), la couche « sociale » (menaces, extorsion, manipulation…) etc.

## Déroulé-type d'une attaque

En résumé :

- l'attaquant se connecte sur un système auquel il n'est pas censé avoir accès
- l'attaquant réalise sur ce système des opérations délictueuses : vol de données, destruction de données, etc.

<details>
<summary>Plus en détails</summary>

- L'attaquant sélectionne une faille repérée sur le système ciblé.
- 1ère charge – connexion : mise en place d'un canal de communication, adapté pour l'attaque, avec le système ciblé (par exemple, requête HTTP pour le web). Peut nécessiter de la part de l'attaquant de réaliser au préalable une [élévation de privilège](https://fr.wikipedia.org/wiki/%C3%89l%C3%A9vation_des_privil%C3%A8ges) grâce à une autre faille repérée en amont.
- 2ème charge — intrusion (souvent, pour de l'observation, du vol de données…) : exploitation du canal de communication pour faire une mise en place de code malicieux. Possibilité de mise en place d'un proxy (programme relais spécifique, anodin en lui-même mais support du code malicieux, qui va permettre de brouiller les pistes).
- 3ème charge – destruction (parfois, mais pas si souvent que ça car ne passe pas inaperçu !) : action destructive / prise de contrôle.

La majorité des attaques s'arrêtent à la seconde charge, et continuent sur ce mode-là tant que l'attaque n'est pas repérée et se justifie.
</details>

<details>
<summary>Exemple</summary>

Un attaquant repère une faille XSS sur un site web (sélection), injecte un script JS avec mise en place d'un canal de communication AJAX voire WebSocket (1ère charge) ; le script est exécuté par le client d'une victime et transmet des informations sensibles (2ème charge).
</details>

Nous pouvons aussi allez voir la [Base](Base.md) de la sécurité.

**Important**

Ce n'est pas parce qu'on sait attaquer un site qu'il faut le faire !! Ça reste illégale !

---


## Principes de base de sécurité

> **Commencer par là**, et oui, si j'ai pas les bases ça rien à rien.

### La théorie

- Règle simple pour estimer un risque : `risque = gravité x probabilité`.
- Segmenter son code pour mieux gérer le facteur gravité. Et oui, si j'ai une app monolithique alors si j'ai une faille, toute mon app sera vulnérable alors que si mon app est distribuée alors c'est un peu plus sécurisé (mais au niveau de la probabilité ça augmente).
- Pour minimiser la `probabilité` d'une attaque réussie, il faut mettre en place plusieurs couches de sécurité, complémentaires, notamment sur les parties où on a identifié que le facteur `gravité` est grand.
- Certains risques ne peuvent pas être anticipés, il faudrait prévoir un bouton `arret d'urgence` pour pallier à un problème trop grand. Il vaut mieux une application éteinte, qu'une perte totale des données.


### La pratique

- Commencer par procéder à une analyse des risques. Je peux essayer d'`hacker` **mon** site avec les failles que je connais.
- Couvrir les risques fondamentaux le plus tôt possible dans la phase de développement, faute de quoi ce ne sera pas fait au final. **Configurer tout ça dès les premiers jours**.
- Prévoir un « système d'intégrité » c'est à dire, un mécanisme de sauvegarde et restauration, automatique si possible. Par exemple, export SQL quotidien pour la base de données. 


## Grands axes de sécurité web

- Éducation de ses utilisateurs.
- Données récupérées de sources externes (protection contre les injections).

![](https://imgs.xkcd.com/comics/exploits_of_a_mom.png)

- Hash de données (protection contre les attaques par dictionnaires).
- ACL (protection contre les attaques par élévation de privilèges).
- SSL/HTTPS (protection contre le vol de données sur le trafic réseau).
- Protection par domaine ([CORS](https://developer.mozilla.org/fr/docs/Web/HTTP/CORS))
- etc.

Ces différents axes sont **complémentaires** ! C'est pas lui ou lui, mais lui ET lui.

## Bonnes pratiques

- Revue de sécurité (temps dédié à la fin des sprints, pendant les _code-reviews_…).
- Tests spécifiques (intrusion, DDOS…).
- Intégration, tout au long du processus de développement.


## Référentiels de sécurité

- [OWASP](https://www.owasp.org/)
  - [Top 10 des vulnérabilités](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)
  - [Fiches-pratique](https://github.com/OWASP/CheatSheetSeries)
  - [Contrôles proactifs](https://www.owasp.org/index.php/OWASP_Proactive_Controls)
  - [Standards de vérification](https://www.owasp.org/index.php/Category:OWASP_Application_Security_Verification_Standard_Project)
- https://www.cert.ssi.gouv.fr/

## Ressources

### Sites de référence

* https://www.hacksplaining.com/lessons

### Lectures additionnelles

Beaucoup, beaucoup, beaucoup d'informations disponibles sur internet. En plus des ressources ci-dessus, indispensables et déjà très fournies, voici une sélection très succinte et sujette à modification :

- [_A quick introduction to web security_](https://medium.freecodecamp.org/a-quick-introduction-to-web-security-f90beaf4dd41)
- [Série _How Browsers Work_](https://medium.freecodecamp.org/web-application-security-understanding-the-browser-5305ed2f1dac)
- [Ingénierie sociale : _The Life of Death_](https://textslashplain.com/2017/01/14/the-line-of-death/)

---

# Attaque par force brute

## Le principe

Tester tous les mots de passe possibles jusqu'à trouver le bon. Tout simplement.

## L'attaque

1. Trouver le pseudo ou l'email de notre victime. (pas si compliqué)

2. Réaliser une requête vers le site qu'on attaque

`https://lesite.com/login?pseudo=victime&password=aaa`

3. Changer de pass et recommencer en boucle jusqu'à trouver le bon !

Alors oui, à la main, c'est long. Mais on peut rapidement coder une boucle qui teste tout très vite. Un petit exemple en 50 lignes se trouve [ici](./exemple/brut_force.php).

## Détails
* Les formulaires de connexion sont la plupart du temps en POST. Pas grave, on a les outils pour faire des requêtes POST. [La doc là](https://www.php.net/manual/fr/book.curl.php), et [un exemple ici](https://stackoverflow.com/questions/5647461/how-do-i-send-a-post-request-with-php).

* Pour trouver le nom des paramètres à envoyer au serveur, rien de plus simple, il suffit d'inspecter le contenu du formulaire dans un navigateur et de repérer les `name` des `input`.


## Comment se défendre

Avant toute chose, il faut dire que plus le mot de passe est long et compliqué, plus il sera difficile de le trouver. En tout cas, ça sera plus long.

La première chose à faire est donc d'obliger ses utilisateurs à choisir un mot de passe suffisament solide. Selon la [recommandation de la CNIL](https://www.cnil.fr/fr/authentification-par-mot-de-passe-les-mesures-de-securite-elementaires), il faut : 
- au moins 8 caractères
- au moins une lettre majuscule
- au moins une lettre minuscule
- au moins un chiffre
- au moins un caractère spécial 


Ensuite on peut compter le nomdre d'essais erronés pour se connecter, et verouiller le compte après X essais infructueux ou trop proches dans le temps. Mais c'est à double tranchant ! Si un pirate s'amuse à faire des requêtes volontairement éronnées avec tous les pseudos possibles et imaginables, il peut bloquer les comptes de tous les utilisateurs et rendre le site complètement inaccessible !

On peut imaginer alors de mettre en place la même chose, mais avec l'adresse IP. Mais c'est loin d'être évident à faire en PHP. On peut aussi utiliser des outils tel [fail2ban](https://www.fail2ban.org/wiki/index.php/Main_Page) qui scanne les logs du serveur et bannit les IP qui paraissent malicieuses.


Enfin, on peut multiplier les étapes de validation d'un login, en rajoutant par exemple un CAPTCHA (pour s'assurer que c'est bien un humain et non un script qui tente de se log), ou une double authentification par email, SMS, ou tout autre système (2FA).

---


# Injections SQL

## Le principe

Exécuter toutes les requêtes qu'on veut dans la base de données de notre victime !

**Note**: le principe de l'injection fonctionne aussi dans les bases NoSQL !

## L'attaque

1. Trouvez un site où la soumission d'un formulaire déclenche selon vous une requête SQL. Pas trop difficile, c'est presque toujours le cas ! Par exemple, un formulaire de connexion va faire une requête SQL pour vous retrouver dans la bdd...

2. Au lieu de taper votre pseudo dans l'input, tapez plutôt une requête SQL. Ou un bout de requête SQL.

3. Si vous avez de la chance, votre requête sera exécutée ! :smiling_imp:

## L'attaque en détail

1. Imaginez la requête SQL qui se cache derrière le formulaire. Dans notre exemple, la requête devrait ressembler à :
```sql
SELECT * FROM users WHERE username = 'pseudo';
```
où la valeur `pseudo` vient directement du formulaire.

2. Maintenant, écrivez ceci dans le formulaire : 

`'; DROP TABLE users; --`

On se retrouve avec la requête suivante : 
```sql
SELECT * FROM users WHERE username = ''; DROP TABLE users; --
```

:boom: Catastrophe, les 2 parties de la requêtes vont s'exécuter, et la table `users` va être totalement supprimée !!

## Comment se défendre

Si on a réussi à effectuer cette attaque, c'est probablement parce que des développeurs ont fait l'erreur suivante :
```php
<?php
// récupérer la valeur passée dans le formulaire
$username = $_POST['login'];
// puis construire la requête SQL en concaténant simplement la valeur récupérée
$query = "SELECT * FROM users WHERE username= ' $username ' ";
// exécuter la requête (et pleurer...)
```

Mais comment faire autrement ?

#### À l'ancienne : échapper les chaines de caractères

En utilisant des fonctions d'échappement (comme [addslashes en PHP](https://www.php.net/manual/fr/function.addslashes.php)), on force le serveur à considérer la valeur comme une seule chaîne de caractères.
Ainsi, on peut faire : 
```php
// récupérer la valeur passée dans le formulaire
$username = $_POST['login'];
// échapper la valeur (= protéger les caractères spéciaux avec des \)
$username = addslashes($username);
// puis construire la requête SQL en concaténant simplement la valeur échappée
$query = "SELECT * FROM users WHERE username= ' $username ' ";

// l'exécution est un peu plus sécurisée
```

Si on essaye de passer notre valeur malicieuse ( `'; DROP TABLE users; --` ), elle sera considérée comme une chaine de caractères et non comme une instruction.

#### La vraie bonne solution : en utilisant les requêtes préparées

L'exemple suivant utilise PDO en PHP, mais le principe des requêtes préparées existe dans tous les langages !

```php
// récupérer la valeur passée dans le formulaire
$username = $_POST['login'];

// créer la requête avec un jeton (ou paramètre préparéé)
$query = "SELECT * FROM users WHERE username = :username ";

// on PREPARE la requête 
$statement = $pdo->prepare($query);

// Puis, avant d'exécuter la requête, on remplace les jetons par des valeurs qui seront automatiquement échappées
$statement->bindValue(":username", $username );

// Et enfin, on peut exécuter la requête en toute sécurité
$statement->execute();
```

REMARQUE : avec PDO, on peut se passer de `bindValue` et passer directement les valeurs dans un tableau associatif en paramètre de `execute`, comme ceci :
```php
$statement = $pdo->prepare($query);

$statement->execute([
  ":username" => $username
]);
```

---

# Cross Site Scripting (XSS)

## Le principe

Exécuter un script maison sur tous les navigateurs de tous les utilisateurs du site piraté.

## L'attaque, version formulaire
1. Trouvez un site web où un formulaire vous permet d'ajouter du contenu au site, ou de participer à celui-ci. Par exemple, Wikipédia, ou un formulaire de commentaire sous un article de blog.
2. Écrivez des balises HTML dans les champs du formulaire. Par exemple, `<h1>hihihi</h1>`.
3. Soumettez le formulaire. Votre "commentaire" sera alors sauvegardé en base de donnée.
4. Rafraîchissez la page, et regardez si votre balise HTML est toujours là, et bien interprétée par le navigateur (ie le texte hihihi s'affiche en grand). Si oui, vous avez réussi une attaque XSS ! :boom:
5. Vous pouvez maintenant passer à l'étape supérieure et injecter des balises `<script>` :imp:

Tous les visiteurs qui affichent cette page subiront votre attaque.

## Comment se défendre

Avant de sauvegarder les données d'utilisateurs peu fiables en base de données, on doit utiliser la fonction [strip_tags](https://www.php.net/manual/fr/function.strip-tags.php) de PHP pour retirer toutes les balises HTML ! Concrètement :

```php
//en traitant un formulaire
$username = strip_tags($_POST['username']);
$comment  = strip_tags($_POST['comment']);
//et ainsi de suite pour toutes les données !
```

En 2ème couche de protection, au moment de l'affichage, on doit transformer les balises en entités HTML avec la fonction PHP [htmlentities](https://www.php.net/manual/fr/function.htmlentities.php). Ceci aurait désactivé les balises. Concrètement :

```php
<div class="comment">
    <div>Auteur : <?= htmlentities($username) ?></div>
    <p><?= htmlentities($comment) ?></p>
</div>
```
## L'attaque, version URL

Les données d'un utilisateur peuvent provenir d'un formulaire, mais aussi directement depuis l'URL ! Il est donc possible de réaliser des attaques XSS (dites non-persistantes) en manipulant les paramètres des urls.

Par exemple, en réalisant une recherche sur http://allocine.fr, on constate que le mot-clef saisi se retrouve dans l'URL ET est réaffiché dans la page. Une recherche de batman m'amène sur l'URL http://www.allocine.fr/recherche/?q=batman et mon terme de recherche m'est représenté.

Que se passe-t-il si je modifie `?q=batman` par `?q=<h1>batman</h1>` dans la barre d'adresse ? Est-ce que batman s'affiche en grand sur la page ? Si oui, on a trouvé une faille ! Il ne reste qu'à remplacer le `<h1>` par un `<script>`, et c'est parti !

Par exemple : `http://lesitecible.fr/search?q=<script>alert("piraté!")</script>`

Malheureusement, ou plutôt _évidemment_, l'attaque échoue sur AlloCiné :wink:.

> Mais d'ailleurs, est-ce que je ne suis pas en train de me hacker moi-même ? Quel est l'intérêt ?

Bonne question ! Il n'y a que nous qui voyons l'attaque, puisqu'elle n'est pas sauvegardée en bdd !

Mais si on on postait un lien comprenant notre attaque XSS sur un forum ? Quelque chose comme :

```html
<a href="http://lesitecible.fr/search?q=<script>alert('piraté!')</script>" >Voir des chatons mignons</a>
```
Les internautes qui cliqueraient dessus se retrouveraient sur le site victime, avec notre attaque XSS qui s'exécuterait!


Alors bien sûr, une `alert` c'est pas bien méchant. Mais en JS, on a accès aux cookies, et on peut faire des requêtes en AJAX. Donc on peut voler des cookies et les envoyer vers un serveur perso. :exploding_head:

## Comment se défendre

Comme pour les XSS "version formulaire":
- en utilisant  [strip_tags](https://www.php.net/manual/fr/function.strip-tags.php) lors de la récupération du mot-clef :
```php
$keyword = strip_tags($_GET['q']);
```
- et [htmlentities](https://www.php.net/manual/fr/function.htmlentities.php) au moment de l'affichage : 
```php
<h2><?= htmlentities($keyword) ?></h2>
```

---

# Cross-Site Request Forgery (CSRF)

_ciseurf_, pour les intimes.

## Le principe

Exploiter la session d'une victime connectée au site cible pour exécuter des actions.

## L'attaque

1. Trouvez un site mal protégé, avec des formulaires sensibles en GET par exemple.
2. Assurez-vous que votre victime est connectée sur le site.
3. Envoyez à votre victime, par email par exemple, un lien dans ce genre : 
```html
<a href="http://www.site-mal-protege.com/change-password.php?newpass=tiguidou">Voir des chatons mignons</a>
```
4. Si la victime clique sur le lien, vous avez changé son mot de passe. :boom: Vous pouvez donc vous connecter à sa place.

WHAT? et oui! quand l'utilisateur a cliqué sur votre lien, son navigateur s'est ouvert, et a chargé l'url demandé _en envoyant tous les cookies qui concernent le site_. Or ces cookies sont justement ce qui maintient votre victime connectée au service. 

Vue du serveur, la requête vient donc d'un utilisateur tout à fait valide ! Si en plus, votre victime est admin du site, c'est la grosse fiesta !

_L'exemple de scénario avec le changement de mot de passe n'est qu'un exemple. On aurait pu poster un message en son nom, supprimer son compte, déclencher un achat, ou un virement bancaire ! Nimporte quel form peut potentiellement être soumis ainsi !_

## La fouille avant l'attaque

1. Comment trouver les failles? 
    - Essayez tous les formulaires et surveillez les url et l'onglet network de l'inspecteur
    - Testez les requêtes paramétrées dont la structure est évidente, par exemple `http://api.sitevictime.fr/user/10/delete`.
2. Comment s'assurer que la victime est connectée?
    - Le plus simple, c'est de lui demander :wink:. Contacter un admin pour une modif par exemple. A priori il va se connecter au site pour vérifier ce que vous dites.

## Comment se défendre

Avant d'effectuer des actions sensibles, on doit s'assurer que c'est bien l'utilisateur qui a rempli le formulaire, bien au chaud sur notre site.

Voici la seule méthode fiable pour s'en assurer : 

1. Avant l'affichage du formulaire, générer une chaîne aléatoire impossible à deviner (avec [random_bytes](https://www.php.net/manual/fr/function.random-bytes.php) en PHP). Cette chaîne est souvent appelée token, ou jeton.

2. Stocker cette chaîne dans la session de l'utilisateur : `$_SESSION['token'] = $token;`

3. Placer ce token en valeur d'un input caché du formulaire : 
```php
<form action="action.php">
    <input type="text" name="data">
    
    <!-- Notre token ! -->
    <input type="hidden" name="token" value="<?= $token ?>">
    
    <button>OK !</button>
</form>
```
4. Lorsque le formulaire est soumis, s'assurer que le token reçu (du formulaire) correspond bien à celui stocké en session.
    1. Si oui, vous savez que c'est bien votre site qui a affiché ce formulaire, et vous pouvez procéder à l'action.
    2. Sinon, hop hop hop ! on arrête tout, et on affiche une erreur !


#### Et maintenant, il fait quoi le pirate ?

Comment construire le lien malicieux ?
```
<a href="http://www.site-mal-protege.com/change-password.php?newpass=tiguidou&token=?????">Voir des chatons mignons</a>
```

Impossible de connaitre la valeur du token. Et de toute façon, si l'utilisateur n'est pas allé lui-même sur le formulaire, il n'y a même pas de token dans la session ! Allez, rentre chez toi, pirate ! Tu as échoué ! :muscle:

#### Du coup, on en met partout?
Oui. On devrait mettre des "jetons anti-CSRF" (ou juste "_jeton ciseurf_" par abus de langage) dans **TOUS** les formulaires.

Heureusement, la plupart des frameworks, dans tous les langages, incluent un système de jetons CSRF, soit par défaut (c'est le cas de [Symfony](https://symfony.com/doc/current/security/csrf.html#csrf-protection-in-symfony-forms) et [Laravel](https://laravel.com/docs/master/csrf)) soit comme plugin (comme dans [Express](https://www.npmjs.com/package/csurf) ).

---



<!--## Sécurisation

Pourquoi sécurisé ? 
- l'être humain n'est pas infaillible
- les attaquants sont ingénieux
- nous ne sommes pas toujours à jour ...

Sécuriser les données est primordiale et indispensable. Il faut partir du constat : "Ne jamais faire confiance à l'utilisateur"

## Principes de base de sécurité

> **Commencer par là**, et oui, si j'ai pas les bases ça rien à rien.

### La théorie

- Règle simple pour estimer un risque : `risque = gravité x probabilité`.
- Segmenter son code pour mieux gérer le facteur gravité. Et oui, si j'ai une app monolithique alors si j'ai une faille, toute mon app sera vulnérable alors que si mon app est distribuée alors c'est un peu plus sécurisé (mais au niveau de la probabilité ça augmente).
- Pour minimiser la `probabilité` d'une attaque réussie, il faut mettre en place plusieurs couches de sécurité, complémentaires, notamment sur les parties où on a identifié que le facteur `gravité` est grand.
- Certains risques ne peuvent pas être anticipés, il faudrait prévoir un bouton `arret d'urgence` pour pallier à un problème trop grand. Il vaut mieux une application éteinte, qu'une perte totale des données.


### La pratique

- Commencer par procéder à une analyse des risques. Je peux essayer d'`hacker` **mon** site avec les failles que je connais.
- Couvrir les risques fondamentaux le plus tôt possible dans la phase de développement, faute de quoi ce ne sera pas fait au final. **Configurer tout ça dès les premiers jours**.
- Prévoir un « système d'intégrité » c'est à dire, un mécanisme de sauvegarde et restauration, automatique si possible. Par exemple, export SQL quotidien pour la base de données. 


## Grands axes de sécurité web

- Éducation de ses utilisateurs.
- Données récupérées de sources externes (protection contre les injections).

![](https://imgs.xkcd.com/comics/exploits_of_a_mom.png)

- Hash de données (protection contre les attaques par dictionnaires).
- ACL (protection contre les attaques par élévation de privilèges).
- SSL/HTTPS (protection contre le vol de données sur le trafic réseau).
- Protection par domaine ([CORS](https://developer.mozilla.org/fr/docs/Web/HTTP/CORS))
- etc.

Ces différents axes sont **complémentaires** ! C'est pas lui ou lui, mais lui ET lui.

## Bonnes pratiques

- Revue de sécurité (temps dédié à la fin des sprints, pendant les _code-reviews_…).
- Tests spécifiques (intrusion, DDOS…).
- Intégration, tout au long du processus de développement.


## Référentiels de sécurité

- [OWASP](https://www.owasp.org/)
  - [Top 10 des vulnérabilités](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)
  - [Fiches-pratique](https://github.com/OWASP/CheatSheetSeries)
  - [Contrôles proactifs](https://www.owasp.org/index.php/OWASP_Proactive_Controls)
  - [Standards de vérification](https://www.owasp.org/index.php/Category:OWASP_Application_Security_Verification_Standard_Project)
- https://www.cert.ssi.gouv.fr/

## Ressources

### Sites de référence

* https://www.hacksplaining.com/lessons

### Lectures additionnelles

Beaucoup, beaucoup, beaucoup d'informations disponibles sur internet. En plus des ressources ci-dessus, indispensables et déjà très fournies, voici une sélection très succinte et sujette à modification :

- [_A quick introduction to web security_](https://medium.freecodecamp.org/a-quick-introduction-to-web-security-f90beaf4dd41)
- [Série _How Browsers Work_](https://medium.freecodecamp.org/web-application-security-understanding-the-browser-5305ed2f1dac)
- [Ingénierie sociale : _The Life of Death_](https://textslashplain.com/2017/01/14/the-line-of-death/)

---

# Sécurité

La sécurité, c'est bien. :+1:

Mais la comprendre, c'est mieux ! :muscle:

Voici les failles les plus communes : 

- [Injection SQL](./details/injection_sql.md)
- [Attaque par force brute (ou Brute Force / Credential Stuffing)](./details/brute_force.md)
- [Cross-Site Scripting (ou XSS)](./details/xss.md)
- [Cross-Site Request Forgery (ou CSRF)](./details/csrf.md)

Pour chacune de ces failles, on va d'abord se mettre dans la peau du pirate en tentant d'attaquer un site mal protégé, puis on verra comment se prémunir.


## Notions générales de sécurité

- Objectif de la sécurité informatique : empêcher les accès & comportements non-autorisés.
- Il faut définir les comportements autorisés, et partir d'une base où tous les accès sont fermés, pour n'autoriser ensuite au cas-par-cas que les comportements autorisés (principe de la whitelist). Ne surtout pas travailler dans le sens inverse (tous accès ouverts par défaut et bloquer au cas-par-cas — principe de la blacklist).
  - Exemple : bloquer l'accès à toutes les pages d'un site, sauf le formulaire de login, puis autoriser l'accès si login OK. Éventuellement laisser l'accès libre à certaines pages spécifiques et bien identifiées.
- Un système sécurisé à 100% ça n'existe pas ! Partir du principe qu'il y aura toujours des [vulnérabilités](https://fr.wikipedia.org/wiki/Vuln%C3%A9rabilit%C3%A9_(informatique))/failles — c'est ce qu'on constate depuis qu'on s'intéresse au sujet et ça n'a pas de raisons de changer.
- La sécurité, ce n'est pas que la lutte contre les intrusions, le vol ou la destruction de données. Un affichage malencontreux d'une donnée sensible peut-être désastreux (ex. affichage du mot de passe de ses clients « par hasard » dans une page mal conçue, ou rendue publique par erreur ; affichage du mot de passe, en clair, dans le mail de confirmation d'inscription ; etc.)
- La sécurité doit être une activité multi-factorielle / multi-niveaux. Il y a des failles aussi bien sur la couche physique (ex. l'accès aux machines) que sur la partie serveur (vulnérabilités, bugs…), la partie cliente (navigateurs mal protégés, cybercafé, WiFi…), la couche « sociale » (menaces, extorsion, manipulation…) etc.

## Déroulé-type d'une attaque

En résumé :

- l'attaquant se connecte sur un système auquel il n'est pas censé avoir accès
- l'attaquant réalise sur ce système des opérations délictueuses : vol de données, destruction de données, etc.

<details>
<summary>Plus en détails</summary>

- L'attaquant sélectionne une faille repérée sur le système ciblé.
- 1ère charge – connexion : mise en place d'un canal de communication, adapté pour l'attaque, avec le système ciblé (par exemple, requête HTTP pour le web). Peut nécessiter de la part de l'attaquant de réaliser au préalable une [élévation de privilège](https://fr.wikipedia.org/wiki/%C3%89l%C3%A9vation_des_privil%C3%A8ges) grâce à une autre faille repérée en amont.
- 2ème charge — intrusion (souvent, pour de l'observation, du vol de données…) : exploitation du canal de communication pour faire une mise en place de code malicieux. Possibilité de mise en place d'un proxy (programme relais spécifique, anodin en lui-même mais support du code malicieux, qui va permettre de brouiller les pistes).
- 3ème charge – destruction (parfois, mais pas si souvent que ça car ne passe pas inaperçu !) : action destructive / prise de contrôle.

La majorité des attaques s'arrêtent à la seconde charge, et continuent sur ce mode-là tant que l'attaque n'est pas repérée et se justifie.
</details>

<details>
<summary>Exemple</summary>

Un attaquant repère une faille XSS sur un site web (sélection), injecte un script JS avec mise en place d'un canal de communication AJAX voire WebSocket (1ère charge) ; le script est exécuté par le client d'une victime et transmet des informations sensibles (2ème charge).
</details>

Nous pouvons aussi allez voir la [Base](Base.md) de la sécurité.

**Important**

Ce n'est pas parce qu'on sait attaquer un site qu'il faut le faire !! Ça reste illégale !



### Faille XSS

XSS : cross-site scripting, représente le fait d'injecter du code HTML, javascript ... au sein du page Web via un formulaire ou encore une URL contenant du javascript ré encoder afin de tromper le traitement des données.

exemple :

```html
// Exemple très souvent montrer
monurl.com?search=<script>alert(document.cookie);</script>Lien</a>
```


### Injection SQL

Représente le fait d'insérer une portion de code SQL non désirée au sein d'une autre requête.

Exemple :
Dans le contexte d'une connexion à un BackOffice d'une application, on nous demande un login et un mot de passe.
Lors du traitement des données, nous effectuons la requête suivante : 
```sql
SELECT user_login FROM user WHERE user_login='login' AND user_password='password'
```

Lors de l'injection, nous insérions une requête SQL forcément vrai pour se connecter et ce peut importe le login ou le mot de passe.

```sql
SELECT user_login FROM user WHERE user_login='inject'='inject' LIMIT 0,1 -- fin !'  AND user_password='n'importe quel mot de passe ira très bien de toute façon cette partie de la requête est en commentaire!'
```

### S'en protéger

Pour s'en protéger il faut donc empécher l'utilisateur d'injecter du code javascript, php ou SQL aux endroits où l'on attend des données.
Dans les exemples ci-dessus, on s'apperçoit que des balises `<script>` ou du code SQL sont utilisés, nous avons donc besoin de "désactiver" ces balises / codes.
Pour cela nous utiliserons des fonctions natives au PHP tels que :
- `trim()`
- `htmlspecialchars()`
- `htmlentities()`
- `stripslashes()`

Voici un exemple en code : 

```php
function textCleaning($text)
{
    $text = trim($text); // supprime espace et retour à la ligne
    $text = stripslashes($text); // supprime les antislashes
    $text = htmlspecialchars($text); // transforme tout les caractères spéciaux en caractères HTML
    // exemple        " > &quot      & > &amp

    return $text;
}
```

## Chiffrement & Hachage 

Le chiffrement (et non pas Cryptage 🤢), est le fait de transfomer un document le rendant impossible à lire.
On différencie le chiffrement symétrique (même clé de chiffrement et déchiffrement) au chiffrement asymétrique (clé privée / publique).

Le Hachage est lui aussi un algorithme permettant également de modifier un texte. A la différence, que celui-ci ne peut pas être "Dé-hacher". 
Aujourd'hui, ce sont plutôt ces derniers que nous avons tendance à utiliser. Le Hachage permet de ne pas stocké de clé de déchiffrage (Sécurité en plus).

Il existe de nombreuses fonctions en PHP natif qui permettent de hacher les mots de passe. 

Voici quelques fonctions : 
- `sha1()` : Calcul le SHA1 d'une chaîne de caractère (40 caractères)
- `md5()` : Calcul le MD5 d'une chaîne de caractère (32 caractères)
- `crypt()` : Hachage à sens unique (indéchiffrable)
- `password_hash()` : Créer une table de hachage pour un mot de passe (tableau associatif Clé -> Valeur)

Cependant il en existe aussi de nombreuses obsolètes de par l'évolution des techniques de "HACK". Pour éviter toute vulnérabilité, il existe une API de hachage de mot de passe avec quatre fonctions simples utilisant par défaut l'algorithme `bcrypt`: 
- `password_hash()` : Hash de mot de passe
- `password_verify()` : Vérifie un mot de passe par rapport à son Hash
- `password_needs_rehash()` : Utilisée lorsqu'un mot de passe doit être modifié
- `password_get_info()` : Renvoie le nom de l'algo de hachage et diverses options utilisées lors du hachage.


### Salt & Pepper (Sel et le poivre)

La notion de sallage et de poivrage permet d'ajouter des élèments de sécurité à notre stockage de mot de passe.
En effet nous allons rajouter des informations à notre mot de passe et ainsi hacher le tout pour que l'attaquant ne puisse pas facilement retrouver le mot de passe original. 


Le Sel, est unique pour chaque utilisateur mais pas forcément secret. Il peut être stocké dans une base de donnée à côté d'autres informations. Son seul objectif est d'emp^cher le pirate d'utiliser des dictionnaires précalcultés de hash.

Le Poivre, permet d'augmenter le niveau de sécurité. Il est unique mais doit être gardé secret. C'est généralement une constante placée dans le code en dur.

Au final, nous nous retrouvons dans notre base de donnée avec un mot de passe haché comme tel : 
**`Pepper::Salt::Password` le tout haché ensemble.**

```php


```






<!---

FAILLE XSS 


> <script>alert("HACKER !!!!!!!") </script>


form avec $_SERVER['PHP_SELF']

en suite protéeger avec htmlspeccialschars($_SERVER['PHP_SELF'])


verifier toujours les input

fonction verifyInput

trim() qui enleve le superflu, espace supp 
stripslashes() enleve tous les anti slashes
htmlspecialchars()  " > &quot      & > &amp




enssuite securisation cote client avec required et type email 
faire des isset ou empty
pour emai; faire la fonction filter_var($var, FILTER_VALIDATE_EMAIL);

pour le tel (regex ou expression reguliaire)
preg_match("/^[0-9 ]*$", $var)



-->