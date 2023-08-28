---
title: Protocoles du courrier électronique
description: 
published: 1
date: 2023-08-28T10:28:12.026Z
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
|**SMTP**|C'est le protocole de transport/d'envoi, il s'occupe aussi du format de l’entête, de ses champs ainsi que des adresses électronique|
|**MIME**|C'est le standard de formatage du corps des messages et des fichiers|
|**POP**|C'est un protocole de réception des messages|
|**IMAP**|C'est un protocole de réception des messages|

# Architecture générale

![protocol-min.png](/images/network/email/protocol-min.png){.align-center}

# Histoire & évolution de la messagerie

La messagerie électronique, souvent appelée email, a vu le jour dans les années 1960. Cependant, c'est dans les années 1970, avec l'apparition du protocole SMTP (Simple Mail Transfer Protocol), qu'elle s'est véritablement standardisée.

- Années 1960 : Les premières formes de communication électronique ont été développées pour les réseaux internes des universités et des institutions.
- Années 1970 : Ray Tomlinson introduit l'usage du symbole "@" pour séparer le nom d'utilisateur du nom de la machine, une norme qui est encore utilisée aujourd'hui.
- Années 1980-1990 : Avec la démocratisation d'Internet, l'email devient un outil de communication essentiel pour les entreprises et le grand public.
- Années 2000 à aujourd'hui : L'évolution de la mobilité et des smartphones a permis un accès permanent à la messagerie électronique, rendant l'email encore plus intégré à notre quotidien.

# Avantages et inconvénients
Avantages :

Rapidité : Les emails sont livrés presque instantanément, permettant une communication rapide à travers le monde.

Coût : Envoyer un email est généralement gratuit ou très peu coûteux, surtout en comparaison avec d'anciennes méthodes comme le fax ou la poste traditionnelle.

Flexibilité : Les emails peuvent être consultés de n'importe où et à tout moment, surtout avec l'avènement des smartphones et des tablettes.

Inconvénients :

Sécurité : Les emails peuvent être la cible de phishing, de logiciels malveillants et d'autres formes de cyberattaques.

Surcharge d'informations : Avec la facilité d'envoi, de nombreuses personnes reçoivent une quantité écrasante d'emails chaque jour, ce qui peut conduire à des informations importantes noyées dans un flot de messages non désirés.

Dépendance technologique : Bien que l'accès à l'email soit omniprésent, une panne de serveur, une perte de connexion ou un dysfonctionnement matériel peuvent interrompre l'accès.

# Parlons définitions

## Agent Utilisateur (User Agent)

> Un agent utilisateur (UA) est une application cliente. Cette application s'identifie à d'autres applications en échangeant une information sous forme de chaîne de caractères dans l'entête d'une requête HTTP, pernettant de donner plusieurs informations à propos de l'application cliente telle que le type de périphérique, adresse IP, système d'exploitation, navigateur, résolution, langue, adresse email originelle, serveur smtp ... 
{.is-success}

## Agent Utilisateur de Couriel (Mail User Agent)

> Un Agent Utilisateur de Courriel (MUA) représente le logiciel de messagerie qui fournit un environnement pour la gestion du courriel (envoi, saisie, réception, suppression, etc.)
{.is-success}

Par exemple :
- la fonction **mail** sous les systènes Unix mais ne traite pas le format MIME
- Netscape/Mozilla Thunderbird
- Outlook
- Interface Texte
- Webmail (via un navigateur) (Gmail)

## Agent de Transfert de Courriel (Message Tranfert Agent)


> Un Agent de transfert de Courriel (MTA) est le composant (logiciel)  faisant partie intégrante d'un serveur de transmission de messagerie (SMTP) et qui s'occupe de transmettre, transférer et router le message au destinataire. Lorsque vous envoyez un e-mail, votre MUA le transmet à un MTA pour qu'il soit délivré. Le MTA prend ensuite le relais pour s'assurer que le message est correctement routé vers le serveur de destination.
{.is-success}


> Il agit comme un centre de tri postal. Il décide en fonction de l’adresse du destinataire si ce courrier doit être envoyé à un autre centre de tri ou s’il doit être donné au facteur pour distribution local.
{.is-info}


- Chaque MTA est composé de deux agents :
    - Agent de routage des messages : détermine le chemin du message en fonction de l'adresse du destinataire.
    - Agent de transport des messages : reçoit un message et un chemin, et le transporte à l'endroit indiqué via le protocole SMTP (sur TCP/IP).


L'agent de transport des messages ne prend donc pas de décision de routage. Elle lui est indiquée par l'agent de routage qui lui transmet le message et le chemin.

par exemple : 
- Postfix, Sendmail et Exim sont des exemples de logiciels MTA.

---

## Agent Délivreurs de Courriel (Mail Delivery Agent) 

> Un Agent Délivreurs de Courriel (MDA) est un logiciel qui est chargé de livrer le courriel dans la boite aux lettres du destinataire. 
{.is-success}

> Ce logiciel gére le filtrage des courriels, la supprésion des spams (antispams) et les virus (antivirus). Mais il intervient également dans la gestion des problèmes comme un disque plein ou bien une corruption de la boîte aux lettres et signaler au MTA toute erreur dans la distribution.
{.is-info}

par exemple : 
- Dovecot est souvent utilisé comme MDA, en particulier en combinaison avec des MTA comme Postfix.

---

## Boite aux lettres

La boîte aux lettres est une localisation de stockage où les e-mails d'un utilisateur sont déposés et conservés.

- Identifie en quelque sorte le destinataire du message
- L'adresse de la boîte aux lettres est une chaîne de caractères ASCII (sauf "@", "<", ">", "," , ";", etc) : <local-part>@<domain>
    - Ex : letoutpuissan@paradis.pa - La partie locale est traitée localement
- Le domaine doit être de type FQDN : "Fully qualified domain name" (mail.exemple.com)
- Historiquement on faisait du "source routing", on indiquait la liste des serveurs de messagerie par lesquels passer pour parvenir au destinataire (il n'y avait pas de DNS).
<!--  
- Liste de diffusion (nom d'une liste de boites aux lettres)
  - Permet d'envoyer un message à plusieurs destinataires sans dupliquer
inutilement le contenu du message -->


---

# Architecture

![architecture-systeme-messagerie-electronique.jpg](/images/network/email/architecture-systeme-messagerie-electronique.jpg){.align-center}
  
---

# Processus 

Un processus typique d'envoi d'e-mail se déroulerait comme suit:

- L'utilisateur compose un e-mail dans son MUA (par exemple, Thunderbird).
- Une fois l'e-mail envoyé, il est transmis au MTA du serveur d'envoi (par exemple, Postfix).
- Le MTA route l'e-mail à travers Internet vers le MTA du serveur de destination.
- À l'arrivée, le MDA (par exemple, Dovecot) du serveur de réception prend le relais et dépose l'e-mail dans la boîte de réception de l'utilisateur final.
- L'utilisateur récupère et lit l'e-mail via son MUA.

 Ce processus garantit que les e-mails sont correctement acheminés à travers les nombreux systèmes et protocoles qui composent l'infrastructure de messagerie d'Internet.

---

# SMTP | protocole de transport
  
Un protocole de communication utilisé pour transférer les e-mails entre les serveurs et, éventuellement, vers le client final.
Histoire : Contexte de l'émergence du SMTP dans les premiers jours d'Internet.

Port standard : 25 (d'autres ports comme 587 sont aussi utilisés dans certains contextes)
Serveurs MX (Mail Exchange) : Serveurs dédiés à la réception des messages SMTP.

  Sessions SMTP
Processus d'établissement d'une connexion.
Commandes SMTP de base : HELO, MAIL FROM, RCPT TO, DATA, QUIT.
2.3. Transmission des messages

Format des e-mails : Entêtes et corps.
MIME (Multipurpose Internet Mail Extensions) : Extension du format de base pour inclure des pièces jointes, du texte au format HTML, etc.
  
## Comment communiquer avec le serveur SMTP ?
  
Format général d'une commande
 Une ligne de caractères ASCII (terminé par les 2 caractères <CRLF>)
 La ligne commence par un mot clef qui définit le type de la commande
 Certaines commandes sont optionnelles (cf. ESMTP)
 Cela peut être négocié lors de l'établissement
 Exemple:
 HELO <serveur> <CRLF>
 Remarque : insensible aux majuscules/minuscules
 Temporisateur :
 Par défaut 2 à 10 minutes en fonction des commandes
 Compatible avec la durée des temporisateurs de TCP
  
## Commandes
  
| **Commande**  | **Syntaxe**                                  | **Fonction**                                                                                    |
|---------------|----------------------------------------------|-------------------------------------------------------------------------------------------------|
| **EHLO**      | EHLO <domain> \[<SP> <add\-param>\]          | Demande d'établissement d'une session de messagerie SMTP avec le serveur du domaine cité        |
| **MAIL FROM** | MAIL FROM: <exp\-path> \[<SP> <add\-param>\] | Demande d'un envoi d'un message, Identification de l'expéditeur \(le chemin vers l'expéditeur\) |
| **RCPT TO**   | RCPT TO: <dest\-path> \[<SP> <add\-param>\]  | Demande d'un envoi d'un message, Identification de l'expéditeur \(le chemin vers l'expéditeur\) |
| **DATA**      | DATA                                         | Délimite le début du message                                                                    |
| **\.**        | \.                                           | Délimite la fin du message                                                                      |
| **QUIT**      | QUIT                                         | Demande de libération de la session                                                             |
| **RESET**     | RESET                                        | Annulation des commandes précédentes \(d'envoi d'un message, par ex\.\)                         |
| **HELP**      | HELP \[<string>\]                            | Le serveur retourne des informations utiles                                                     |
| **HELO**      | HELO <domain>                                | Demande d'établissement d'une session de messagerie avec commandes \(obsolète\)                 |
| **NOOP**      |                                              | "No operation"                                                                                  |
| **SEND**      | SEND FROM <exp\-path>                        | Envoi d'un message au terminal \(obsolète\)                                                     |
| **SOML**      | SOML FROM <exp\-path>                        | Envoi du message au terminal sinon au serveur responsable de la BAL \(obsolète\)                |
| **SAML**      | SAML FROM <exp\-path>                        | Envoi du message au terminal et au serveur responsable de la BAL \(obsolète\)                   |
| **VRFY**      | VRFY <string>                                | Vérification de la chaîne de caractères                                                         |
| **EXPN**      | EXPN <string>                                | Expansion de la chaîne de caractères                                                            |
| **TURN**      |                                              | Echange les rôles entre le client et le serveur                                                 |
| **X\.\.\.**   |                                              | Commande étendue définie localement                                                             |

## Code Retour
  
| **Code** | **Signification**                                                           |
|----------|-----------------------------------------------------------------------------|
| **250**  | Service action completed                                                    |
| **421**  | <domain> Service not available                                              |
| **221**  | <domain> Service closing                                                    |
| **220**  | <domain> Service ready                                                      |
| **214**  | Help message                                                                |
| **211**  | System status                                                               |
| **504**  | Parmeter not implemented                                                    |
| **502**  | bad sequence of commands                                                    |
| **501**  | Parameter syntax error                                                      |
| **500**  | Syntax error                                                                |
| **251**  | User not local; will forward to <forward\-path>                             |
| **252**  | Cannot VRFY user, but will accept message and attempt delivery              |
| **450**  | Requested mail action not taken: mailbox busy                               |
| **550**  | Requested action not taken: mailbox not found, no access for policy reasons |
| **451**  | Requested action aborted: error in processing                               |
| **551**  | User not local; please try <forward\-path>                                  |
| **452**  | Requested action not taken: insufficient system storage                     |
| **552**  | Requested mail action aborted: exceeded storage allocation                  |
| **354**  | Start mail input; end with <CRLF>\.<CRLF>                                   |
| **554**  | Transaction failed                                   |  
  
---

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