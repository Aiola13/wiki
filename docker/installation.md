---
title: Installation de Docker
description: 
published: true
date: 2024-12-11T08:39:25.331Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:39:25.331Z
---

# Docker Desktop

> Docker Desktop est une application qui s'installe en un clic dans votre environnement Mac, Linux ou Windows et qui vous permet de créer, de partager et d'exécuter des applications et des microservices conteneurisés.
> 
> Elle offre une interface graphique directe qui vous permet de gérer vos conteneurs, vos applications et vos images directement depuis votre machine.
{.is-success}

## Docker Pour Windows

Pour faire fonctionner Docker sous Windows, nous aurions de nombreuses manipulations à faire... Cependant, Docker Desktop permet d'automatiser et de simplifier grandement la tache et ainsi d'avoir rapidement Docker sous Windows.

Docker Desktop va vous créer une machine virtuelle Hyper-V sur votre Windows, et procéder à l'installation de Docker au sein de celui-ci.

Attention, vous devez avoir un Windows Enterprise ou Windows Professional pour que cette fonctionnalité soit disponible. Dans le cas contraire.

Vous devez vous rendre sur cette page et télécharger la version "Stable" de Docker for Windows.

Une fois le téléchargement réalisé, vous pourrez lancer l'utilitaire et suivre la procédure d'installation de celui-ci. Attention, vous devrez certainement redémarrer votre PC.

Vous avez maintenant un Docker for Windows totalement fonctionnel sur votre PC !

## Docker pour Mac

L'installation de Docker pour Mac fonctionne comme pour Docker pour Windows.

Vous devrez télécharger l'utilitaire à cette adresse.

Cependant je vous recommande l'installation et l'utilisation de Docker Engine.

## Docker pour Linux

L'installation de Docker pour Linux fonctionne comme pour Docker pour Windows.

Vous devrez télécharger l'utilitaire à cette adresse.

Cependant je vous recommande l'installation et l'utilisation de Docker Engine.


# Docker Engine

> Docker Engine est le moteur de conteneurisation open source permettant de construire et de conteneuriser vos applications. Docker Engine agit comme une application client-serveur avec :
> 
> - un serveur doté d'un processus démon de longue durée, Dockerd.
> - Des API qui spécifient les interfaces que les programmes peuvent utiliser pour communiquer avec le démon Docker et lui donner des instructions.
> - Une interface de ligne de commande (CLI) client docker.
> - La CLI utilise les API Docker pour contrôler ou interagir avec le démon Docker par le biais de scripts ou de commandes CLI directes. De nombreuses autres applications Docker utilisent l'API et la CLI sous-jacentes. Le démon crée et gère les objets Docker, tels que les images, les conteneurs, les réseaux et les volumes.
> 
{.is-success}

## Docker pour Windows

Malheuresement Docker Engine n'est pas disponible en tant que tel sous Windows ...

Cependant, il y a un moyen de le forcer un peu. En utilisant le WSL (Windows SubSystem Linux ou en français, le Sous-Système Windows pour Linux).

Pour ce faire, il faut se rendre dans l'outil Windows "Activer ou désactiver des fonctionnalités Windows", et cocher la case en face de "Sous-Système Windows pour Linux" et de "Plateforme de l'hyperviseur Windows" ainsi que "Plateforme de machine virtuelle"

De cette manière docker pourra fonctionner correctement sous windows (enfin ... sous Linux mais dans Windows)

## Docker pour Mac

Pour installer Docker Engine sur Mac, suivez les instructions à cette adresse : 



## Docker pour Linux

Pour installer Docker Engine sur Linux, suivez les instructions à cette adresse : 

# Docker Hub

> Le Docker Hub est un service fourni par Docker Inc ; vous pouvez le comparer à GitHub, mais spécialisé dans le stockage d'image pour Docker.
{.is-success}
