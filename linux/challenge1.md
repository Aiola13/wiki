---
title: Challenge 1
description: 
published: true
date: 2024-12-11T09:03:19.954Z
tags: 
editor: markdown
dateCreated: 2024-12-11T09:02:41.129Z
---

# Challenge 1 - Administration d'une distribution GNU/Linux


> Table des matières
> [1 Information système](#h-1-identifiants-de-connexion)
> [2 Créer des utilisateurs](#h-2-creation-de-comptes)
> [3 Installer des applications](#h-3-installer-des-applications)
> [4 Gestion des disques et partitions](#h-4-gestion-des-disques-et-partitions)
> [5 Gestion des permissions et droits](#h-5-gestion-des-permissions-et-droits)
> [6 Surveillance des serveurs](#h-6-surveillance-des-permissions-et-droits)
> [7 Diagnostique et résolution de problèmes](#h-7-diagnostique-et-resolution-de-problemes)
{.is-info}



## 1 - IDENTIFIANTS DE CONNEXION
Vous devez créer une machine virtuelle sous ALMA LINUX / ROCKY LINUX (basées toutes 2 sur CentOS) - installation minimale, avec ces informations :

| Identifiant | Mot de passe | Role |
|-------------|--------------|------|
| stag        | iop          | Utilisateur|
| root        | iop          | Super Admin |

<!--Login : "stag"
Password: "iop"
Login : "root"
Password : "iop"-->


## 2 - CREATION DE COMPTES

Objectifs :
> - Savoir gérer les comptes utilisateurs : création, modification, suppression
> - Savoir gérer les groupes : création, modification, suppression
> - Savoir gérer les fichiers liés aux utilisateurs : /etc/skel, /etc/profile, $HOME/.bashrc, … 
{.is-info}


### 2.1 - PARAMETRER L'ENVIRONNEMENT PAR DEFAUT

Les utilisateurs créés devront avoir les caractéristiques suivantes : 
- La commande `ping` fait 4 tests et quitte 
- La commande `rm` sera interactive sauf pour l'utilisateur root 
- La commande `nano` disposera des options suivantes : indentation automatique et affichage des numéros de ligne
- Chaque nouvel utilisateur aura les répertoires **Mes documents** et **Modèles** dans son répertoire personnel

### 2.2 - CREER DES COMPTES UTILISATEURS

Créer des comptes pour les utilisateurs François et Frédéric avec les caractéristiques suivantes :

|                      	| François                  	| Frédéric                                                          	|
|----------------------	|:---------------------------	|:-------------------------------------------------------------------	|
| Login                	| francois                  	| frederic                                                          	|
| Mot de passe         	| password                  	| AchAngEr                                                          	|
| Répertoire personnel 	| /home/francois            	| /home/fred                                                        	|
| Shell à utiliser     	| zsh                      	| bash                                                              	|
| Groupe principal     	| users                     	| par défaut                                                        	|
| Groupes secondaires  	| stagiaires, documentation 	| stagiaires, documentation                                         	|
| Autres paramètres    	|                           	| Le mot de passe sera à changer à la première ouverture de session 	|

Créer les groupes manquants si nécessaire.


## 3 - INSTALLATION D’APPLICATIONS

Objectifs :
- Configurer et utiliser les dépôts logiciels
- Connaître et exploiter les différentes méthodes d'installation : compilation, et yum
- Diagnostiquer et résoudre les problèmes de dépendances


### 3.1- METTRE A JOUR LE SYSTEME

**Vérification et mise à jour de la liste des dépôts**
En ligne de commande, vérifiez l'accès au dépôt d'ALMA LINUX / ROCKY LINUX.

**Mettre à jour le système**
Procédez à la mise à jour complète de votre système sans interaction avec vous. 

### 3.2 - INSTALLER DES FONCTIONNALITES

**Transformer une installation minimale en station de travail graphique**

1. Vérifier la présence des outils permettant une connexion SSH à distance sur le serveur. Les installer si nécessaire.
Tester cette connexion depuis votre poste physique.

2. Installer le groupe de paquets vous permettant d'avoir l'interface graphique par défaut d'ALMA LINUX / ROCKY LINUX. Vous utiliserez l’outil yum et ses commandes adaptées pour une installation manuelle du groupe de paquet.

**Installer rsync**

Installer à partir des sources la version de `rsync` disponible ici [https://rsync.samba.org](https://rsync.samba.org). Vous pouvez utiliser `wget` directement à partir de la machine virtuelle ou le logiciel `winscp` (présent sur distrib) pour transférer les sources de `rsync` de votre système hôte vers votre système ALMA LINUX / ROCKY LINUX.

> Le répertoire racine de l'installation de rsync sera /opt.
{.is-warning}

> Lancer la commande rsync avec l’option permettant d’afficher son numéro de version. Est-ce bien la version installée précédemment ?
Si non, comment expliquer et résoudre cette problématique ?
{.is-success}

## 4 - GESTION DES DISQUES ET PARTITIONS

Objectifs :
- Utiliser les commandes de partitionnement, de formatage et de montage
- Préparer et rendre disponible des volumes de stockage
- Gérer et modifier les volumes montés au démarrage

### 4.1 - PARTITIONNER MANUELLEMENT

Ajouter un disque dur de 40 GiB dont l’espace sera utilisé de la façon suivante :
- P1 : Une partition de 5 GiB qui accueillera les logs de votre système
- P2 : Une partition occupant l’espace disque restant pour le partitionnement LVM

### 4.2 - PREPARER ET METTRE EN SERVICE LES PARTITIONS

**Formater et utiliser les nouvelles partitions**

P1 – La partition est à nommer `LOG` et à formater en `ext4`. Elle vient décharger le répertoire /var de son dossier `log`. Ces données seront accessibles depuis `/var/log` ou `/root/logs`.

P2 – L'espace disque dévolu aux utilisateurs est insuffisant. Utiliser 30GiB du groupement de volume LVM pour générer un espace formaté en `ext4`. Il devra remplacer le répertoire /home existant. Ce système de fichier sera contrôlé tous les 60 montages ou tous les 60 jours.

> Les données devront être conservées et les modifications ne devront pas avoir d’impact sur les utilisateurs.
{.is-warning}

## 5 - GESTION DES DROITS UNIX

Objectifs :
- Comprendre les droits Unix de base et étendus
- Modifier la configuration des droits pour des utilisateurs et des groupes
- Mettre en place une structure de stockage aux accès sécurisés

### 5.1 - CREER UNE STRUCTURE DE STOCKAGE POUR LES UTILISATEURS

Définir et mettre en place les solutions pour répondre aux besoins suivants :

1. Un répertoire **/data/public** accessible en écriture pour tous les utilisateurs
2. Un répertoire **/data/depot** accessible en écriture pour tous les utilisateurs mais dans lequel seul l’utilisateur propriétaire du fichier pourra le supprimer
3. Un répertoire **/data/admin** accessible en écriture pour les administrateurs uniquement
4. Un répertoire **/data/documentation** accessible en lecture pour tous les utilisateurs et en écriture pour les gestionnaires de la documentation

Créer de nouveaux groupes et de nouveaux utilisateurs si nécessaire.

Tester les paramétrages avec les différents types de comptes utilisateurs (administrateur, utilisateur, gestionnaire de la documentation ...).

## 6 - SURVEILLANCE DES SERVEURS

Objectifs :
- Obtenir des informations pertinentes pour la surveillance des serveurs
- Organiser et définir une planification pour le suivi de ces informations

### 6.1 - DEFINIR LES COMMANDES DE SUPERVISION

Trouver les commandes adaptées pour afficher exclusivement les informations suivantes :
1. Le détail des volumes occupés sur les partitions montées
2. Les 10 processus qui consomment le plus de temps processeur

### 6.2 - PLANIFIER UNE TACHE DE SUPERVISION

Planifier la tache de supervision suivante :

De 9H30 à 12H00, tous les jours ouvrés, toutes les 20 minutes seront relevés les quantités de mémoire vive et de swap : libre, consommé et totales. Ces informations seront exprimées en MiB et devront être conservées pour la journée en cours dans le fichier **/root/suivi/conso_memoire.log**.

> Le résultat devra être affiché en direct sur une console de supervision (à identifier et conserver ouverte).
{.is-success}

## 7 - DIAGNOSTIQUE ET RESOLUTION DE PROBLEMES

Objectifs :
- Identifier la source d’une problématique et la résoudre 

### 7.1 - DIAGNOSTIQUER ET RESOUDRE DES DYSFONCTIONNEMENTS
Une machine virtuelle à dépanner est mis à votre disposition par le formateur.

Ci-dessous, sa configuration d'installation :
- Système : ALMA LINUX / ROCKY LINUX
- Partitionnement
	- Disque 1 – 20 GB
  | Partition Primaire 1 	| /boot 	| 500 MiB 	| xfs  	|
  |----------------------	|-------	|---------	|------	|
  | Partition Primaire 2 	| /     	| 9,8 GiB 	| xfs  	|
  | Partition Primaire 3 	| SWAP  	| 2 GiB   	| swap 	|
  | Partition Logique 1  	| /usr  	| 7,8 GiB 	| xfs  	|

	- Disque 2 – 40 GB
  | LVM	| /home 	| 40 GiB 	| xfs  	|
  |----	|-------	|---------	|------	|
  
- Identifiants
|  	    | Mot de passe 	|
|-------|-------------	|
| stag 	| iop     	    |
| root 	| iop  	        |


_Enoncé de la problématique :_
- Suite à une maintenance de ce poste pour effectuer la migration du répertoire /home dans un nouvel espace de type LVM, le système ne démarre plus.

_Actions à réaliser :_
- Effectuer et formaliser un diagnostic précis de la problématique rencontrée.
- Résoudre celle-ci puis s’assurer que l'utilisateur stag puisse se connecter correctement.