---
title: Conceptualiser ses bases
description: 
published: 1
date: 2022-08-21T21:57:38.146Z
tags: 
editor: markdown
dateCreated: 2022-08-21T06:40:54.432Z
---

# Conceptualiser ses bases de données

Comme indiqué dans la page précédente, il existe plusieurs façons de conceptualiser ses bases de données. Dont voici deux concepts : 
- Le Langage UML
- La méthode Merise

Nous commencerons par l'UML puis plus tard la méthode MERISE.

> La méthode merise est en cours de rédaction. **Elle sera disponible incessamment sous peu** !
{.is-danger}

## Le Langage de modélisation UML

### Définition

> l'**UML** (**Unified Modeling Language**) est un langage graphique de modélisation conçu pour *représenter*, *spécifier*, *construire* et *documenter* un système d'information et qui peut se substituer à d'autres méthodes. 
C'est donc un "métalangage" fournissant des éléments permettant de construire le modèle de votre projet.
{.is-success}

> l'**UML** n'est pas une **méthode**
{.is-warning}

> Un **Modèle** est une représentation abstraite et simplifiée, d'une entité du monde réel en vue de le décrire, de l'expliquer ou de le prévoir
{.is-success}

Mais pourquoi modéliser ? 🤔 Je vous dirais que c'est une bien belle question. 😁

Modéliser un système avant sa réalisation permet de mieux comprendre le fonctionnement du système. Il est connu par tous les membres de l'équipe et il est donc un vecteur privilégié pour communiquer 😉.

Quelques exemples de modèles : 

- Modèle Météorologique : permet de prévoir, à partir de données d'observation, les futurs conditions climatiques.

- Modèle Economomique : permet de simuler l'évolution de cours boursiers en fonction de certains facteurs (taux de croissance, % de chomage ...)

- Modèle démographique : définit la composition d’un panel d’une population et son comportement, dans le but de fiabiliser des études statistiques, etc.

### Historique 

En 1994, l'UML hérite de 3 méthodes  :
- OMT de James Rumbaugh
- OOD de Grady Booch
- OOSE d'Ivar Jacobson

UML 1.0 est proposé et normalisé en janvier 1997 par l'OMG (Object Management Group). La dernière version, 2.5.1, date de décembre 2017.
[https://www.omg.org/spec/UML/](https://www.omg.org/spec/UML/)


### Les diagrammes UML

L'UML permet de créer des diagrammes permettant de définir une application selon plusieurs points de vue (centrée sur les besoins des utilisateurs) : 
- Vue Fonctionnel (diagramme des cas d'utilisation)
- Vue Statique (diagrammes de classes, objets ...)
- Vue Dynamique (diagrammes de séquence, états, activité, interaction ...)
- Vue Implémentation (diagrammes de composants, déploiement ...)
- ect ...


Exemples : 

##### Exemples {.tabset}
###### Diagramme de cas d'utilisation 
```plantuml

:Utilisateur: as A
:Administrateur: as B
A <|-- B

(Envoyer des courriels) as E
(Gérer les comptes) as G
(Authentification) as AU

A - E
B - G
E .> AU : include
G .> AU : include
```
###### Diagramme de classes
```plantuml

:Utilisateur: as A
:Administrateur: as B
A <|-- B

(Envoyer des courriels) as E
(Gérer les comptes) as G
(Authentification) as AU

A - E
B - G
E .> AU : include
G .> AU : include
```



<!--### UML pour les Bases de données

Très utilisé pour facilité la conception de documents nécessaires au développement de logiciel orienté objet, nous allons nous concentrer sur 


## La Méthode MERISE -->
