---
title: Le petit plus
description: 
published: 1
date: 2023-01-31T06:34:43.925Z
tags: 
editor: markdown
dateCreated: 2023-01-18T21:15:11.409Z
---

# Les notions supplémentaires indispensables

## Transtypage
**Le transtypage** (on parle aussi de **coercition**, de **cast** ou de **conversion de type**), et le fait de convertir une valeur d'un type (source) dans un autre (cible).

### Transtypage : Règles de conversion

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

### Transtypage : Forcer une conversion

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

### Syntaxe

```php
include 'filename'; ou require 'filename';
```

### Exemple

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

## Fonctions de Rappel (Callback Functions)
> 
> une fonction de rappel en PHP est une fonction qui peut être passée en argument à une autre fonction. Toute fonction existante peut être utilisée comme fonction de rappel. 
{.is-success}

### exemple

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

### Définir vos propres fonctions de rappel

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


## Gestion des fichiers

> Soyez prudent lorsque vous manipulez des fichiers !
> 
> Vous pouvez faire beaucoup de dégâts si vous faites quelque chose de mal. Les erreurs les plus courantes sont : l'édition d'un mauvais fichier, le remplissage d'un disque dur avec des données inutiles et la suppression du contenu d'un fichier par accident.
{.is-warning}

### readfile() - Lire|Ouvrir un fichier

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

### fopen() - Ouvrir|Créer un fichier

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

### fread() - Lire un fichier ouvert

> La fonction fread() lit depuis un fichier ouvert.
{.is-success}

Le premier paramètre de fread() contient le nom du fichier à lire et le second paramètre spécifie le nombre maximum d'octets à lire.

Le code PHP suivant lit le fichier "webdictionary.txt" jusqu'à la fin :

```php
<?php
    fread($myfile,filesize("webdictionary.txt"));
?> 
```

### fclose() - Fermer un fichier

La fonction fclose() est utilisée pour fermer un fichier ouvert.

C'est une bonne pratique de programmation que de fermer tous les fichiers après les avoir utilisés. Vous ne voulez pas qu'un fichier ouvert se balade sur votre serveur en consommant des ressources !

La fonction fclose() requiert le nom du fichier (ou une variable qui contient le nom du fichier) que nous voulons fermer :
<?php
  $myfile = fopen("webdictionary.txt", "r");
  // du code à exécuter....
  fclose($myfile);
?>

### fgets() - Lire une seule ligne

La fonction fgets() est utilisée pour lire une seule ligne d'un fichier.

L'exemple ci-dessous affiche la première ligne du fichier "webdictionary.txt" :
<?php
  $myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
  echo fgets($myfile);
  fclose($myfile);
?> 

### feof() - Vérifier la fin du fichier

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

### getc() - Lire un seul caractère

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

### fwrite() - Écrire dans un fichier

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