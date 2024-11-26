---
title: Protocoles du courrier électronique
description: 
published: 1
date: 2024-11-26T22:55:21.607Z
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

- **Années 1960 :** Les premières formes de communication électronique ont été développées pour les réseaux internes des universités et des institutions.
- **Années 1970 :** Ray Tomlinson introduit l'usage du symbole "@" pour séparer le nom d'utilisateur du nom de la machine, une norme qui est encore utilisée aujourd'hui.
- **Années 1980-1990 :** Avec la démocratisation d'Internet, l'email devient un outil de communication essentiel pour les entreprises et le grand public.
- **Années 2000 à aujourd'hui :** L'évolution de la mobilité et des smartphones a permis un accès permanent à la messagerie électronique, rendant l'email encore plus intégré à notre quotidien.

# Avantages et inconvénients
1. ***Avantages :***
  - **Rapidité :** Les emails sont livrés presque instantanément, permettant une communication rapide à travers le monde.
  - **Coût :** Envoyer un email est généralement gratuit ou très peu coûteux, surtout en comparaison avec d'anciennes méthodes comme le fax ou la poste traditionnelle.
  - **Flexibilité :** Les emails peuvent être consultés de n'importe où et à tout moment, surtout avec l'avènement des smartphones et des tablettes.

2. ***Inconvénients :***
  - **Sécurité :** Les emails peuvent être la cible de phishing, de logiciels malveillants et d'autres formes de cyberattaques.
  - **Surcharge d'informations :** Avec la facilité d'envoi, de nombreuses personnes reçoivent une quantité écrasante d'emails chaque jour, ce qui peut conduire à des informations importantes noyées dans un flot de messages non désirés.
  - **Dépendance technologique :** Bien que l'accès à l'email soit omniprésent, une panne de serveur, une perte de connexion ou un dysfonctionnement matériel peuvent interrompre l'accès.


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

# SMTP | (Simple Mail Transfer Protocol) [RFC 821 : 1982]
  
Un protocole de communication utilisé pour transférer les e-mails entre les serveurs et, éventuellement, vers le client final.

Port standard : 25 (d'autres ports comme 587 sont aussi utilisés dans certains contextes)

## Commnent s'établit une connexion/session SMTP ?

La connexion ou session SMTP s'établit en suivant un protocole précis et une suite de commandes pour assurer la transmission d'emails en utilisant le protocole de communication `TELNET`.

### Format général d'une commande
 - Une ligne de caractères ASCII (terminé par les 2 caractères <CRLF>)
 - La ligne commence par un mot clef qui définit le type de la commande
 - Certaines commandes sont optionnelles
 - Cela peut être négocié lors de l'établissement
 - Exemple: `HELO <serveur> <CRLF>`
>  Remarque : insensible aux majuscules/minuscules
>  Temporisateur :
>  Par défaut 2 à 10 minutes en fonction des commandes
{.is-info}

  
### Etapes
## Tabs {.tabset}
### Simplifié

1. **Connexion**: 
   - Le client se connecte au serveur SMTP sur le port 25 (non sécurisé) ou 587 (sécurisé).
2. **Salutation**: 
   - Le client envoie `HELO` ou `EHLO` pour se présenter.
3. **Sécurité (si nécessaire)**: 
   - Le client demande `STARTTLS` pour sécuriser la connexion.
   - Le serveur accepte, et la connexion devient chiffrée.
4. **Authentification**: 
   - Le client fournit son nom d'utilisateur et son mot de passe.
   - Le serveur vérifie et confirme si l'authentification est réussie.
5. **Envoi de l'e-mail**: 
   - Le client indique l'expéditeur (`MAIL FROM:`) et le destinataire (`RCPT TO:`).
   - Le client envoie le contenu de l'e-mail avec `DATA` et termine avec un point (`.`).
   - Le serveur confirme la réception.
6. **Fin de la session**: 
   - Le client envoie `QUIT` pour terminer la connexion.
   - Le serveur confirme la déconnexion.

### Compléte

1. **Établissement de la connexion TCP**:
   - Le client établit une connexion TCP avec le serveur SMTP sur le port 25, qui est le port par défaut pour la communication non sécurisée. Pour une communication sécurisée, le port 587 est souvent utilisé.
2. **Salutation**:
   - Une fois la connexion TCP établie, le serveur envoie un code de réponse `220` indiquant qu'il est prêt à accepter les commandes.
   - Le client envoie une commande `HELO` ou `EHLO` pour se présenter au serveur. La commande `EHLO` est une version étendue de `HELO` et est préférée dans les communications modernes.
   - Le serveur répond avec un code `250` et énumère souvent les fonctionnalités qu'il prend en charge.
3. **Négociation de sécurité (si nécessaire)**:
   - Si la connexion doit être sécurisée, le client demande à passer en mode sécurisé avec la commande `STARTTLS`.
   - Le serveur accepte avec un code `220`, et le client et le serveur négocient alors une connexion chiffrée.
4. **Authentification**:
   - Pour envoyer des emails via un serveur SMTP qui nécessite une authentification, le client doit fournir des informations d'identité.
   - Le client envoie la commande `AUTH`, suivie de la méthode d'authentification, comme `LOGIN` ou `PLAIN`.
   - Le serveur demande alors le nom d'utilisateur et le mot de passe, généralement sous forme encodée en base64.
   - Si l'authentification réussit, le serveur envoie un code `235` pour signifier l'acceptation.
5. **Transmission de l'e-mail**:
   - Le client indique l'expéditeur de l'e-mail avec la commande `MAIL FROM:<adresse-email>`. Le serveur répond généralement avec un code `250` s'il accepte.
   - Le client indique le destinataire de l'e-mail avec la commande `RCPT TO:<adresse-email>`. Le serveur confirme de la même manière.
   - Pour envoyer le corps de l'e-mail, le client utilise la commande `DATA`. Le serveur répond avec un code `354` pour signifier qu'il est prêt à recevoir les données.
   - Le client envoie alors le contenu de l'e-mail, suivi d'une ligne contenant uniquement un point (`.`) pour signifier la fin du contenu.
   - Si tout se passe bien, le serveur envoie un code `250` pour confirmer la réception.
6. **Terminer la session**:
   - Après avoir envoyé le courriel, le client envoie la commande `QUIT` pour terminer la session.
   - Le serveur confirme la fin de la session avec un code `221`.

### Exemple
  
```telnet
Étape 1: Connexion au serveur SMTP
Commande utilisateur: telnet smtp.gmail.com 587

Réponse du serveur: 
220 smtp.gmail.com ESMTP x123sm2131234pfa.123 - gsmtp

---

Étape 2: Salutation (HELO/EHLO)
Commande utilisateur: EHLO mondomaine.com

Réponse du serveur:
250-smtp.gmail.com at your service
250-SIZE 35882577
250-8BITMIME
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-CHUNKING
250 SMTPUTF8

---

Étape 3: Mise en place d'une connexion sécurisée (optionnel pour certains serveurs, mais nécessaire pour Gmail)
Commande utilisateur: STARTTLS

Réponse du serveur:
220 2.0.0 Ready to start TLS

(Note: À ce stade, la communication sera chiffrée, donc les commandes telnet en clair ne fonctionneront plus. Pour de vraies interactions, un client devrait passer à une connexion sécurisée.)

---

Étape 4: Authentification
(Note: Puisque la connexion est sécurisée, les commandes sont simplifiées pour l'illustration. Dans une vraie situation, l'utilisateur aurait à fournir des informations d'authentification encodées en base64.)
Commande utilisateur: AUTH LOGIN

Réponse du serveur:
334 VXNlcm5hbWU6

Commande utilisateur: [Votre nom d'utilisateur encodé en base64]

Réponse du serveur:
334 UGFzc3dvcmQ6

Commande utilisateur: [Votre mot de passe encodé en base64]

Réponse du serveur:
235 2.7.0 Accepted

---

Étape 5: Envoi de l'e-mail
Commande utilisateur: MAIL FROM:<votre@email.com>

Réponse du serveur:
250 2.1.0 OK x123sm2131234pfa.123 - gsmtp

Commande utilisateur: RCPT TO:<destinataire@email.com>

Réponse du serveur:
250 2.1.5 OK x123sm2131234pfa.123 - gsmtp

Commande utilisateur: DATA

Réponse du serveur:
354  Go ahead x123sm2131234pfa.123 - gsmtp

Commande utilisateur:
Subject: Test via Telnet

Ceci est un test.

.

---

Étape 6: Quitter la session SMTP
Commande utilisateur: QUIT

Réponse du serveur:
221 2.0.0 closing connection x123sm2131234pfa.123 - gsmtp
```

### Exemple 2
Installer OPENSSL : slproweb.com/products/Win32OpenSSL.html
Puis via PowerShell ou le cmd, vous placer dans le dossier OpenSSL
Ou via winget avec la commande : `winget install "openssl light"`
  
```telnet
Étape 1: Connexion au serveur SMTP
Commande utilisateur: .\openssl s_client -starttls smtp -connect smtp-mail.outlook.com:587 -ign_eof

Réponse du serveur: 
220 smtp-mail.outlook.com ESMTP x123sm2131234pfa.123 - gsmtp

---

Étape 2: Salutation (HELO/EHLO)
Commande utilisateur: EHLO outlook.com

Réponse du serveur:
250-smtp-mail.outlook.com at your service
250-SIZE 35882577
250-8BITMIME
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-CHUNKING
250 SMTPUTF8

---

Étape 3: Authentification
(Note: Puisque la connexion est sécurisée, les commandes sont simplifiées pour l'illustration. Dans une vraie situation, l'utilisateur aurait à fournir des informations d'authentification encodées en base64.)
Commande utilisateur: AUTH LOGIN

Réponse du serveur:
334 VXNlcm5hbWU6

Commande utilisateur: [Votre nom d'utilisateur encodé en base64]

Réponse du serveur:
334 UGFzc3dvcmQ6

Commande utilisateur: [Votre mot de passe encodé en base64]

Réponse du serveur:
235 2.7.0 Accepted

---

Étape 4: Envoi de l'e-mail
Commande utilisateur: MAIL FROM:<votre@email.com>

Réponse du serveur:
250 2.1.0 OK x123sm2131234pfa.123 - gsmtp

Commande utilisateur: RCPT TO:<destinataire@email.com>

Réponse du serveur:
250 2.1.5 OK x123sm2131234pfa.123 - gsmtp

Commande utilisateur: DATA

Réponse du serveur:
354  Go ahead x123sm2131234pfa.123 - gsmtp

Commande utilisateur:
Subject: Test via Telnet

Ceci est un test.

.

---

Étape 5: Quitter la session SMTP
Commande utilisateur: QUIT

Réponse du serveur:
221 2.0.0 closing connection x123sm2131234pfa.123 - gsmtp
```
  
## Tabs {.tabset}
### Commandes
  
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
{.dense}
  
### Réponse SMTP
  
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
{.dense}
  
<!--## Encapsulation d’un message

Les messages de l'application (SMTP, POP, IMAP) sont encapsulés en segments TCP, qui sont ensuite encapsulés en paquets IP, puis en trames Ethernet, et finalement en bits sur la couche physique. La notion de couches est importante dans la pile TCP/IP.-->

## Transmission des messages et Format des courriels - emails [RFC 822 : 1982]

Un courriel se compose de deux parties: l'entête et le corps.

Exemple de format d'un courriel:

## Tabs {.tabset}
### Exemple 1

```makefile

From: cook@caramel.vn
To: eat@kangourous.co.au
Subject: rue de Charonne

Viens boire une Guiness ce soir
au cafe de la plage
```

### Exemple 2

```makefile
Delivered-To: hello@kangourous.co.au
Date: Thu, 21 Mar 2023 15:15:39 +0100
From: Cook <cook@caramel.vn>
Organization: Kangoo
X-Accept-Language: fr
MIME-Version: 1.0
To: eat@kangourous.co.au
Cc: ALBANESE Anthony  <anthony.albanese@gov.au>
Subject: rue de Charonne
```
  
  
  
# MIME | Multipurpose Internet Mail Extensions [RFC 2045-2046 : 1996]
  
<!-- MIME (Multipurpose Internet Mail Extensions) : Extension du format de base pour inclure des pièces jointes, du texte au format HTML, etc. -->
  
Le MIME, acronyme de **Multipurpose Internet Mail Extensions**, est une norme qui a été développée dans le but d'étendre les capacités des e-mails pour permettre le transport de contenus autres que du texte brut ASCII, comme des fichiers binaires, des images et des caractères non-ASCII. 

Avant l'introduction de MIME, les e-mails étaient limités à des caractères ASCII simples, ce qui rendait difficile le transfert d'autres types de données.

Voici quelques points clés concernant MIME:

1. **Types et sous-types**: MIME introduit le concept de types et de sous-types pour définir la nature des données. Par exemple, une image JPEG serait typée comme `image/jpeg`, où `image` est le type et `jpeg` est le sous-type.

2. **Encodage des données binaires**: Étant donné que les systèmes de messagerie traditionnels étaient conçus pour transporter du texte, MIME a introduit plusieurs méthodes pour encoder des données binaires en texte, afin qu'elles puissent être transportées par des systèmes de messagerie. L'encodage le plus courant est "base64".

3. **En-têtes MIME**: Pour indiquer qu'un e-mail utilise MIME, et pour fournir d'autres métadonnées (comme le type de contenu et l'encodage), des en-têtes MIME sont ajoutés à l'e-mail. Des en-têtes tels que `Content-Type` et `Content-Transfer-Encoding` sont couramment utilisés.

4. **Multi-part MIME**: Permet d'envoyer des messages composés de plusieurs parties, chacune avec son propre type de contenu. Ceci est souvent utilisé pour les e-mails contenant à la fois une version texte et une version HTML du même message, ou pour les e-mails avec des pièces jointes. Chaque partie est séparée par une "frontière" (boundary) définie.

5. **Extensions**: MIME a été étendu pour être utilisé au-delà des e-mails. Par exemple, le protocole HTTP utilise également des en-têtes MIME pour spécifier le type de données retournées par un serveur web.

6. **Caractères non-ASCII**: MIME permet également d'encoder des caractères non-ASCII pour qu'ils puissent être transportés de manière sécurisée. Cela permet, par exemple, d'envoyer des e-mails en différentes langues et scripts.

Un exemple simple de contenu MIME multi-parties serait :

```plaintext
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="frontiere"

--frontiere
Content-Type: text/plain

Ceci est la partie texte de l'e-mail.

--frontiere
Content-Type: image/jpeg [types/sous-types; paramètres
optionnels]
Content-Transfer-Encoding: base64 [Spécifie le codage]

[Réel contenu encodé en base64 de l'image]

--frontiere--
```

## Exemple d'encocage

- 8bits:
Viens boire une Guiness ce soir
au café de la plage
- base64
VmllbnMgYm9pcmUgdW5lIEd1aW5lc3MgY2U
gc29pciBhdSBjYWbpIGRlIGxhIHBsYWdlDQ
  
## Tableau MIME
  
| **Type**    | **Sous\-Type** | **Description** |
|-------------|----------------|-----------------|
| text        | plain, html    | Sans format, Document HTML   |
| image       | jpeg, png, gif |                 |
| video       | mpeg, webm     |                 |
| application | octet\-stream  |  Document en binaire               |
| message     | external\-body |   Message sera téléchargé à la demande              |
| multipart   | mixed          |  parties dans des formats divers               |
{.dense}

>   Pour aller voir plus loin : https://developer.mozilla.org/fr/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types
{.is-info}

