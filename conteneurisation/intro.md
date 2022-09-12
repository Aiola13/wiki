---
title: Présentation
description: 
published: 1
date: 2022-09-12T10:24:55.407Z
tags: 
editor: markdown
dateCreated: 2022-09-08T13:30:00.323Z
---

## Introduction
Docker est initialement un projet Open-Source distribué depuis mars 2013 qui permet de concevoir, tester et déployer des applications. Mais il désigne également les outils issus de ce projet, l'entreprise Docker Inc. qui est le principal soutien de ce projeéainsi que les outils que l'entreprise prend en charge.  Docker est la plateforme de conteneurisation la plus utilisée avec présentement plus de 13 500 forks et 1 700 contributeurs sur leur page Github. Il est tellement devenu populaire en quelques années qu'il se voit intérégé nativement dans les NAS et certains systèmes.


Dans l'ensemble les conteneurs et les microservices sont de plus en plus utilisés pour le développement et le déploiement d'application. C'est ce qu'on appelle le developpement "Cloud-Native".


Maintenant que l’historique (plutôt récent) est fait, nous allons pouvoir aborder la question de l’intérêt de Docker. 


## Les conteneurs

Mais avant de rentrer dans le vif du sujet avec Docker, parlons "Conteneurs".

Un conteneur, en informatique (bien sur), est un ensemble de processus qui sont isolés du reste du système hôte. Le conteneur s'éxécute à partir d'une image (un peu comme un ISO) contenant tous les élèments / fichiers dont les bibliothèques, les outils système, le code, l'environnement d'exécution et les dépendances nécessaires à son exécution.

Avec ce système vous pouvez facilement déployer et dimensioner des applications dans n'importe quel environnement, avec l'assurance que l'application s'exécutera correctement et de la même manière.

Un autre aspect très avantageux est leur isolation. Les conteneurs sont isolés de l'OS, ils partagent le même noyaux mais sont complétement indépendants les uns des autres que cela soit au niveau ressource qu'au niveau réseau.

Vu qu'ils n'embarquent pas d'OS, les conteneurs sont également très légers en se basant sur les ressources déjà existantes sur l'OS hôte là ou les VMs classiques virtualisent un OS entier avec donc ses pilotes, des périphériques.

![monolith_2-vm-vs-containers.78f841efba175556d82f64d1779eb8b725de398d.png](/images/conteneurisation/monolith_2-vm-vs-containers.78f841efba175556d82f64d1779eb8b725de398d.png)

## Et Docker ?

> **Build, Ship, and Run Any App, Anywhere**

Cette phrase résume à elle seule la philosophie de *Docker*.

Docker est un peu un "Hyperviseur" de conteneurs. Grâce à lui vous pourrez déploiyer et gérer très facilement vos applications.

L'architecture de Dockeéest divisée en 3 parties : 
- **Docker_client**
Contient le Daemon de Docker, qui instencie un conteneur à partir d'une image.
- **Docker_host**
Est une application en CLI permettant la communication entre l'utilisateur et le daemon.
- **Registry**
Est un serveur qui permet de gérer le stockage, l'envoi, la récupération des images Docker.