---
title: ECF
description: 
published: 1
date: 2022-09-15T07:25:24.559Z
tags: 
editor: markdown
dateCreated: 2022-09-14T21:23:20.849Z
---

# ECF - GNU/Linux

Objectifs :
- Savoir gérer les comptes utilisateurs, les groupes et les fichiers
- Configurer et utiliser les dépôts logiciels
- Comprendre et modifier la configuration des droits

## 1 - IDENTIFIANTS DE CONNEXION
Vous devez créer une machine virtuelle sous Debian - installation minimale, avec ces informations :
Login : "stag"
Password: "iop"
Login : "root"
Password : "iop"


## 2 - CREATION DE COMPTES

Les utilisateurs créés devront avoir les caractéristiques suivantes : 
- La commande `ping` fait 4 tests et quitte 
- La commande `rm` sera interactive sauf pour l'utilisateur root 
- Chaque nouvel utilisateur aura les répertoires **Mes documents** et **Modèles** dans son répertoire personnel



Créer les groupes suivants : **sshuser**, **ftpuser**

Créer les utilisateurs pim, pam et poum avec les caractéristiques suivantes :
|                      	| Darth Vader                 | R2D2                                                          			|
|----------------------	|:---------------------------	|:-------------------------------------------------------------------	|
| Login                	| vader                  			| rrdd                                                          			|
| Mot de passe         	| mort                  			| B!Pbip22                                                         		|
| Répertoire personnel 	| /home/vader            			| /home/rrdd                                                  				|
| Shell à utiliser     	| csh                      		| bash                                                              	|
| Groupe principal     	| sshuser                     | ftpuser                                                        			|
| Groupes secondaires  	| stagiaires, documentation 	| stagiaires, documentation                                         	|

Créer les groupes manquants si nécessaire.


## 3 - INSTALLATION D’APPLICATIONS

Définir et mettre en place les solutions pour répondre aux besoins suivants :

1. Serveur à jour
2. un serveur SSH
3. un serveur FTP
4. Bonne pratique en terme de sécurité
5. Seuls les groupes autorisés pourront utiliser les services correspondants.


<!-- Vérifier et mettre à jour la liste des dépôts, puis mettre à jour le système.

Installer un serveur SSH ci ne n'est pas le cas. Faites de même avec un serveur FTP. Et adapter les meilleurs règles de sécurité.
Faire en sorte que seul le groupe **sshuser** puisse se connecter en **SSH** et que seul le groupe **ftpuser** puisse se connecter en **FTP** -->

## 4 - GESTION DES DROITS UNIX


Définir et mettre en place les solutions pour répondre aux besoins suivants :

1. Un répertoire **/data/public** accessible en écriture pour tous les utilisateurs
2. Un répertoire **/data/depot** accessible en écriture pour tous les utilisateurs mais dans lequel seul l’utilisateur propriétaire du fichier pourra le supprimer

Créer de nouveaux groupes et de nouveaux utilisateurs si nécessaire.

## 5 - TEST

Tester les paramétrages avec les différents types de comptes utilisateurs (administrateur, utilisateur ...).