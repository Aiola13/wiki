---
title: Le petit plus
description: 
published: 1
date: 2023-01-30T17:41:57.517Z
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


## Gestion des fichiers


## Sécurisation

Pourquoi sécurisé ? 
- l'être humain n'est pas infaillible
- les attaquants sont ingénieux
- nous ne sommes pas toujours à jour ...

Sécuriser les données est primordiale et indispensable. Il faut partir du constat : "Ne jamais faire confiance à l'utilisateur"

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