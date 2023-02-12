---
title: Le modèle OSI
description: 
published: 1
date: 2023-02-12T15:05:11.413Z
tags: 
editor: markdown
dateCreated: 2023-02-10T22:23:48.843Z
---

![osi.png](/images/network/osi/osi.png){.align-center}

# Présentation

> Le modèle OSI (Open Systems Interconnection) est un modèle proposé par l’ISO (Organisation Internationale de Normalisation) qui décrit les composants et les fonctionnalités nécessaires à la communication des données.
{.is-success}


Le principe du modèle OSI est de cadrer le protocole TCP/IP. Il est basé sur 7 couches de communication qui s'empilent conceptuellement de bas en haut :

- Physique
- Liaison des données
- Réseau
- Transport
- Session
- Présentation
- Application

![osi_model_v1.png](/images/network/osi/osi_model_v1.png){.align-center}

> Les couches ne peuvent communiquer qu’entre elles (réseau / réseau, liaison / liaison mais pas liaison / transport).
{.is-info}


# Les couches
## Couche 7 - La couche d'Application

Cette couche fait l’interface entre l’homme et la machine. 

Par exemple, votre navigateur (firefox, safari,chrome…), votre client de messsagerie (outlook, thunderbird…) sont des applications qui transfèrent des messages / des informations via la couche 7.

Lorsqu'un message est reçu sur le logiciel client, c'est la couche application qui le présente à l'utilisateur.

Les protocoles d'application comprennent le SMTP (Simple Mail Transfer Protocol) et le HTTP, qui est le protocole de communication entre les navigateurs et les serveurs Web.



## Couche 6 - La couche de Présentation

## Couche 5 - La couche de Session

## Couche 4 - La couche de Transport

## Couche 3 - La couche Réseau

## Couche 2 - La couche de Liaison de Données

## Couche 1 - La couche Physique

