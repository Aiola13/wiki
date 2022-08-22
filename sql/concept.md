---
title: Conceptualiser ses bases
description: 
published: 1
date: 2022-08-22T06:16:30.891Z
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

Les premières méthodes d'analyse arrivent aux alentours des années 70 avec une découpe plutôt cartésienne (fonctionnelle et hiérarchique) d'un système.
Puis dans les années 80, les méthodes se rapprco

Et enfin, dans les années 90, l'émergence des méthodes objet, avec une question : 
- Comment structurer un système sans centrer l'analyse uniquement sur les données ou uniquement sur les traitements (mais sur les deux) ?

Plus de 50 méthodes objet sont apparues durant cette période (Booch, Classe-Relation, Fusion, HOOD, OMT, OOA, OOD, OOM ...) sans pour autant qu'il y en ait une qui s'impose.

En 1994, une premier consensus, l'UML hérite de 3 méthodes  :
- OMT de James Rumbaugh : Vue statiques, dynamiques et fonctionnelles d'un système (R&D de General Electric)
- OOD de Grady Booch : Vue logiques et physiques du système
- OOSE d'Ivar Jacobson : couvre tout le cycle de développement (R&D d'Ericsson) en se reposant sur l'analyse des besoins utilisateurs

UML 1.0 est proposé et normalisé en janvier 1997 par l'OMG (Object Management Group). La dernière version, 2.5.1, date de décembre 2017.
[https://www.omg.org/spec/UML/](https://www.omg.org/spec/UML/)


### Les diagrammes UML

L'UML permet de créer des diagrammes permettant de définir une application selon plusieurs points de vue :

- Vue Statique (ou structurelles) :
	- diagramme de classe 
  - diagramme d'objets 
  - diagramme de composants 
  - diagramme de déploiement 
  - diagramme de paquetage
  - diagramme de structures composites
- Vue Dynamique (ou comportementales) :
	- diagramme de cas d'utilisation
  - diagramme d'activités
  - diagramme d'états-transitions
  - diagrammes d'interaction
  	- diagramme de séquence
    - diagramme de communication
    - diagramme global d'intéraction
   	- diagramme de temps


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

left to right direction
class Commandes  {
  date : string
  prepaye : boolean
  nombre : integer
  prix : float
  envoyer()
	terminer()
}

class Client {
   nom : string
   adresse : string
   montantCredit() : int
}

Commandes "*" -- "1" Client : Association

```



### UML pour les Bases de données

Très utilisé pour facilité la conception de documents nécessaires au développement de logiciel orienté objet, nous allons nous concentrer sur 


## La Méthode MERISE
