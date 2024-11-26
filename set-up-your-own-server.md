---
title: Monter son propre serveur, façon chill 😎
description: 
published: 1
date: 2024-11-26T20:04:34.305Z
tags: hyperviseur, ovh, proxmox, virtualisation, vm
editor: markdown
dateCreated: 2024-06-10T13:18:25.873Z
---

# Introduction : Pourquoi vouloir créer son propre serveur ?

> Eh bien, pourquoi pas ? C’est un super projet pour se lancer, apprendre plein de trucs, et montrer aux pros que vous n’êtes pas là pour rigoler. En plus, c’est carrément stylé de dire : "Oui, j’ai mon propre serveur." Mais ce n’est pas juste pour se la raconter, il y a plein d’avantages à faire ça. Allez, on vous explique tout :
{.is-info}


# Tabs {.tabset}
## Contrôle Total

- Faites ce que vous voulez ! (Personnalisation) : Vous pouvez configurer votre serveur exactement comme vous l’aimez, installer les applis qui vous plaisent, et bidouiller jusqu’à ce que tout soit parfait pour vos besoins.
- Des ressources rien que pour vous (Gestion des Ressources) : Besoin de plus de puissance ? Moins ? C’est vous le patron ! CPU, RAM, stockage : vous gérez tout comme un pro (ou un gamer exigeant).

## Flexibilité à gogo

- Multi-tâches au max : Hébergez un site, une base de données, un serveur de jeu, ou même un serveur mail. Pourquoi choisir quand on peut tout faire ?
- La magie de la virtualisation : Avec des outils comme Proxmox, vous transformez un serveur en plusieurs petits serveurs virtuels. Ça veut dire plus d’expériences, plus de tests, et encore plus de fun.

## La sécurité, comme un boss

- Zéro stress : C’est vous qui gérez la sécurité. Firewall, mots de passe béton, et politique maison, tout est sous votre contrôle.
- Chacun chez soi (Isolation) : Avec les machines virtuelles, chaque service est isolé. Si quelque chose plante, le reste continue de tourner tranquille.

## Des performances au top
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


De mon côté, j’ai choisi l’offre Low Cost **Kimsufi** d’OVH, qui propose un excellent rapport qualité/prix pour démarrer sans exploser le budget et le système de **virtualisation Proxmox** qui me permettra si je le souhaite de me créer plusieurs machines (VM) au sein d'une seule et unique machine.
https://eco.ovhcloud.com/fr/kimsufi/

# Installation de Promox sur un serveur Dédié

Et maintenant, passons aux choses sérieuses : l’installation de Proxmox. Pas de panique, c’est simple comme bonjour. Voici les étapes :

# Tabs {.tabset}
## Accéder au serveur via KVM ou IPMI

- Connectez-vous à l’interface de gestion OVH.
-	Allez dans l’onglet Bare Metal Cloud, puis dans Serveur Dédié > Tous mes serveurs.

## Installer Proxmox
- Dans la vue de droite, cliquez sur Système d’exploitation (OS).
- Ouvrez le menu à trois petits points (les fameux "…" qu’on adore) et choisissez Installer.
![install-proxmox-01.png](/images/myownserver/install-proxmox-01.png)
- Suivez les instructions affichées à l’écran pour installer Proxmox VE.  
![install-proxmox-02.png](/images/myownserver/install-proxmox-02.png)

## Configurer le réseau
- Une fois l’installation terminée, configurez le réseau pour que votre serveur soit accessible via l’interface web.

## Accéder à l’interface web de Proxmox
	- Dans votre navigateur préféré, tapez : https://<ip-du-serveur>:8006.	

  
## Résultat
  
Admirez votre Proxmox tout beau, prêt à être configuré. ![install-proxmox-03.png](/images/myownserver/install-proxmox-03.png)


# Créer un utilisateur autre que ROOT sans PROXMOX

> Pourquoi créer un utilisateur autre que ROOT, vous allez me dire ? 🤔
{.is-info}

> Bonne question ! Utiliser root pour tout, c’est un peu comme utiliser une clé passe-partout pour chaque porte de ta maison. Pratique, mais carrément risqué. 😬 Voici pourquoi il vaut mieux éviter de toujours jouer les super admins :
{.is-success}


**1. Limiter les risques**

- Si quelqu’un met la main sur les identifiants de root, il peut littéralement tout casser, et pas qu’un peu. En créant un utilisateur avec des permissions limitées, tu réduis la casse en cas de pépin. 🚧

**2. Respecter les bonnes pratiques**

- Séparer les tâches : Un utilisateur admin pour les grosses manips, et un utilisateur normal pour les petites actions du quotidien. C’est comme porter une blouse quand tu fais de la chimie : mieux vaut prévenir que guérir. 🧪
- Traçabilité : Avec plusieurs utilisateurs, tu sais qui a fait quoi (pratique pour éviter les disputes avec ton collègue marcel). 📜

**3. Gérer les permissions intelligemment**

- Tu peux donner à chaque utilisateur exactement les droits qu’il lui faut : pas plus, pas moins. Par exemple, un collègue peut gérer uniquement ses VM sans avoir accès à tout le système. 🎯
- En gros, créer un utilisateur autre que root, c’est comme avoir plusieurs clés adaptées à chaque porte, plutôt qu’une seule clé qui ouvre tout (et que tu pourrais perdre). Maintenant, passons à l’action avec PAM pour faire ça proprement ! 💪

> En gros, créer un utilisateur autre que root, c’est comme avoir plusieurs clés adaptées à chaque porte, plutôt qu’une seule clé qui ouvre tout (et que tu pourrais perdre). Maintenant, passons à l’action avec PAM pour faire ça proprement ! 💪
{.is-warning}

# Créer un utilisateur PAM dans Proxmox : C'est qui PAM ? 🤔

> Alors là, on parle d’un petit classique dans le monde de Proxmox : créer un utilisateur PAM. Mais d’abord, un petit cours express sur PAM (Pluggable Authentication Modules). En gros, PAM, c’est le système qui gère les connexions utilisateurs dans Linux. Si tu te connectes avec ton mot de passe habituel, c’est PAM qui vérifie. 🔐
{.is-info}


> Dans Proxmox, PAM est bien pratique, parce qu’il permet de créer des utilisateurs directement liés au système Linux sous-jacent. Ça veut dire que ton utilisateur PAM peut aussi se connecter via SSH, si tu veux, et pas juste à l’interface web de Proxmox.
{.is-success}


## Pourquoi créer un utilisateur PAM dans Proxmox ?
> - Pour éviter d’utiliser root tout le temps : Sérieusement, utiliser root partout, c’est comme laisser les clés de la maison sous le paillasson. Avec un utilisateur dédié, tu limites les dégâts en cas de pépin. 🛡️
> - Pour créer des accès spécifiques : Tu peux donner à ton pote/ton collègue un accès limité à certaines ressources sans lui filer les pleins pouvoirs.
> - Pour mieux organiser les permissions : Les utilisateurs PAM peuvent être liés à des rôles et permissions dans Proxmox, ce qui te permet de garder un contrôle total. 🎯
{.is-success}

## Comment créer un utilisateur PAM dans Proxmox ?

Allez, voici la recette pas à pas :

### Etape 1 : Créer l’utilisateur dans Linux
On commence par créer l’utilisateur directement dans le système à partir de la fenêtre SHELL. Par exemple, pour un utilisateur appelé marcel :

```bash
sudo adduser marcel
```
Tu suis les instructions (nom, mot de passe, etc.), et hop, l’utilisateur est prêt.

### Etape 2 : Lier cet utilisateur à Proxmox

Maintenant, direction l’interface web de Proxmox :
**1. Connexion à l’interface :** Connecte-toi en tant que root (ou un utilisateur qui a les droits admin).
**2. Aller dans la gestion des utilisateurs :** 
		Menu "Datacenter" > "Permissions" > "Users".
**3. Ajouter l’utilisateur PAM :**
- Clique sur "Add" (le bouton magique).
- Renseigne :
	- ID utilisateur : Mets le même que celui que tu as créé (marcel dans notre exemple).
  - Realm : Choisis PAM (pour que Proxmox sache que cet utilisateur est géré par Linux).
- Valide. 🎉
    
### Etape 3 : Attribuer des permissions**
Un utilisateur sans permissions, c’est comme un joueur sans manette : il ne peut rien faire. Donc, il faut lui donner des droits :
**1. Toujours dans "Permissions", va sur l’onglet "Roles".**
**2. Ajoute une permission pour ton utilisateur :**
- Sélectionne un rôle (par exemple, PVEAdmin pour qu’il puisse gérer les VM, ou PVEDatastoreUser pour accéder au stockage).
- Associe-lui une ressource (par exemple, tout le datacenter ou une VM en particulier).
- Valide. 🎯



> Et voilà, ton utilisateur PAM est prêt à l’emploi ! 🕹️
> Maintenant, marcel peut se connecter à l’interface web de Proxmox (et potentiellement via SSH) avec les permissions que tu lui as données. Tu peux aussi utiliser ça pour créer un accès temporaire à un collègue ou restreindre un utilisateur à une seule VM. Bref, c’est propre, sécurisé, et sous contrôle. 💪
{.is-success}


# Configuration Réseau de Promox

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
  
> C’est là qu’on rigole un peu avec les règles NAT et de redirection. Regarde ces lignes :
{.is-info}


```bash
post-up echo 1 > /proc/sys/net/ipv4/ip_forward  # Active le routage IPv4
post-up iptables -t nat -A POSTROUTING -s '192.168.50.0/24' -o vmbr0 -j MASQUERADE  # NAT vers Internet
post-down iptables -t nat -D POSTROUTING -s '192.168.50.0/24' -o vmbr0 -j MASQUERADE  # On retire ça au down

# Exemple de redirection : envoyer le port 443 de l’extérieur vers une machine locale (192.168.50.2)
post-up iptables -t nat -A PREROUTING -i vmbr0 -p tcp --dport 443 -j DNAT --to 192.168.50.2:443
post-down iptables -t nat -D PREROUTING -i vmbr0 -p tcp --dport 443 -j DNAT --to 192.168.50.2:443

# Pareil pour d’autres ports si besoin (SSH, torrent, etc.)
```

> En gros, tout ça sert à dire :
> 
> Post-up : "À l’allumage, fais ça" 🟢
> Post-down : "À l’arrêt, enlève ça proprement" 🔴
{.is-info}


<details>
    <summary>Finalement mon fichier ressemble à : </summary>
  
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
        address <ip-du-serveur>/24
        gateway <ip-passerelle>
        bridge-ports eno1
        bridge-stp off
        bridge-fd 0
        hwaddress <adresse-mac-serveur>

iface vmbr0 inet6 static
        address <ipV6-du-serveur>
        gateway <ipV6-passerelle>

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
  
</details>


## Étape 3 : Redémarrer les interfaces
  
> Une fois que tout est prêt, tu peux relancer les interfaces. Hop, deux petites commandes magiques :
{.is-info}


```bash
sudo ifdown vmbr1  # On éteint l'interface vmbr1
sudo ifup vmbr1    # Et on la rallume
```
  
> Boum ! Normalement, ton réseau interne est prêt, et tes VMs peuvent papoter entre elles (et même aller sur Internet). 🎉
{.is-info}




# Configuration des disques LVM (Logical Volume Manager)

> LVM, alias le Gestionnaire de Volumes Logiques, c'est un peu comme un Tetris pour vos disques sous Linux. Besoin de jongler avec de l'espace disque sans casser vos partitions ? LVM est là pour rendre votre vie plus simple et plus flexible que les bonnes vieilles partitions rigides. 🎮
{.is-success}


![lvm.png](/images/divers/lvm.png)
  

## Effacer les disques (facultatif mais recommandé)


> Si vos disques contiennent des données précédentes, mieux vaut tout effacer. Ça évite les conflits et les bugs du genre « Mais pourquoi ce disque me déteste ? ». 😅
{.is-warning}

```bash
sgdisk --zap-all /dev/sdX # Où X est le disque dur en question
```

## Préparer les disques (Créer des partitions comme un boss)

### Trouver vos disques
Avant de commencer, il faut repérer vos disques comme un détective. 🕵️‍♀️ Utilisez une des commandes magiques :
  
```bash
fdisk
```
ou
```bash
lsblk
```
  
  
Quelques commandes utiles :

- `fdisk --help` : Obtenez la liste des commandes (parce que personne ne peut tout retenir 💡).
- `fdisk -l `: Liste les disques et partitions.
- `fdisk /dev/sdbx` : Zoom sur un disque en particulier.
  
  
### Créer une partition
Une fois dans le menu de fdisk, suivez le guide :

- **Tapez <kbd>n</kbd>** : Ajoutez une nouvelle partition.
- **Choisissez <kbd>p</kbd>** : Pour une partition primaire (simple et efficace).
- **Sélectionnez le numéro de partition** : En général, 1 fait le taf.
- **Début et fin de partition** : Appuyez sur Entrée pour accepter les valeurs par défaut.
- **Tapez <kbd>w</kbd>** : Sauvegardez vos changements et sortez.
  
🎉 Bravo, vous venez de créer une partition ! 🎉
  
## Passez à LVM (parce qu'on ne fait pas les choses à moitié)
  
1. Créer un PV (Physical Volume)
> Vulgairement, un PV, c'est un moyen d'indiquer à LVM que le disque est utilisable et peut stocker des informations.
> Imaginez un PV comme une étiquette disant à LVM : « Hey, ce disque est prêt à stocker des trucs. » 🏷️
{.is-success}

{.is-success}

```bash
pvcreate /dev/sdbx
```
  
2. Créer un VG (Volume Group)
> Un VG, est un moyen d'aggréger (combiner l'espace) des PVs entre eux pour créer un seul et unique espace de stockage logique. 🛠️
{.is-success}

```bash
vgcreate big1 /dev/sdbx
```
  
## Bonus : LVM + RAID (parce qu’on aime dormir tranquille)

> Envie de dormir sur vos deux oreilles avec un stockage résistant aux pannes ? Activez le RAID. 🚨
{.is-success}

### Créer un RAID
Créez un RAID 5 sur 3 disques avec la commande suivante :

```bash
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[abc]  
```

### Suivre l'avancement du RAID
  
Parce qu'on aime bien savoir où on en est :
  
```bash
mdadm --detail /dev/md0
```
ou 
  
```bash
cat /proc/mdstat
```
  
## Astuce RAID-friendly
Lors de la création de partitions pour un disque RAID :

1. Tapez <kbd>n</kbd> : Ajoutez une nouvelle partition.
1. Tapez <kbd>p</kbd> : Partition primaire.
1. Sélectionnez le numéro partition : 1 fait encore l’affaire.
1. Début et fin departition : Entrée pour les valeurs par défaut.
1. Tapez <kbd>t</kbd> : Changez le type de partition, puis entrez <kbd>fd</kbd> pour définir le type (Linux RAID autodetect).
1. Tapez <kbd>w</kbd> : Sauvegardez et quittez.
  
  
Et voilà, vous êtes maintenant un pro du LVM et du RAID. 🥳  
  
 
# Choisir et créer une VM
  
Maintenant que Proxmox est paramétré, tu peux choisir quel système installer dans ta VM. Selon tes besoins, voici quatre options cool et pratiques : OMV, CasaOS, UmbrelOS et Cosmos Cloud. Fais ton choix ! 🔥
  
## Option 1 : Installer OpenMediaVault (OMV) 🗄️
  
> OMV, c’est la référence pour transformer ton serveur en solution de stockage réseau (NAS) et préparer le terrain pour Docker de manière user-friendly. Si tu veux gérer du stockage, des sauvegardes et des services en mode solide, c’est pour toi.
{.is-success}


**1. Télécharge l’ISO :**
- Va sur le site officiel d’OMV et récupère l’image ISO (basée sur Debian).
  
**2. Crée une VM dans Proxmox :**
- Clique sur « Créer une VM ».
- Donne un nom à ta VM (ex : VM-OMV).
- Ajoute l’image ISO téléchargée.
- Alloue des ressources (CPU, RAM, disque dur).
  
**3. Installe Debian/OMV :**
- Lance l’installation et suis les instructions comme un installateur Debian classique.
  
  
> Pourquoi OMV ?
> 
> C’est stable et axé sur la gestion des fichiers et services de stockage.
> Parfait pour gérer Docker et des outils comme Jellyfin.
{.is-info}

## Option 2 : Installer CasaOS 🏡
  
## Option 3 : Installer UmbrelOS 🌐
  
## Option 4 : Installer Cosmos Cloud 🌌

<!--
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