---
title: Le modèle OSI
description: 
published: true
date: 2024-12-08T10:52:50.852Z
tags: osi, modele
editor: markdown
dateCreated: 2024-12-08T10:52:50.852Z
---

![logo-osi.png](/images/network/osi/logo-osi.png){.align-center}

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

![model-osi-v1.png](/images/network/osi/model-osi-v1.png){.align-center}

> Les couches ne peuvent communiquer qu’entre elles (réseau / réseau, liaison / liaison mais pas liaison / transport).
{.is-info}


# Les couches
## Couche 7 - La couche d'Application

> Cette couche fait l’interface entre l’homme et la machine. 
{.is-success}


### Exemples de protocoles :
- **Navigateur web (firefox, safari,chrome…) :** Lorsque vous tapez une adresse comme www.example.com, le protocole HTTP (ou HTTPS) est utilisé pour demander et recevoir la page web.
- **Client de messsagerie (outlook, thunderbird…) :** L'envoi de mails passe par des protocoles comme SMTP (pour envoyer) ou IMAP/POP3 (pour recevoir).
- **Transfert de fichiers :** Lorsqu’un fichier est téléchargé ou envoyé, le protocole FTP (File Transfer Protocol) peut être utilisé.

### Compléments utiles :
- **Protocole DNS :** Ce protocole, souvent associé à cette couche, traduit les noms de domaine (ex. : www.google.com) en adresses IP compréhensibles par les machines.
- **Protocole Telnet ou SSH :** Ces protocoles permettent de se connecter à distance à un autre ordinateur pour le contrôler via une interface en ligne de commande.

> En résumé, cette couche est la plus proche de vous en tant qu’utilisateur, et c’est celle qui transforme vos actions (cliquer, écrire un e-mail, télécharger un fichier) en instructions compréhensibles pour le réseau.
{.is-info}



## Couche 6 - La couche de Présentation

> Cette couche s'occupe de la syntaxe et de la sémantique des informations échangées. Elle sert d’intermédiaire pour garantir que les données transmises entre les applications sont compréhensibles malgré d’éventuelles différences entre systèmes.
{.is-success}


### Principales fonctions :
- **Conversion de format :** Adaptation du format des données pour que l’application destinataire puisse les traiter (exemple : conversion d’un fichier texte d’ASCII à EBCDIC).
- **Cryptage/Décryptage :** Sécurisation des données via le chiffrement, comme avec le protocole SSL/TLS.
- **Compression/Décompression :** Réduction de la taille des données pour optimiser la transmission, par exemple avec les formats ZIP ou JPEG.

### Exemples de protocoles :
- SSL/TLS (sécurisation des communications)
- MIME (encodage des e-mails pour les pièces jointes)

## Couche 5 - La couche de Session

> La couche de session établit, maintient et termine les connexions entre deux applications. Elle gère les dialogues entre les systèmes pour assurer une communication fluide.
{.is-success}

### Principales fonctions :
- **Synchronisation :** Insertion de points de reprise pour éviter de tout recommencer en cas d’interruption.
- **Gestion des sessions :** Ouverture et fermeture des sessions de communication.
- **Contrôle des dialogues :** Détermination des modes d'échange (semi-duplex, full-duplex).

### Exemples de protocoles :
- NetBIOS (Network Basic Input/Output System)
- RPC (Remote Procedure Call)

## Couche 4 - La couche de Transport

> La couche de transport garantit le transfert fiable des données d’un point à un autre, même si le réseau sous-jacent est sujet à des erreurs.
{.is-success}


### Principales fonctions :
- **Segmentation et réassemblage :** Découpage des données en segments et réassemblage à l’arrivée.
- **Contrôle des flux :** Éviter la saturation de l’émetteur ou du récepteur.
- **Détection et correction des erreurs :** Gestion des pertes ou doublons de paquets.
- **Multiplexage :** Gestion de plusieurs connexions sur une seule ligne physique.

### Exemples de protocoles :
- TCP (Transmission Control Protocol, fiable)
- UDP (User Datagram Protocol, rapide mais non fiable)

## Couche 3 - La couche Réseau

> La couche réseau gère l’acheminement des données entre les équipements à travers différents réseaux intermédiaires.
{.is-success}


### Principales fonctions :
- **Adressage logique :** Attribution des adresses IP pour localiser les hôtes.
- **Routage :** Sélection du meilleur chemin pour acheminer les données d’une source à une destination.
- **Fragmentation et réassemblage :** Division des paquets pour s’adapter à la taille maximale des trames réseau.

### Exemples de protocoles :
- IPv4/IPv6 (protocole Internet)
- ICMP (Internet Control Message Protocol, pour diagnostiquer les pannes)
- OSPF, BGP (protocoles de routage)


## Couche 2 - La couche de Liaison de Données

> La couche de liaison de données assure un transfert fiable des données entre deux nœuds connectés directement.
{.is-success}


### Principales fonctions :
- **Encapsulation des trames :** Ajout d’une en-tête et d’une bande de contrôle pour vérifier l’intégrité.
- **Contrôle d’accès au média (MAC) :** Gestion des conflits lors de l’accès au support physique.
- **Détection et correction des erreurs :** Grâce au contrôle de redondance cyclique (CRC).

### Exemples de sous-couches :
- LLC (Logical Link Control) : Communication entre couches réseau et liaison.
- MAC (Media Access Control) : Gestion de l’accès au canal.

### Exemples de protocoles :
- Ethernet
- Wi-Fi (IEEE 802.11)
- PPP (Point-to-Point Protocol)

## Couche 1 - La couche Physique

> La couche physique concerne les aspects matériels de la transmission des données.
{.is-success}


### Principales fonctions :
- **Transmission binaire : **Conversion des données en signaux électriques, optiques ou radio.
- **Spécifications matérielles :** Définition des normes pour les câbles, connecteurs et autres composants physiques.
- **Topologie physique :** Organisation des dispositifs dans un réseau (bus, étoile, anneau).

### Exemples de technologies :
- Fibre optique
- Câble Ethernet (Cat 5e, Cat 6, Cat 7)
- Signaux radio (Wi-Fi, Bluetooth)

