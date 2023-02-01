---
title: Protocole Email
description: 
published: 1
date: 2023-02-01T01:24:48.816Z
tags: 
editor: markdown
dateCreated: 2023-01-31T23:11:52.729Z
---

# Protocole du courrier électronique


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

ChatGPT Jan 30 Version. Free Research Preview. Our goal is to make AI systems more natural and safe to interact with. Your feedback will help us improve.