---
title: Notions de base
description: 
published: 1
date: 2024-11-29T00:38:08.729Z
tags: base, notion, php
editor: markdown
dateCreated: 2023-01-18T21:06:55.552Z
---

# Historique

> Rasmus Lerdorf, un programmeur Groenlandais avec la nationalité canadienne, crée PHP (Personnal Home Page Tools), initialement une bibliothèque de scripts Perl, en 1994 pour noter et analyser les connexions/acces sur son CV en ligne. Il réalise les 2 premières moutures du langage (v1 et v2). En 1997, deux étudiants, Andi Gutmans et Zeev Suraski, reprennent le moteur, il en sortira PHP 3.0 puis les outils Zend.
{.is-success}

> La version stable actuelle de PHP est la 8.2.1, sortie le 8 Décembre 2022. La version 7 est sortie en Décembre 2015 et il n’y a jamais eu de version 6 ! PHP 8.3 est prévu pour décembre 2023.
{.is-info}


> PHP Signifie **Hypertext Pre Processor**
{.is-success}

> Plus de 300 millions de sites sont réalisés en PHP à travers le monde !
{.is-success}

# Fonctionnement

L’interpréteur lit un fichier source .php puis génère un flux de sortie avec les règles suivantes :

- toute ligne située à l’extérieur d’un bloc PHP ( entre <?php et ?>) est recopiée inchangée dans le flux de sortie

- le code PHP est interprété et génère éventuellement des résultats intégrés eux aussi au flux de sortie

- les erreurs éventuelles donnent lieu à des messages d’erreurs qu’on retrouve également dans le flux de sortie (selon la configuration du serveur)

- une page html pure sauvegardée avec l’extension .php sera donc non modifiée et renvoyée telle quelle …

![fonctionnement_php.png](/images/php/fonctionnement_php.png){.align-center}

# Installation

> Pour travailler avec PHP, plusieurs outils sont indispensables, notamment :
{.is-success}

## Logiciel spécifique

| un serveur web                | **Apache** ou Nginx                                              |
|:----------------------------- | --------------------------------------------------- |
| un interpréteur de script PHP | Zend Engine ou autre                                        |
| un serveur de base de donnée  | MySQL, MariaDB, PostGres ...                                              |

Heureusement, 

Nous avons de la chance ... 💡, il existe une solution simplifiée : des logiciels tout-en-un qui incluent à la fois :

- un serveur web
- un interpréteur de script PHP
- un serveur de base de donnée 

Voici une liste des options disponibles selon votre système d'exploitation :

| Plateforme | Solution intégrée                |
|:----------:|:---------------------------------|
| Windows    | **[Laragon](https://laragon.org)** à préférer ou **[WAMP](https://www.wampserver.com)** |
| Mac        | **[MAMP](https://www.mamp.info/en/downloads/)**                         |
| Linux      | **LAMP**                         |
| Multi-plateforme | **[XAMPP](https://www.apachefriends.org/fr/index.html)**                |




## Utiliser Docker
L’utilisation de Docker permet de spécifier très précisément les dépendances souhaitées pour un projet et aussi de tester ce projet sur différentes plateformes et avec différentes versions de PHP.

Voir par exemple le site Formation Docker qui propose des docker-compose pour des environnements de développement en PHP.

# Notions de bases

## Intégration d'un script dans une page

Les pages contenant du php doivent porter l'extension **.php**. Voici comment insérer du code PHP dans du HTML : `<?php ... ?>`

```php
<?php
  $sTexteHtml = '<p>Bonjour, voici ma première page</p>';
?>
<!doctype html>
<html lang="fr">
  <head>
    <meta charset="utf-8">
    <title>Titre de la page</title>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>
  <body>
    <?php
      echo $sTexteHtml;
    ?>
  </body>
</html>
```

## Les commentaires

Un script PHP se commente comme dans beaucoup de langage, tels que C ou javascript :

```php
<?php
  // commentaire sur une ligne
  /* commentaire
    sur plusieurs
    lignes */
  #commentaires comme en shell
?>
```

> ⚠️ Comme pour tous les langages, il est vivement conseillé de commenter ses scripts.
{.is-warning}


---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/php/data)