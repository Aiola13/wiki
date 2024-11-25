---
title: Créer son propre serveur
description: 
published: 1
date: 2024-11-25T10:43:05.050Z
tags: 
editor: markdown
dateCreated: 2024-06-10T13:18:25.873Z
---

# Introduction : Pourquoi vouloir créer son propre serveur ?

> Eh bien, pourquoi pas ? C’est un super projet pour se lancer, apprendre plein de trucs, et montrer aux pros que vous n’êtes pas là pour rigoler. En plus, c’est carrément stylé de dire : "Oui, j’ai mon propre serveur." Mais ce n’est pas juste pour se la raconter, il y a plein d’avantages à faire ça. Allez, on vous explique tout :
{.is-info}



1. Contrôle Total
	- Faites ce que vous voulez ! (Personnalisation) : Vous pouvez configurer votre serveur exactement comme vous l’aimez, installer les applis qui vous plaisent, et bidouiller jusqu’à ce que tout soit parfait pour vos besoins.
	- Des ressources rien que pour vous (Gestion des Ressources) : Besoin de plus de puissance ? Moins ? C’est vous le patron ! CPU, RAM, stockage : vous gérez tout comme un pro (ou un gamer exigeant).

2. Flexibilité à gogo
	- Multi-tâches au max : Hébergez un site, une base de données, un serveur de jeu, ou même un serveur mail. Pourquoi choisir quand on peut tout faire ?
	- La magie de la virtualisation : Avec des outils comme Proxmox, vous transformez un serveur en plusieurs petits serveurs virtuels. Ça veut dire plus d’expériences, plus de tests, et encore plus de fun.

3. La sécurité, comme un boss
	- Zéro stress : C’est vous qui gérez la sécurité. Firewall, mots de passe béton, et politique maison, tout est sous votre contrôle.
	- Chacun chez soi (Isolation) : Avec les machines virtuelles, chaque service est isolé. Si quelque chose plante, le reste continue de tourner tranquille.

4. Des performances au top
	- Pas de coloc relou : Contrairement à l’hébergement mutualisé, vous ne partagez rien avec personne, pas de Ressources Partagées . Tout est à vous, et vos applis tournent à fond tout le temps. Parfait pour les performances !
  
  
  
# Choisir un serveur dédié

## Pourquoi et comment ?


> Alors, pourquoi opter pour un serveur dédié hébergé plutôt qu’un petit serveur qui trône fièrement à côté de votre box internet ? Voici les raisons évidentes :
> 
> - Pas de place chez moi : Votre appart est déjà un Tetris géant. Pas envie de rajouter une tour bruyante.
> - Le prix de l’électricité : Spoiler : ça monte. Héberger un serveur chez soi, c’est un peu comme garder une lampe allumée en permanence, sauf que la lampe consomme comme un chauffage.
> - Les pannes coûtent cher : Disque dur qui claque ? Alim qui rend l’âme ? Ce n’est pas donné, et ça tombe toujours au mauvais moment.
> 
> ‎
{.is-success}


## Les hébergeurs à considérer
> Une fois convaincu que déléguer l’hébergement, c’est plus cool, il faut choisir son hébergeur. Voici quelques options bien connues :
> 
> - Scaleway
> - OVH
> - Ikoula
> - Hostinger
> - PlanetHoster
> - Infomaniak
> - IONOS by 1&1
>
> ‎
{.is-success}


De mon côté, j’ai choisi l’offre Low Cost Kimsufi d’OVH, qui propose un excellent rapport qualité/prix pour démarrer sans exploser le budget.
https://eco.ovhcloud.com/fr/kimsufi/

# Installation de Promox sur un serveur Dédié

Et maintenant, passons aux choses sérieuses : l’installation de Proxmox. Pas de panique, c’est simple comme bonjour. Voici les étapes :

1. Accéder au serveur via KVM ou IPMI :
	- Connectez-vous à l’interface de gestion OVH.
	-	Allez dans l’onglet Bare Metal Cloud, puis dans Serveur Dédié > Tous mes serveurs.

2. Installer Proxmox
	- Dans la vue de droite, cliquez sur Système d’exploitation (OS).
	- Ouvrez le menu à trois petits points (les fameux "…" qu’on adore) et choisissez Installer.![install-proxmox-01.png](/images/myownserver/install-proxmox-01.png)
	- Suivez les instructions affichées à l’écran pour installer Proxmox VE.  ![install-proxmox-02.png](/images/myownserver/install-proxmox-02.png)
  
3. Configurer le réseau
	- Une fois l’installation terminée, configurez le réseau pour que votre serveur soit accessible via l’interface web.

4. Accéder à l’interface web de Proxmox
- Dans votre navigateur préféré, tapez : https://<ip-du-serveur>:8006.

  
Admirez votre Proxmox tout beau, prêt à être configuré.

![install-proxmox-03.png](/images/myownserver/install-proxmox-03.png)
  
# Configuration de Promox

> Proxmox, c’est notre chef d’orchestre pour gérer les machines virtuelles (VM). Mais Proxmox lui-même ne fait pas grand-chose d’autre que superviser. Donc, si on veut qu’une de nos VM joue le rôle de serveur (par exemple, un serveur web), il faut que les requêtes qui arrivent sur Proxmox soient redirigées vers cette fameuse VM. 🎯
> 
> C’est là qu’intervient le port forwarding (ou redirection de port, pour les intimes). En gros, tu dis à Proxmox :
> "Hey, si quelqu’un toque à la porte 443 (HTTPS), envoie-le voir cette VM, c’est elle qui gère !"
> Et pour ça, on ajoute des règles de NAT (traduction d’adresses réseau). Le NAT, c’est le truc qui fait passer tout ça en douceur entre le monde extérieur (Internet) et ton réseau local.
> 
> Tu verras dans la config qu’on utilise iptables pour faire tout ça. Ça paraît complexe, mais en gros :
> 
> 	- Le NAT, c’est comme un interprète entre deux langues (Internet ↔ LAN).
> 	- Le port forwarding, c’est un peu comme pointer le doigt vers la bonne personne à l’intérieur de la maison. 👈
>   
> Bref, avec tout ça en place, ta VM devient le vrai serveur visible depuis Internet ! 🎉
{.is-success}

  
> Bon, on va mettre les mains dans le cambouis pour configurer le réseau de notre Proxmox. Respire un bon coup, et c'est parti ! 🔧
{.is-info}


## Étape 1 : Modifier les interfaces réseau

1. Pour commencer, on édite le fichier de configuration des interfaces réseau avec notre fidèle commande :

```bash
  sudo nano /etc/network/interfaces
```

Là-dedans, tu vas trouver un fichier ressemblant à une recette de cuisine technique. Voici à quoi ça ressemble (on t'explique après) :
  
```bash
# network interface settings; autogenerated
# Please do NOT modify this file directly, unless you know what
# you're doing.
#
# If you want to manage parts of the network configuration manually,
# please utilize the 'source' or 'source-directory' directives to do
# so.
# PVE will preserve these directives, but will NOT read its network
# configuration from sourced files, so do not attempt to move any of
# the PVE managed interfaces into external files!

auto lo 
iface lo inet loopback  # Boucle locale : elle est toujours là, elle fait son job.

iface eno1 inet manual # Ton interface physique principale. On lui dit : "Reste cool, on s'occupe de toi."

# Interface vmbr0 : ton lien vers l’extérieur (WAN)
auto vmbr0
iface vmbr0 inet static
        address <ip-du-serveur>/24 # Ton IP publique
        gateway <ip-passerelle> # La porte de sortie vers Internet
  			bridge-ports eno1          # On lie ça à l'interface physique eno1
        bridge-stp off             # Désactive STP (on n'en a pas besoin ici)
        bridge-fd 0                # Pas de délai sur le bridge
        hwaddress <adresse-mac-serveur> # Adresse MAC statique (optionnel)

iface vmbr0 inet6 static
        address <ipV6-du-serveur>/128 # Une IPv6 pour ceux qui en ont besoin
        gateway <ipV6-passerelle> # Et sa passerelle
  
```
  
2. Colle ce bloc magique si ce n’est pas déjà fait :
{.is-success}

```bash
# Interface vmbr1 : le réseau interne (LAN)
auto vmbr1
iface vmbr1 inet static
        address 192.168.1.1/24   # Une IP locale pour le réseau interne (LAN) (à adapter si besoin)
        bridge-ports none         # Pas de ports physiques associés, c’est un bridge "virtuel"
        bridge-stp off            # Pas de spanning tree (inutile ici)
        bridge-fd 0               # Pas de délai

```
  
3. Enregistrer et relancer l’interface :

```bash
  sudo ifdown vmbr1  # Arrêter l’interface si elle est déjà active
sudo ifup vmbr1    # Relancer pour activer les nouvelles configs
```

  
## Étape 2 : Configurer les règles réseau (iptables)
  
sudo nano /etc/network/interfaces

```bash
# network interface settings; autogenerated
# Please do NOT modify this file directly, unless you know what
# you're doing.
#
# If you want to manage parts of the network configuration manually,
# please utilize the 'source' or 'source-directory' directives to do
# so.
# PVE will preserve these directives, but will NOT read its network
# configuration from sourced files, so do not attempt to move any of
# the PVE managed interfaces into external files!

auto lo
iface lo inet loopback

iface eno1 inet manual

auto vmbr0
iface vmbr0 inet static
        address 176.31.183.88/24
        gateway 176.31.183.254
        bridge-ports eno1
        bridge-stp off
        bridge-fd 0
        hwaddress 70:54:D2:19:BD:D6

iface vmbr0 inet6 static
        address 2001:41d0:8:ee58::1/128
        gateway 2001:41d0:8:eeff:ff:ff:ff:ff

auto vmbr1
iface vmbr1 inet static
        address 192.168.50.1/24
        bridge-ports none
        bridge-stp off
        bridge-fd 0

post-up echo 1 > /proc/sys/net/ipv4/ip_forward
post-up iptables -t nat -A POSTROUTING -s '192.168.50.0/24' -o vmbr0 -j MASQUERADE
post-down iptables -t nat -D POSTROUTING -s '192.168.50.0/24' -o vmbr0 -j MASQUERADE
post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 443 -j DNAT --to 192.168.50.2:443
post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 443 -j DNAT --to 192.168.50.2:443
post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 2223 -j DNAT --to 192.168.50.2:22
post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 2223 -j DNAT --to 192.168.50.2:22
post-up iptables -t nat -A PREROUTING -i vmbr0 -p udp --dport 6881 -j DNAT --to 192.168.50.2:6881
post-down iptables -t nat -D PREROUTING -i vmbr0 -p udp --dport 6881 -j DNAT --to 192.168.50.2:6881
post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 8211 -j DNAT --to 192.168.50.2:8211
post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 8211 -j DNAT --to 192.168.50.2:8211
post-up iptables -t nat -A PREROUTING -i vmbr0 -p udp --dport 21027 -j DNAT --to 192.168.50.2:21027
post-down iptables -t nat -D PREROUTING -i vmbr0 -p udp --dport 21027 -j DNAT --to 192.168.50.2:21027
post-up iptables -t nat -A PREROUTING -i vmbr0 -p udp --dport 22000 -j DNAT --to 192.168.50.2:22000
post-down iptables -t nat -D PREROUTING -i vmbr0 -p udp --dport 22000 -j DNAT --to 192.168.50.2:22000
post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 22000 -j DNAT --to 192.168.50.2:22000
post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 22000 -j DNAT --to 192.168.50.2:22000



```

sudo ifdown vmbr1
sudo ifup vmbr1

## Configuration des disques LVM (Logical Volume Manager)

> LVM, ou Gestionnaire de Volumes Logiques, est une technologie de gestion de stockage pour les systèmes d'exploitation Linux. Elle permet aux administrateurs système de regrouper et de gérer l'espace disque de manière plus flexible que les partitions classiques.
{.is-success}


![lvm.png](/images/divers/lvm.png)

### Effacer les disques (facultatif mais recommandé)

> Si les disques contiennent des données précédentes, il est conseillé de les effacer pour éviter tout conflit.
{.is-warning}

```bash
sgdisk --zap-all /dev/sdX
```

### Préparer les disques (Création de partition)

Pour identifier les disques utilisez la commande : 

```
fdisk
```
ou
```
lsblk
```

```bash
fdisk --help # pour demander l'aide et la liste des commandes
fdisk -l # pour lister les partitions et disques
fdisk /dev/sdbx # pour les informations sur un disque en particulier
```

Une fois dans les informations du disque sélectionner : 
- Tapez n pour ajouter une nouvelle partition.
- Sélectionnez p pour une partition primaire.
- Choisissez le numéro de partition (1 est généralement correct).
- Acceptez les valeurs par défaut pour le début et la fin de la partition.
- Tapez w pour écrire les modifications et quitter.


Une fois les partitions créées : 

- Créer un PV (Physical Volume) 
> Vulgairement, un PV, c'est un moyen d'indiquer à LVM que le disque est utilisable et peut stocker des informations.
{.is-success}
```bash
pvcreate /dev/sdbx
```

- Créer un VG (Volume Group)
> Un VG, est un moyen d'aggréger (combiner l'espace) des PVs entre eux pour en créer un seul et unique espace de stockage logique.
{.is-success}
```bash
vgcreate big1 /dev/sdbx
```


## Configuration LVM + RAID

> Pour plus de sécuriter.
{.is-success}

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[abc]



### Voir l'état d'avancement du raid 

mdadm --detail /dev/md0

cat /proc/mdstat









Une fois dans les informations du disque sélectionner : 
- Tapez n pour ajouter une nouvelle partition.
- Sélectionnez p pour une partition primaire.
- Choisissez le numéro de partition (1 est généralement correct).
- Acceptez les valeurs par défaut pour le début et la fin de la partition.
- Tapez t pour changer le type de partition, et entrez fd pour définir le type à "Linux RAID autodetect".
- Tapez w pour écrire les modifications et quitter.




## Ajout d'un administrateur et des utilisateurs

### Qu'est-ce que PAM (Pluggable Authentication Module) ?

PAM est la méthode d'authentification native de linux. Elle permet entre autre de pouvoir recuillir toutes sortes d'information à propos d'un tuilisateur mais également de rajouter cet utilisateur à la gestion du PVE.


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