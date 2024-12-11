---
title: TP2
description: 
published: true
date: 2024-12-11T09:02:06.434Z
tags: 
editor: markdown
dateCreated: 2024-12-11T09:02:06.434Z
---


#  ADMINISTRATION LINUX - PARTIE 2 | LE GESTIONNAIRE DE PAQUET (ET LES ARCHIVES)

## Gestionnaire de paquet

*   1.11 Suite à l'installation de votre système (par exemple), vous voulez vous assurer qu'il est à jour.

    *   Lancez la commande `apt update`. Quels dépôts sont contactés pendant cette opération ?
    *   Lancez la commande `dpkg -l`.  `firefox`, `libreoffice`, `linux-firmware` et `apt` sont-ils présents ?
    *   À l'aide de `apt list --upgradable`, identifiez si `firefox`, `libreoffice`, `linux-firmware` et `apt` peuvent être mis à jour - et identifiez l'ancienne version et la nouvelle version.
    *   Lancez la mise à jour avec `apt dist-upgrade`. Pendant le déroulement de la mise à jour, identifiez les trois parties clefs du déroulement : liste des tâches et validation par l'utilisateur, téléchargement des paquets, et installation/configuration.
*   1.12 - Cherchez avec `apt search` si le programme `sl` est disponible. (Utiliser `grep` pour vous simplifiez la tâche). À quoi sert ce programme ? Quelles sont ses dépendances ? (Vous pourrez vous aider de `apt show`). Finalement, installez ce programme en prêtant attention aux autres paquets qui seront installés en même temps.

*   1.13 - Même chose pour le programme `lolcat`

*   1.15 - Parfois, il est nécessaire d'ajouter un nouveau dépôt pour installer un programme (parce qu'il n'est pas disponible, ou bien parce qu'il n'est pas entièrement à jour dans la distribution utilisée). Ici, nous prendrons l'exemple de `docker` qui n'est disponible que via un dépôt précis maintenu par Docker.

    *   Regarder avec `apt search` et `apt show` (et `grep` !) si le paquet `docker` est disponible et quelle est la version installable.
    *   Exécuter la commande suivante qui va ajouter le dépôt de Docker:

```
sudo add-apt-repository\
 "deb [arch=amd64] https://download.docker.com/linux/ubuntu\
 $(lsb_release -cs)\
 stable"
```

    *   Faire `apt update`. Que se passe-t-il ? Quels serveurs votre machine a-t-elle essayé de contacter ? Pourquoi cela produit-il une erreur ?
    *   Ajoutez la clef d'authentification des paquets avec `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`.
    *   Vérifiez l'empreinte de la clé ajoutée qui devrait être `9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88`. Pour cela, cherchez les 8 derniers caractères de cette clé, comme ceci :


```
$ sudo apt-key fingerprint 0EBFCD88

pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

*   Refaire `apt update`. Est-ce que ça fonctionne ?

*   Regarder avec `apt search` et `apt show` (et `grep` !) si le paquet `docker-ce` est disponible et quelle est la version installable.

*   Installer le paquet. Depuis où a-t-il été téléchargé ?

*   1.16 - Regardez le contenu de `/var/cache/apt/archives`. À quoi ces fichiers correspondent-ils ?

*   1.17 - Utilisez `aptitude why` pour trouver la raison pour laquelle le paquet `libxcomposite1` est installé

*   1.18 - Utilisez `apt-rdepends` pour afficher la liste des dépendances de `libreoffice`.

*   1.19 - Identifiez l'utilité de la commande `apt moo`

### [#](#gestion-des-archives) Gestion des archives

*   1.20 - Créez une archive (non-compressée !) de votre répertoire personnel avec `tar`.
*   1.21 - En utilisant `gzip`, produisez une version compressée de l'archive de la question précédente
*   1.22 - Recommencez mais produisant une version compressée directement
*   1.23 - En fouillant dans les options de `tar`, trouvez un moyen de lister le contenu de l'archive
*   1.24 - Créez un dossier `test_extract` dans `/tmp/`, déplacez l'archive dans ce dossier puis décompressez-là dedans.
*   1.25 - Trouvez un ou des fichiers `.gz` dans `/var/log` (ou ailleurs ?) et cherchez comment combiner `cat` et `gzip` pour lire le contenu de ce fichier sans créer de nouveau fichier.

</div>