---
title: Notions de base
description: 
published: true
date: 2024-12-31T12:02:37.124Z
tags: 
editor: markdown
dateCreated: 2024-12-31T12:02:37.124Z
---

# Kézako ??
## Définitions

> La **SQL** (**Structured Query Language**) est un langage de programmation servant à exploiter et gérer des bases de données (BDD), il est intégré dans les SGBDR. 
{.is-success}

> Une **BDD** (**Base de données**) est un ensemble structuré de données (comme un tableau excel) administrée par une SGBD. 
{.is-success}

> Une **SGBD** (**Système de Gestion de Base de Données**) est un ensemble de logiciels permettant la recherche (sélection), la mise à jour, l'ajout et la suppression de données stockées sur une mémoire. Ce groupe de quatre opérations courantes, base de toute manipulation de données, est appelé **CRUD** pour Create, Read, Update, Delete. {.is-success}

> Ses caractéristiques : 
> - Centraliser l'information
> - Manipulation facile des données
> - Assurer l'indépendance données/traitements
> - Partager l'information entre différents utilisateurs
> - Préserver la cohérence des données
> - Assurer la sécurité des données

## Types

Il existe 2 principales familles de SGBD : 
- **SGBD Relationnelles** (SGBDR): SQL (MariaDB, MySQL, Postgresql, Oracle…)
 	- SQL
  - Intégré à Xampp, Wamp, … (MariaDB, MySQL)
  - Ensemble cohérent de données dans un tableau, avec des relations, contraintes entre les données
  - Absence de redondances (découpage, clé, etc.)
  
---
  
- **SGBD Non Relationnelles**: NoSQL (MongoDB, Firestore, Redis… )
	- NoSQL (Not Only SQL)
  - Ensemble de clé-valeur | Orienté graphe
  - Gère de très gros volumes
  - Ensemble de documents sans forcément avoir de structure identique.
  - Redondances possibles (voire encouragés)


Les SGBD-R sont les plus utilisés sur le Web, les SGBD NoSQL servant essentiellement au traitement des Big Datas. Dans cette formation, nous nous concentrerons sur les SGBD relationnels (SGBD-R), et utiliserons plus particulièrement le SGBD MySQL|MariaDB.


## Modélisation

> Il est très important, qu'avant de se jeter tête baissée comme un bourrin dans le développement, de se poser et de réfléchir à comment on va créer notre base et agencer nos données.
{.is-warning}

Pour cela, il existe plusieurs façons de conceptualiser une base de donnée : 
- ***Le langage UML***
- ***La méthode MERISE***

### Le langage UML

> l'**UML** (**Unified Modeling Language**) est un langage de modélisation utilisé pour décrire les traitements et les données d'un système non seulement en SQL mais pour tout langage POO.
{.is-success}



<!--- Diagramme peuvent être abordés de façon indépendante
- Philosophie qui peut permettre pour modéliser une BDD
pour et contre

Diagramme de classse > MPD > LDD
La conception du diagramme de classe UML est une étape
importante vers la création des BDD, mais il faut ensuite
implémenter ce diagramme dans un SGBDR.
Il existe deux étapes pour arriver à la création des tables à
partir du diagramme de classe:
BD
Du MCD aux tables
1. Création du Modèle Physique des Données (MPD);
2. Création du script SQL de génération des tables à l'aide du
Langage de Définition de Données (LDD); -->





### La méthode Merise

> **MERISE** est une méthode d'analyse et de conceptualisation.
{.is-success}

Il possède plusieurs modèles (étapes) pour modéliser des données : 
- Modèle Conceptuel de Données (MCD) -> Abstrait qui est une représentation graphique des informations
- Modèle Logique de Données (MLD)
- Modèle Physique de Données (MPD) -> Script SQL

> Méthode qu'il faut normalement suivre étape par étape.
{.is-warning}



Nous reviendrons dessus sur le chapitre suivant 

## Outils


Et puis ?

Comme pour tous sites, nous devons utiliser un serveur pour pouvoir abriter nos données et donc notre base de données 😁.
Je vous laisse deviner ? 🙄 … **WampServer** 

> WampServer : Où j’aurais pu dire XAMPP, LAMP (pour Linux) ou MAMP (pour MAC), est un environnement web intégrant plusieurs serveurs (Apache, MySQL & MariaDB) et un interpréteur de script PHP fonctionnant localement sur la machine.
Lien : http://wampserver.aviatechno.net/?lang=fr
{.is-info}




| Une fois installé, Wamp se glisse dans la barre des tâches / notifications en bas à droite et doit être vert pour indiquer le bon lancement de l’ensemble de ses services. | ![logo-tray-wamp-resizer.jpg](/images/sql/logo-tray-wamp-resizer.jpg) |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|

Via clique gauche, vous retrouvez ces informations,
 - **Localhost** : L'accès à votre serveur web (votre page d'accueil index.php/html
 - **My Projects** : L'ensemble de vos projets
 - **phpMyAdmin** : Est l’accès aux bases de données de vos sites web. Par défaut, l’identifiant est root est il n’y a pas de mot de passe.
 - **Répertoire www** : L'ensemble de vos fichiers via l'explorateur Windows
 - **Apache** : Les fichiers de configuration du serveur web Apache
 - **PHP** : Les fichiers de configuration de l'interpréteur PHP
 - **MySQ**L : Les fichiers de configuration concernant MySQL

> PS : Lors de son utilisation sur un environnement professionnel, ne pas laisser les accès par défaut et créer des utilisateurs. -->