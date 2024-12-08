---
title: Monter son propre serveur, façon chill 😎
description: 
published: true
date: 2024-12-08T11:21:00.881Z
tags: serveur, homelab
editor: markdown
dateCreated: 2024-12-06T23:03:06.652Z
---

# Monter son propre serveur

- [Introduction : Pourquoi vouloir créer son propre serveur ? *Une envie d'indépendance ou de contrôle total ?*](/set-up-your-own-server/introduction)
- [Choisir un serveur dédié *Un choix stratégique crucial 🤔*](/set-up-your-own-server/choose-serveur)
- [Installation de Proxmox *La fondation de votre serveur 🛠️*](/set-up-your-own-server/install-proxmox)
- [Création et gestion des utilisateurs *Parce qu’un ROOT, c’est risqué ! 🛡️*](/set-up-your-own-server/users)
- [Sécuriser SSH *Mettez les hackers à distance 🚀*](/set-up-your-own-server/secure-ssh)
- [Configuration réseau de Proxmox *Le nerf de la guerre 🌐*](/set-up-your-own-server/network-config)
- [Configuration des disques *LVM ou ZFS ? Choisissez votre camp !*](/set-up-your-own-server/disk-config)
- [Choisir et créer une VM *Parce que tout commence par une machine virtuelle 🖥️*](/set-up-your-own-server/create-vm)
{.links-list}

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
- Dans votre navigateur préféré, tapez : 
```
https://<ip-du-serveur>:8006
```
  
## Résultat
  
Admirez votre Proxmox tout beau, prêt à être configuré. ![install-proxmox-03.png](/images/myownserver/install-proxmox-03.png)

# Mise à jour de Proxmox : Gardez votre serveur au top ! 👍

> Votre Proxmox est installé, tout beau, tout neuf. Mais si vous voulez qu’il reste au top, il va falloir le mettre à jour régulièrement. Pourquoi ? Parce que les mises à jour, c’est un peu comme les vitamines pour votre serveur : ça corrige les bugs, ça améliore les performances, et surtout, ça comble les failles de sécurité. Bref, c’est obligatoire pour un admin sérieux (et vous en êtes un, non ? 😉). Bon point, Proxmox nous permet de tout faire via son interface web.
{.is-success}

## Étape 1 : Vérifiez les mises à jour disponibles

> Une fois connecté, cliquez sur le noeud au dessous de "Datacenter" dans le menu de gauche. (proxmox sur capture d'écran)
> 1. Dans la vue principale, repérez l’onglet "Updates". Cliquez dessus.
> 2. Vous verrez une liste des paquets installés sur votre serveur. Proxmox vérifiera automatiquement si des mises à jour sont disponibles. Si ce n’est pas le cas, vous pouvez forcer une vérification en cliquant sur le bouton "Refresh".
{.is-info}

![update-proxmox-01.png](/images/myownserver/update-proxmox-01.png)

> 💡 Astuce : Si rien ne s’affiche et si vous utilisez l’offre gratuite de Proxmox (sans abonnement), assurez-vous que le dépôt pve-no-subscription est activé. Vous pouvez vérifier ça dans la configuration des dépôts (voir ci-après).


## Étape 2 : Installer les mises à jour

> 1. Une fois que Proxmox a identifié les paquets à mettre à jour, cliquez sur le bouton "Upgrade".
> 2. Une fenêtre pop-up s’ouvrira pour afficher les détails des mises à jour (ce qui va être installé, mis à jour ou supprimé). Confirmez en cliquant sur "Upgrade" dans cette fenêtre.
{.is-info}

> Proxmox va maintenant télécharger et appliquer les mises à jour. Vous verrez une barre de progression. Pas besoin de toucher quoi que ce soit : laissez-le travailler tranquillement !
> {.is-info}
{.is-info}


![update-proxmox-01.png](/images/myownserver/update-proxmox-02.png)

> Une nouvelle fenêtre va peut être apparaître et il suffira de faire <kbd>Entrée/Enter</kbd> avec la touche de votre clavier. Une fois la mise à jour terminée, fermez la fenêtre.
{.is-warning}


![update-proxmox-01.png](/images/myownserver/update-proxmox-03.png)

# Créer un utilisateur autre que ROOT dans PROXMOX

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

# Sécuriser SSH : Changer le port et installer Fail2Ban 🚀

> Vous avez installé votre serveur, vous y accédez via SSH, et tout roule. Mais attendez… Avez-vous laissé le port SSH par défaut ? Si oui, il y a un souci. Pourquoi ? Parce que le port 22, c’est le point d’entrée de toutes les attaques automatisées (botnet). C’est un peu comme laisser la porte d’entrée de votre maison grande ouverte avec un panneau "Bienvenue". 😅 Heureusement, on peut sécuriser ça en quelques étapes simples : changer le port par défaut et installer un petit garde du corps nommé Fail2Ban. Allez, on y va !
{.is-success}

> ⚠️ **Attention**, si vous comptez créer un cluster sur Proxmox, ignorer cette étape, en effet Proxmox utilise le port 22 pour créer ses clusters.
{.is-warning}


> ⚠️ **Attention**, Changer le port SSH n'est pas une mesure de sécurité en soi. Cela ne fait qu'ajouter une couche d'obscurité qui complique légèrement la tâche des attaquants, notamment les scripts automatisés. Cependant, un attaquant sérieux pourra toujours trouver votre nouveau port en scannant votre serveur, via la commande **nmap** par exemple.
> 
> Cette pratique reste utile pour :
> 
> - Réduire les attaques triviales.
> - Alléger les journaux système.
> 
> Pour ajouter une couche de sécurité, privilégiez l’utilisation de clés SSH, un pare-feu (iptables), et un outil comme Fail2Ban. Changer le port ne remplace pas ces mesures ! Considérez cela comme un complément, pas une solution magique.
{.is-warning}

> Pour une sécurité maximale, une des meilleures pratiques consiste à protéger l'accès SSH derrière un VPN. Avec cette méthode :
> 
> - Votre port SSH n'est pas accessible directement depuis l'extérieur.
> - Seuls les utilisateurs connectés au VPN peuvent tenter d'accéder à SSH.
> - Port du VPN masqué pour les cans externes.
> 
> Configurer un VPN comme WireGuard ou OpenVPN sur votre serveur est une approche bien plus sécurisée, particulièrement si vous gérez des environnements sensibles. Cela ajoute une véritable barrière supplémentaire contre les intrusions.
{.is-info}

## Partie 1 : Changer le port par défaut de SSH 🚪
Le port par défaut de SSH est 22, mais rien ne vous oblige à le garder. On peut le changer en toute simplicité, grâce au fichier de configuration sshd_config.

### Étape 1 : Créer un fichier de configuration dédié
Pour éviter de modifier directement le fichier principal et risquer une erreur, on va créer une surcharge propre dans le dossier dédié à SSH :

```bash
sudo nano /etc/ssh/sshd_config.d/99-custom-config.conf
```

> 💡 Pourquoi un numéro en début de nom ? Dans le dossier /etc/ssh/sshd_config.d/, vous trouverez peut-être un fichier nommé 50-cloud-init.conf. Ce fichier a été créé automatiquement. Le 50 au début indique l’ordre de priorité lorsque SSH applique ses configurations : les fichiers sont lus dans l’ordre croissant des numéros.
>
> En créant un fichier avec un numéro plus élevé, comme 99-custom-port.conf, vous garantissez que votre configuration surchargera celle de 50-cloud-init.conf ou tout autre fichier avec un numéro plus bas.
{.is-info}

> ⚠️ Attention : Assurez-vous que votre nouveau fichier contient uniquement les directives nécessaires (comme le port), pour éviter de surcharger accidentellement d'autres configurations importantes. 
{.is-warning}

### Étape 2 : Ajouter une directive pour le nouveau port
Dans ce fichier, ajoutez la ligne suivante :

```bash
PermitRootLogin no # On évite la connexion en root directement (d'ou la création d'un autre utilisateur)
Port 2222
AllowGroups sshusers # Et on accepte seulement les membres du groupe sshusers à se connecter
```

> 💡 Conseil : Vous pouvez remplacer le port 2222 par le port de votre choix (au-dessus de 1024, de préférence).
{.is-warning}

Enregistrez et fermez le fichier (Ctrl + O pour enregistrer, Ctrl + X pour quitter).

### Étape 3 : Appliquer et tester la configuration
Avant de relancer le service SSH, vérifiez que tout est OK :

```bash
sudo sshd -t
```
Si tout est bon, redémarrez le service :

```bash
sudo systemctl restart sshd
```
### Étape 4 : Tester la connexion SSH avec le nouveau port
Ouvrez une autre fenêtre de terminal et essayez de vous connecter avec le nouveau port :


```bash
ssh utilisateur@votre-ip -p 2222
```
> 
> ⚠️ **Attention** : Ne fermez pas votre session SSH actuelle tant que vous n’avez pas confirmé que la connexion fonctionne avec le nouveau port ! Sinon, vous risquez de vous bloquer hors du serveur. 😬
{.is-warning}




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

## Étape 1 : Créer une interface réseau

1. On va débuter par créer une interface réseau dans proxmox :
	- Dans l'onglet System > Network > Create > Linux Bridge
	![install-proxmox-04.png](/images/myownserver/install-proxmox-04.png)
	- Ensuite, on va enregistrer les informations.
  ![install-proxmox-05.png](/images/myownserver/install-proxmox-05.png)

## Étape 2 : Modifier les interfaces réseau

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

  
## Étape 3 : Configurer les règles réseau (iptables)
  
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
post-up iptables -t nat -A PREROUTING -i vmbr0 -p udp --dport 51820 -j DNAT --to 192.168.50.2:51820
post-down iptables -t nat -D PREROUTING -i vmbr0 -p udp --dport 51820 -j DNAT --to 192.168.50.2:51820
```
  
</details>

  
## Étape 4 : Redémarrer les interfaces
  
> Une fois que tout est prêt, tu peux relancer les interfaces. Hop, deux petites commandes magiques :
{.is-info}


```bash
sudo ifdown vmbr1  # On éteint l'interface vmbr1
sudo ifup vmbr1    # Et on la rallume
```
  
> Boum ! Normalement, ton réseau interne est prêt, et tes VMs peuvent papoter entre elles (et même aller sur Internet). 🎉
{.is-info}



# Configuration des disques : LVM ou ZFS ? À vous de choisir !
  
>   **LVM** et **ZFS** sont deux outils puissants pour gérer vos disques. LVM est parfait pour les besoins classiques de gestion flexible de partitions et d’espace disque, tandis que ZFS va plus loin avec des fonctionnalités avancées comme les snapshots, la compression native et une gestion simplifiée du RAID. 🚀
> 
> Vous ne savez pas encore lequel choisir ? Pas de panique : on vous explique les deux. Suivez le guide ! 🎮
{.is-success}

## Option 1 : LVM (Logical Volume Manager)
  > **LVM, alias le Gestionnaire de Volumes Logiques**, c'est un peu comme un Tetris pour vos disques sous Linux. Besoin de jongler avec de l'espace disque sans casser vos partitions ? LVM est là pour rendre votre vie plus simple et plus flexible que les bonnes vieilles partitions rigides. 🎮
{.is-success}
  
  ![lvm.png](/images/divers/lvm.png)
 
 
### Etape 1 : Effacer les disques (facultatif mais recommandé)
  > Si vos disques contiennent des données précédentes, mieux vaut tout effacer. Ça évite les conflits et les bugs du genre « Mais pourquoi ce disque me déteste ? ». 😅
{.is-warning}

```bash
sgdisk --zap-all /dev/sdX # X est le disque dur en question
```
   
  
### Etape 2 : Préparer les disques et partitions
  #### Trouver vos disques
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
  
#### Créer une partition
Une fois dans le menu de fdisk, suivez le guide :

- **Tapez <kbd>n</kbd>** : Ajoutez une nouvelle partition.
- **Choisissez <kbd>p</kbd>** : Pour une partition primaire (simple et efficace).
- **Sélectionnez le numéro de partition** : En général, 1 fait le taf.
- **Début et fin de partition** : Appuyez sur Entrée pour accepter les valeurs par défaut.
- **Tapez <kbd>w</kbd>** : Sauvegardez vos changements et sortez.

  🎉 Bravo, vous venez de créer une partition ! 🎉
  
  
### Etape 3 : Passez à LVM (parce qu'on ne fait pas les choses à moitié)  
  
1. Créer un PV (Physical Volume)
> Vulgairement, un PV, c'est un moyen d'indiquer à LVM que le disque est utilisable et peut stocker des informations.
> Imaginez un PV comme une étiquette disant à LVM : « Hey, ce disque est prêt à stocker des trucs. » 🏷️
{.is-success}

{.is-success}

```bash
pvcreate /dev/sdbX
pvdisplay # Pour vérifier les PV
```
 > 💡 Astuce : Si vous avez plusieurs disques, effacez-les tous (par exemple /dev/sdX, /dev/sdY, etc.).
{.is-info}
  
2. Créer un VG (Volume Group)
> Un VG, est un moyen d'aggréger (combiner l'espace) des PVs entre eux pour créer un seul et unique espace de stockage logique. 🛠️
{.is-success}

```bash
vgcreate nom_vg /dev/sdbX /dev/sdcX 
vgdisplay # Pour vérifier les VG
```
  <!--
3. Ajoutez un volume logique  :
```bash
lvcreate -L 100G -n nom_lv nom_vg # par exemple, pour 100 Go
lvcreate -l 100%FREE -n nom_lv nom_vg # par exemple, pour tout l'espace libre
lvcreate --type raid5 -l 100%FREE -n nom_lv nom_vg # Pour créer un lvm raid5
```


https://serverfault.com/questions/1164668/lvm-raid5-replacerebuild

  
4. Formatez le volume logique :
```bash
mkfs.ext4 /dev/nom_vg/nom_lv # formattez en ext4
mkfs.xfs /dev/nom_vg/nom_lv # formattez en xfs
```
  -->
3. Ajouter votre stockage au noeud
  
Aller dans stockage > Add > LVM
  
### Etape Bonus : LVM + RAID mdadm (parce qu’on aime dormir tranquille)
  
> Envie de dormir sur vos deux oreilles avec un stockage résistant aux pannes ? Activez le RAID. 🚨
{.is-success}

  
  #### Créer un RAID mdadm
Créez un RAID 5 sur 3 disques avec la commande suivante :

```bash
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[abc]  
```

#### Suivre l'avancement du RAID
  
Parce qu'on aime bien savoir où on en est :
  
```bash
mdadm --detail /dev/md0
```
ou 
  
```bash
cat /proc/mdstat
```
  
### Astuce RAID-friendly
Lors de la création de partitions pour un disque RAID :

1. Tapez <kbd>n</kbd> : Ajoutez une nouvelle partition.
1. Tapez <kbd>p</kbd> : Partition primaire.
1. Sélectionnez le numéro partition : 1 fait encore l’affaire.
1. Début et fin departition : Entrée pour les valeurs par défaut.
1. Tapez <kbd>t</kbd> : Changez le type de partition, puis entrez <kbd>fd</kbd> pour définir le type (Linux RAID autodetect).
1. Tapez <kbd>w</kbd> : Sauvegardez et quittez.
  
> Une fois votre RAID fait, vous pouvez suivre les étapes pour mettre en place un LVM si vous souhaitez rester flexible tout en bénéficiant d'un raid performant.
{.is-info}

> Attention, il y a une différence entre le LVM RAID et mdadm RAID : 
> |        Critère        |              LVM RAID 5             |           mdadm RAID 5          |
> |:---------------------:|:-----------------------------------:|:-------------------------------:|
> | Performance           | Moins performant pour les écritures | Performances optimales          |
> | Gestion               | Unifiée avec LVM                    | RAID séparé, gestion RAID + LVM |
> | Flexibilité RAID      | Moins flexible                      | Options RAID avancées           |
> | Snapshots             | Intégrés dans LVM                   | Doit utiliser LVM au-dessus     |
> | Complexité            | Plus simple (RAID + LVM unifiés)    | Plus complexe                   |
> | Stabilité et maturité | Plus récente                        | Solution éprouvée               |
> 
> ‎
{.is-warning}

  
Et voilà, vous êtes maintenant un pro du LVM et du RAID. 🥳  
  <!--
## Option 2 : ZFS (Zettabyte File System)
  
>   Vous cherchez une solution tout-en-un, moderne et performante ? ZFS, c’est le chef d’orchestre des systèmes de fichiers. Avec ZFS, pas besoin de LVM ou de RAID séparé : tout est intégré. Il offre la compression, les snapshots, et une gestion impeccable du stockage. ✨
> 
> Voici comment configurer vos disques avec ZFS.
{.is-success}

  
  
### Étape 1 : Préparer les disques
ZFS aime partir d’une base propre, donc effaçons tout !

```bash
wipefs -a /dev/sdX  # X est le disque cible
> 💡 Astuce : Si vous avez plusieurs disques pour ZFS, effacez-les tous (par exemple /dev/sdX, /dev/sdY, etc.).
{.is-info}


Étape 2 : Créer un pool ZFS
Un pool ZFS est une sorte de super-volume qui regroupe un ou plusieurs disques. Voici les configurations les plus courantes :

1. Pool simple (1 disque)
Si vous voulez un stockage de base sur un seul disque :

bash
Copier le code
zpool create mypool /dev/sdX
2. Pool avec RAID-Z (RAID 5 façon ZFS)
Pour protéger vos données avec un RAID-Z sur 3 disques :

bash
Copier le code
zpool create mypool raidz /dev/sdX /dev/sdY /dev/sdZ
3. Pool en miroir (RAID 1 façon ZFS)
Pour doubler vos données sur 2 disques :

bash
Copier le code
zpool create mypool mirror /dev/sdX /dev/sdY
Étape 4 : Vérifier l’état du pool
Une fois le pool créé, vérifiez qu’il est opérationnel avec :

bash
Copier le code
zpool status
Vous verrez une sortie détaillée qui confirme que votre pool est actif et sain. 🎉

Étape 5 : Monter automatiquement le pool
ZFS monte automatiquement les pools créés sous /mypool (le nom que vous avez donné). Si vous voulez un autre point de montage :

bash
Copier le code
zfs set mountpoint=/mnt/mypool mypool
Étape 6 : Activer des options avancées (facultatif mais stylé)
Activer la compression pour économiser de l’espace :

bash
Copier le code
zfs set compression=on mypool
Créer un dataset (sous-volume logique) :

bash
Copier le code
zfs create mypool/dataset1
Faire un snapshot (sauvegarde instantanée) :

bash
Copier le code
zfs snapshot mypool/dataset1@sauvegarde1
Lister vos snapshots :

bash
Copier le code
zfs list -t snapshot  
  
  
  
  -->
  
  
  
  
# Choisir et créer une VM
  
Maintenant que Proxmox est paramétré, tu peux choisir quel système installer dans ta VM. Selon tes besoins, voici quatre options cool et pratiques que je te propose : OMV, CasaOS, UmbrelOS et Cosmos Cloud. Fais ton choix ! 🔥
  
## Option 1 : Installer OpenMediaVault (OMV) 🗄️
  
> OMV, c’est la référence pour transformer ton serveur en solution de stockage réseau (NAS) et préparer le terrain pour Docker avec un interface graphique. Si tu veux gérer du stockage, des sauvegardes et des services en mode solide, c’est pour toi.
{.is-success}


1. **Télécharge l’ISO :**
- Va sur [le site officiel d’OMV](https://www.openmediavault.org) et récupère l’image ISO (basée sur Debian).
  
2. **Crée une VM dans Proxmox :**
- Clique sur « Créer une VM ».
- Donne un nom à ta VM (ex : VM-OMV).
- Ajoute l’image ISO téléchargée.
- Alloue des ressources (CPU, RAM, disque dur).
  
3. **Installe Debian/OMV :**
- Lance l’installation et suis les instructions comme un installateur Debian classique.
  
  
> Pourquoi OMV ?
> 
> C’est stable et axé sur la gestion des fichiers et services de stockage.
> Parfait pour gérer Docker et des outils comme Jellyfin.
{.is-info}

## Option 2 : Installer CasaOS 🏡
  
>   [CasaOS](https://casaos.io), c’est l’option user-friendly pour ceux qui veulent un serveur à la maison sans prise de tête. Interface sexy, simple à utiliser, et idéale pour gérer des médias ou des apps courantes sans le stress des configs compliquées.
{.is-success}

1. **Télécharge l’ISO de Debian et utilise leur script :**
- CasaOS ne fournit pas d’ISO direct, mais tu peux installer [une base Debian](https://www.debian.org/distrib/index.fr.html) et ajouter [CasaOS](https://casaos.io) ensuite avec leur script magique.
```bash
curl -fsSL https://get.casaos.io | sudo bash
```

2. **Crée une VM dans Proxmox :**
- Ajoute l’ISO de Debian (ou Ubuntu).
- Donne un nom à ta VM (ex : VM-CASA).
- Configure les ressources de la VM.
- Lance Debian et connecte-toi en SSH.
  
3. **Installe CasaOS :**
- Exécute le script mentionné plus haut pour installer CasaOS.

> Pourquoi CasaOS ?
> 
> Simple et accessible, parfait pour débuter.
> Une interface moderne avec des apps pré-intégrées pour la gestion de médias et plus (Docker, gestion des médias, etc.).
{.is-info}

  
## Option 3 : Installer UmbrelOS 🌐
  
>   [UmbrelOS](https://umbrel.com/umbrelos), c’est l’option pour les fans de décentralisation et de projets comme Bitcoin, Lightning Network, ou d’apps privées type Nextcloud. Mais ça peut aussi gérer des apps basiques !
{.is-success}
  
1. **Télécharge l’ISO :**
- Va sur [le github d'UmbrelOS](https://github.com/getumbrel/umbrel/wiki/Install-umbrelOS-on-a-Linux-VM).
  
2. **Crée une VM dans Proxmox :**
- Clique sur « Créer une VM ».
- Donne un nom à ta VM (ex : VM-UMBREL).
- Ajoute l’image ISO téléchargée.
- Alloue des ressources (CPU, RAM, disque dur).

3. **Lance UmbrelOS :**
- Une fois installé, accède à l’interface web pour commencer à configurer tes services.

  
> Pourquoi UmbrelOS ?
> 
> Focus sur les outils décentralisés (Bitcoin, Nextcloud, etc.).
> Idéal pour explorer l’univers des clouds privés.  
{.is-info}

  
## Option 4 : Installer Cosmos Cloud 🌌
  
>   [Cosmos Cloud](https://cosmos-cloud.io), est une autre solution qui te permet de gérer un cloud personnel hyper intuitif. Il se concentre sur une interface claire et des fonctionnalités collaboratives.
{.is-success}
  
1. **Télécharge l’ISO de Debian :**
- Cosmos Cloud ne fournit pas d’ISO direct, mais tu peux installer une base Debian et ajouter Cosmos Cloud ensuite via docker.
  
2. **Crée une VM dans Proxmox :**
- Ajoute l’ISO de Debian (ou Ubuntu).
- Donne un nom à ta VM (ex : VM-COSMOS).
- Configure les ressources de la VM.
- Lance Debian et connecte-toi en SSH.
  
3. **Installe Docker :**
- Tu peux aisement installer docker grâce au script suivant. 
  
```bash
curl -fsSL https://get.docker.com | sudo sh
```
4. **Installe Cosmos Cloud :**
Exécute la commande docker suivante pour installer Cosmos Cloud.
  
```bash
sudo docker run -d --network host  --privileged --name cosmos-server -h cosmos-server --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket -v /:/mnt/host -v /var/lib/cosmos:/config azukaar/cosmos-server:latest
```

> Pourquoi Cosmos Cloud ?
> 
> Une alternative open-source aux clouds mainstream.
> Idéal pour les particuliers ou petites équipes cherchant un espace collaboratif.
> Le seul avec OMV a être multi-utilisateur.
{.is-info}

  

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