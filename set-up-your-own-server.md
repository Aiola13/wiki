---
title: Créer son propre serveur
description: 
published: 1
date: 2024-06-10T13:18:25.873Z
tags: 
editor: markdown
dateCreated: 2024-06-10T13:18:25.873Z
---

# Introduction : Pourquoi vouloir créer son propre serveur ?

Outre que cela soit un beau projet et intérésant pour développer ses connaissances perosnnelles, il a ammène aussi un vrai plus auprès des professionnels pour témoigner de vos connaissances ainsi que de vos motivations. Mais il existe plusieurs autres avantages : 

1. Contrôle Total
	- Personnalisation : Vous pouvez configurer votre serveur exactement comme vous le souhaitez, installer les logiciels de votre choix, et ajuster les paramètres selon vos besoins spécifiques.
	- Gestion des Ressources : Vous avez le contrôle total sur l'allocation des ressources (CPU, RAM, stockage), ce qui vous permet d'optimiser les performances pour vos applications.
2. Flexibilité
	- Multiples Services : Avec votre propre serveur, vous pouvez héberger plusieurs services et applications, comme des sites web, des bases de données, des applications métier, des serveurs de messagerie, etc.
	- Virtualisation : Utiliser des technologies comme Proxmox permet de créer plusieurs machines virtuelles sur un seul serveur physique, offrant une grande flexibilité pour tester et déployer différentes configurations et environnements.
3. Sécurité
	- Contrôle de la Sécurité : Vous pouvez mettre en œuvre vos propres politiques de sécurité, pare-feu, et mesures de protection des données.
	- Isolation : Les machines virtuelles permettent d'isoler les différentes applications et services, réduisant le risque qu'un problème sur une application n'affecte les autres.
4. Performances
	- Pas de Ressources Partagées : Contrairement à l'hébergement mutualisé, vous ne partagez pas les ressources avec d'autres utilisateurs, ce qui garantit des performances stables.
  
  
  
# Choix d'un serveur dédié
  
Pourquoi un serveur dédié herbergé ? Tout simplement parce que : 

- Je n'ai pas de place chez moi
- Le prix de l'éléctricité augmente
- Prix des pièces de rechange si une panne quelconque arrive

Une fois ces avantages mis en avant, il faut choisir un hébergeur pour son serveur dédié ? Il en existe plusieurs : 

- Scaleway
- OVH
- Ikoula
- Hostinger
- PlanetHoster
- Infomaniak
- IONOS by 1&1

J'ai personnellement choisi l'offre Low Cost de OVH, Kimsufi, pour son rapport qualité/prix.
LIEN

# Installation de Promox sur le serveur Dédié

Accéder au serveur via KVM ou IPMI :

Connectez-vous à l'interface de gestion OVH et rendez-vous dans l'onglet Bare Metal Cloud puis sur le menu Serveur Dédié > Tous mes serveurs.

Pour installer Promox, sélectionner dans la vue de droite Système d'exploitation (OS) et dans le menu à 3 points choisisser Installer.
Suivez les instructions à l'écran pour installer Proxmox VE.

Configurer le réseau :
Une fois Proxmox installé, configurez le réseau pour accéder à l'interface web de Proxmox.

Accéder à l'interface web de Proxmox :
Utilisez un navigateur pour accéder à l'interface web de Proxmox : `https://<ip-du-serveur>:8006`.
  
# Configuration de Promox

  
<!-- Installation d'un Serveur Dédié chez OVH avec Proxmox et OpenMediaVault
Cette procédure décrit les étapes nécessaires pour installer un serveur dédié chez OVH, y configurer Proxmox pour la gestion des machines virtuelles (VM), et créer une machine virtuelle sous OpenMediaVault (OMV) pour la gestion du stockage et des services courants tels que Jellyfin et Wiki.js, exécutés dans des conteneurs Docker. Un reverse proxy (swag) sera également configuré pour faciliter l'accès aux services via des sous-domaines.

Objectif
Installer Proxmox sur un serveur dédié OVH.
Créer une VM sous Proxmox pour OMV.
Configurer Docker sur OMV pour gérer Jellyfin, Wiki.js et d'autres services.
Mettre en place un reverse proxy swag pour accéder aux services via des sous-domaines.
Pré-requis
Un serveur dédié chez OVH.
Un nom de domaine configuré pour pointer vers l'IP du serveur dédié.
Accès SSH au serveur.
Connaissance de base en administration Linux et réseau.
Étapes de l'installation -->

# Création d'une VM OMV

2. Création d'une VM sous Proxmox pour OMV

Télécharger l'image ISO de OpenMediaVault (OMV), OMV est basé sur Debian 

Créer une nouvelle VM dans Proxmox :
Dans l'interface web de Proxmox, créez une nouvelle VM en utilisant l'image ISO de OMV.


Installer Debian sur la VM :
Suivez les instructions pour installer Debian sur la VM.


3. Configuration de Docker sur OMV
Installer Docker :

Sur la VM OMV, exécutez les commandes suivantes pour installer Docker :
sh
Copier le code
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
Installer Docker Compose :

Installez Docker Compose en utilisant les commandes suivantes :
sh
Copier le code
sudo apt-get install -y python3-pip
sudo pip3 install docker-compose

4. Déploiement des Services (Jellyfin, Wiki.js, etc.) via Docker
Créer un fichier docker-compose.yml :

Créez un fichier docker-compose.yml pour gérer vos services. Exemple :
yaml
Copier le code
version: '3'
services:
  jellyfin:
    image: jellyfin/jellyfin
    container_name: jellyfin
    volumes:
      - /path/to/config:/config
      - /path/to/media:/media
    ports:
      - 8096:8096
  wikijs:
    image: requarks/wiki
    container_name: wikijs
    ports:
      - "3000:3000"
    volumes:
      - /path/to/config:/var/wiki
    environment:
      - DB_TYPE=sqlite
      - DB_FILE=/var/wiki/wiki.db
Lancer Docker Compose :

Dans le répertoire contenant le fichier docker-compose.yml, exécutez :
sh
Copier le code
docker-compose up -d

5. Configuration du Reverse Proxy (swag)
Installer swag (Secure Web Application Gateway) :

Ajoutez swag à votre docker-compose.yml :
yaml
Copier le code
version: '3'
services:
  swag:
    image: linuxserver/swag
    container_name: swag
    cap_add:
      - NET_ADMIN
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Paris
      - URL=yourdomain.ovh
      - SUBDOMAINS=wildcard
      - VALIDATION=dns
      - DNSPLUGIN=cloudflare
      - EMAIL=youremail@example.com
    volumes:
      - /path/to/config:/config
    ports:
      - 443:443
      - 80:80
Configurer les sous-domaines :

Dans le répertoire de configuration de swag, créez des fichiers de configuration pour chaque service dans /path/to/config/nginx/proxy-confs.
Redémarrer les services :

Exécutez docker-compose up -d pour redémarrer les services et appliquer la configuration du reverse proxy.
Finalisation
Accéder aux services :
Vous pouvez maintenant accéder à vos services via les sous-domaines configurés (ex : jellyfin.votre-domaine.ovh, wikijs.votre-domaine.ovh).
Conclusion
Cette procédure couvre l'installation et la configuration d'un serveur dédié chez OVH avec Proxmox, la création d'une VM pour OMV, et la mise en place de services courants sous Docker avec un reverse proxy pour une gestion simplifiée des accès. Assurez-vous de sécuriser votre installation en appliquant les meilleures pratiques de sécurité pour Proxmox, Docker et les services hébergés.

#