---
title: Protocoles du courrier électronique
description: 
published: 1
date: 2023-02-05T22:45:21.806Z
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

# Parlons définitions

## Agent Utilisateur (User Agent)

> Un agent utilisateur (UA) est une application cliente. Cette application s'identifie à d'autres applications en échangeant une information sous forme de chaîne de caractères dans l'entête d'une requête HTTP, pernettant de donner plusieurs informations à propos de l'application cliente telle que le type de périphérique, adresse IP, système d'exploitation, navigateur, résolution, langue, adresse email originelle, serveur smtp ... 
{.is-success}

## Agent Utilisateur de Couriel (Mail User Agent)

> Un Agent Utilisateur de Courriel (MUA) représente le logiciel de messagerie utilisé.
{.is-success}

Par exemple :
- la fonction **mail** sous les systènes Unix mais ne traite pas le format MIME
- Netscape/Mozilla Thunderbird
- Outlook
- Interface Texte
- Webmail (via un navigateur)

## Agent de Transfert de Courriel (Mail Tranfert Agent)

> Un Agent de transfert de Courriel (MTA) 
{.is-success}

MTA - 

- Agit comme un centre de tri postal. Il décide en fonction de l’adresse du destinataire si ce courrier doit être envoyé à un qutre centre de tri ou s’il doit être donné au facteur pour distribution local.


- Chaque MTA est composé de deux agents :
    - Agent de routage des messages : détermine le chemin du message en fonction de l'adresse du destinataire.
    - Agent de transport des messages : reçoit un message et un chemin, et le transporte à l'endroit indiqué via le protocole SMTP (sur TCP/IP).


L'agent de transport des messages ne prend donc pas de décision de routage. Elle lui est indiquée par l'agent de routage qui lui transmet le message et le chemin.

---

## MDA - Agents Délivreurs de Courriel

- Il joue le rôle de facteur
- Il distribue les courriers dans le réseau local, ce qui revient à remettre physiquement le courrier entrant dans les boîtes aux lettres des destinataires.
- Il ne prend aucune décision de routage.
<!--- Comme MDA, on peut citer « /bin/mail » ou « procmail -->


---

## Mémoire de messages

- Boîte aux lettres (ou mailbox) : fichier texte.
- Sur les systèmes Unix, c’est un fichier dans /var/spool/mail/login ou encore dans /var/mail/login.
- Dans un tel fichier, tout nouveau message débute par une ligne From (sans caractère « : »). Cette ligne sert à délimiter les différents message

---

## Boite aux lettres

Endroit où le message doit être déposé :
- Identifie en quelque sorte le destinataire du message
- L'adresse de la boîte aux lettres est une chaîne de caractères ASCII (sauf "@", "<", ">", "," , ";", etc) : local-part>@<domain
    - Ex : letoutpuissan@paradis.pa - La partie locale est traitée localement
- Le domaine doit être de type FQDN : "Fully qualified domain name"

<!-- La notation entre crochets
 Ex : Bernard Cousin <bcousin@ifsic.univ-rennes1.fr> -->
- Historiquement on faisait du "source routing", on indiquait la liste des serveurs de messagerie par lesquels passer pour parvenir au destinataire (il n'y avait pas de DNS).
- Liste de diffusion (nom d'une liste de boites aux lettres)
    - Permet d'envoyer un message à plusieurs destinataires sans dupliquer
inutilement le contenu du message



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