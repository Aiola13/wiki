---
title: Le Cloud
description: 
published: 1
date: 2023-05-26T10:22:02.629Z
tags: 
editor: markdown
dateCreated: 2023-05-26T10:10:28.893Z
---

# Qu'est-ce que le NUAGE ?

## Introduction

> Cloud, Cloud ... On en entend beaucoup parlé mais chez moi il fait beau pourtant 🤔

|Le Cloud Computing, que nous appellerons par son petit nom : **Cloud**, était un soldat de la puissante compagnie **SHINRA**.|![](https://www.nautiljon.com/images/jeuxvideo_persos/00/58/cloud_strife_3185.jpg)|
|------|---------|

> Blague à part ...
Le cloud existe depuis bien longtemps, mais c'est avant tout un terme __*MARKETING*__. 

Tout d'abord, revenons à la base. Depuis les années 2000, nous pouvons faire tout un tas de chose sur internet, tel que acheter des jeux vidéo, commander des livres, lire des articles, ect ... Et ces demandes sont en constantes évolutions. Pour pouvoir gérer de plus en plus de clients, les entreprises ont dû investir dans des infrastructures de plus en plus grosses. Et justement, pour cela il faut des serveurs, vraiment beaucoup de serveurs.

Tous les sites sur lesquels vous vous rendez sont donc hébergés sur ces serveurs, qui sont eux mêmes regroupés dans des **Datacenters**.


> Voyez-vous le souci venir ? 

En informatique nous exploitons des ressources, qu'elles soient physiques ou virtuelles. Que ce soit écologiquement ou économiquement, l'idéal serait d'utiliser 80% de ces ressources. Or, il est très peu probable d'y arriver. En effet, nous dépendons des processus utilisés, des utilisateurs connectés, ect ...

Prenons un exemple, lors des "Black Friday", nous avons un pic de consommation de ressources. (Beaucoup d'utilisateurs qui se ruent vers les promotions). Quelle est alors la stratégie à tenir ? 
- Conserver un nombre de ressources fixes durant toute l'année, et tant pis pour les pics.
- Surévaluer les capactiés des serveurs, quitte à perdre des ressources et de l'argent.

Tout simplement, aucune des deux, on peut tout simplement moduler nos ressources, et c'est là tout l'avantage du Cloud.
Donc le Cloud Computing correspond à l'accès à des ressources, des services informatiques par rapport à la demande.

## Le Cloud Computing

Tout d'abord comment reconnaît-on un Cloud ?
Le National Institute of Standards and Technology (NIST), aux États-Unis, a défini cinq caractéristiques claires qui font d'un cloud, un cloud : 

- **On-demand Self-Service** (Libre-service à la demande)
L’utilisateur gère les ressources mis à disposition par le fournisseur provider, et paie en fonction de l’utilisation de ces ressources, il s’agit d’un paiement à l’utilisation.
- **Broad Network Access** (Large accès au réseau)
Déployer rapidement à l’échelle mondiale, si vous avez un client à l’étranger, il devrait y accéder avec une très faible latence.
- **Ressource Pooling** (Mise en commun des ressources)
En créant une infrastructure partagée avec d’autres clients vous pouvez réaliser des économies d’échelles plus importantes
- **Rapid Elasticity** (Elasticité rapide)
L’élisticité représente la capacité du système à s’adapter aux demandes en approvisionnant et en désapprovisionnant des ressources de manière automatique.
- **Measured Service** (Service mesuré)
Sécuriser le service par une détection immédiate d’une surcharge ou inversement, si l’une de ces conditions est vérifié, c’est à l’elasticité de prendre en charge cela.


## Les Types (modèles) de cloud

- **IaaS** (Infrastructure as a Service)
Un prestataire vous fournit un accès à tout ou partie de son infrastructure technique.
- **STaaS** (Storage as a Service)
Un prestataire vous fournit un espace de stockage variable en fonction des besoins.
- **PaaS** (Platform as a Service)
La même chose que le IaaS, mais en plus le prestataire s'occupe de gérer le nombre de machines nécessaires au fonctionnement de votre application ainsi que les outils nécessaires à son bon fonctionnement.
- **DaaS** (Desktop as a Service)
Un prestataire fournit des postes de travail virtuels aux utilisateurs finaux via Internet, sous licence avec un abonnement à l’utilisateur. 
- **FaaS** (Function as a Service)
Le prestataire fournit un ensemble de serveur qui permet aux utilisateurs de développer des applications et de déployer des fonctionnalités (sans gérer de serveur). Le concept est également connu sous l'appellation serverless.
- **SaaS** (Software as a Service)
Le prestataire fournit l'accès à l'écosystème d'un logiciel sous forme de service. (Ex: Office 365)

![types_cloud.png](/images/cloud/types_cloud.png)

![offres_cloud.png](/images/cloud/offres_cloud.png)

## En résumé

La force :
- La force du cloud est : "Modularité et Flexibilité"
- Location de ressources automatisées
- MindState : Pay As You Go
- Responsabilité partagée avec le fournisseur (problèmes techniques bas niveau)

Les limites : 
- Respectez les règles émises par le prestataire (Pas de stockage de fichier si pas de STaaS
- Changement de prestataire limité
- Dépendant du prestataire
