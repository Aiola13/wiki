---
title: Challenge 1
description: 
published: 1
date: 2022-09-06T21:43:58.851Z
tags: 
editor: markdown
dateCreated: 2022-09-06T21:43:58.851Z
---

# Challenge 1 - Administration d'une distribution GNU/Linux


> Table des matières
1 Information système
2 Créer des utilisateurs 
2.1 Paramétrer l'environnement par défaut 
2.2 Créer des comptes utilisateurs 
3 Installer des applications 
3.1 Mettre à jour le système 
3.2 Installer des fonctionnalités 
4 Gestion des disques et partitions 
4.1 Partitionner manuellement 
4.2 Préparer et mettre en service les partitions 
5 Gestion des permissions et droits 
5.1 Créer une structure de stockage pour les utilisateurs 
6 Surveillance des serveurs
6.1 Définir les commandes de supervision 
6.2 Planifier une tache de supervision 
7 Diagnostique et résolution de problèmes 
7.1 Diagnostiquer et résoudre des dysfonctionnements 


## 1 - IDENTIFIANTS DE CONNEXION
Vous avez à disposition une machine virtuelle LINUX - installation minimale.
Login : "stag"
Password: "iop"
Login : "root"
Password : "iop"


## 2 - CREATION DE COMPTES

Objectifs :
- Savoir gérer les comptes utilisateurs : création, modification, suppression
- Savoir gérer les groupes : création, modification, suppression
- Savoir gérer les fichiers liés aux utilisateurs : /etc/skel, /etc/profile, $HOME/.bashrc, …


### 2.1 - PARAMETRER L'ENVIRONNEMENT PAR DEFAUT

Les utilisateurs créés devront avoir les caractéristiques suivantes : 
- La commande `ping` fait 4 tests et quitte 
- La commande `rm` sera interactive sauf pour l'utilisateur root 
- La commande `vi` disposera des options suivantes : indentation automatique et affichage des numéros de ligne
- Chaque nouvel utilisateur aura les répertoires **Mes documents** et **Modèles** dans son répertoire personnel

### 2.2 - CREER DES COMPTES UTILISATEURS

Créer des comptes pour les utilisateurs François et Frédéric avec les caractéristiques suivantes :

|François|Frédéric|
|:--------:|:--------:|
|