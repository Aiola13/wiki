---
title: Protocoles du courrier électronique
description: 
published: 1
date: 2023-02-05T15:29:21.413Z
tags: 
editor: markdown
dateCreated: 2023-01-31T23:11:52.729Z
---

# Mais c’est quoi un protocole ? 

> Un protocole en informatique, c'est un ensemble de règles et de conventions que les ordinateurs doivent suivre pour pouvoir se parler et travailler ensemble sans se disputer 😡. C'est comme si vous étiez à une soirée et que tout le monde se mettait d'accord sur le fait de ne parler que dans une langue étrangère pour s'amuser. Les ordinateurs, eux, se mettent d'accord sur le protocole pour s'assurer que toutes les communications soient claires et efficaces.
{.is-success}

# Les protocoles du courrier électronique

|Protocole|Description|
| --- | :--- |
|**SMTP**|C'est le protocole de transport, il s'occupe aussi du format de l’entête, de ses champs ainsi que des adresses électronique|
|**MIME**|C'est le standard de formatage du corps des messages et des fichiers|
|**POP**|C'est un protocole de réception des messages|
|**IMAP**|C'est un protocole de réception des messages|

<!--
SMTP protocole de transport

Format de l’entête et des champs des adresses électroniques, utilise le standard MIME pour le formatage du corps des messages.
POP3 protocole de réception
IMAP protocole de réception, gestion de courrier ou des news dans des dossiers
SMTP (Simple Mail Transfer Protocol) [RFC 821 : 1982]
Encapsulation d’un message

Les messages de l'application (SMTP, POP, IMAP) sont encapsulés en segments TCP, qui sont ensuite encapsulés en paquets IP, puis en trames Ethernet, et finalement en bits sur la couche physique. La notion de couches est importante dans la pile TCP/IP.
Exemple d'une session SMTP

Session SMTP comprenant l'ouverture, la fermeture, et la transmission d'un message (sans les entêtes).
Requêtes et réponses SMTP

Commandes du client: HELO, MAIL FROM, RCPT TO, DATA, QUIT.
Réponses du serveur (exemple): <no> <texte en clair>.
Format des courriels - emails [RFC 822 : 1982]

Un courriel se compose de deux parties: l'entête et le corps.

Exemple de format d'un courriel:

makefile

From: cook@caramel.vn
To: eat@kangourous.co.au
Subject: rue de Charonne

Viens boire une Guiness ce soir
au cafe de la plage

-->