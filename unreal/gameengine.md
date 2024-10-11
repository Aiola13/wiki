---
title: Les bases de Unreal
description: 
published: 1
date: 2024-10-11T05:53:58.348Z
tags: 
editor: markdown
dateCreated: 2024-10-02T16:06:39.314Z
---

# Epic Games Launcher

> Epic Games Launcher est une application permettant de gérer vos projets, ainsi que les versions d'Unreal Engine utilisées.
{.is-success}

![unreal-01-epic_launcher.png](/images/videogames/unreal/unreal-01-epic_launcher.png)
 
> Pour l'installer, il suffit de se rendre sur le site officiel d'Epic Games et de créer un compte.
> Download : https://store.epicgames.com/fr/
{.is-success}


> Pour plus de détail, rendez-vous directement sur la doc de Epic Games : https://dev.epicgames.com/documentation/fr-fr/unreal-engine/installing-unreal-engine
{.is-info}

# Unreal Launcher

> Unreal Launcher nous permet de lancer des projets à partir de templates prédéfinis, avec des plugins et configurations déjà paramétrés pour faciliter la création.
{.is-success}

![unreal-02-unreal_launcher.png](/images/videogames/unreal/unreal-02-unreal_launcher.png)

> Si vous avez une carte graphique récente supportant le RayTracing (RTX), je vous recommande vivement de cocher la case RayTracing avant de lancer un projet, cela aura pour effet d'activer dans les paramètres du projet tout en relation avec la  gestion de la lumière (Lumen, nous reviendrons dessus plus tard).
{.is-warning}


# Interface générale

L’interface se présente comme ceci : 

![unreal-03-interface.png](/images/videogames/unreal/unreal-03-interface.png)

| N° | Panel Name | Description                                                        |
|---|----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | Level Viewport | C’est la vue d’édition d'Unreal (réglages positions, orientations, ajout d’objets …).                                                        |
| 2 | Outliner       | Affiche tous les acteurs de la scène dans une arborescence hiérarchique (les objets peuvent y être sélectionnés)                             |
| 3 | Details Panel  | Ce sont les paramètres (Détails) de l’objet (Actor) sélectionné.                                                                             |
| 4 | Bottom Toolbar |                                                                                                                                              |
|   | Content Drawer | C’est l’explorateur de votre projet. C'est une fenêtre qui affiche tous les assets, matériaux et autres fichiers contenus dans votre projet. |
|   | Output Log     | La console affiche les erreurs relatives à votre projet. (Erreur de compilation)                                                             |
|   | Cmd            | Permet d'éxécuter des commandes dans l'éditeur          


Les interactions dans l’éditeur graphique peuvent se faire à partir des boutons suivants : 

![unreal-04-move_button.png](/images/videogames/unreal/unreal-04-move_button.png){.align-center}

Dans l’ordre : Déplacement, Translation, Rotation, Echelle

L’exécution de l’application se fait à partir des boutons suivants : ![unreal-04-play_button.png](/images/videogames/unreal/unreal-05-play_button.png)

> Astuce : En tout temps, vous pouvez modifier la disposition des “Layouts” en cliquant sur Window > Load Layout. Ou les déplacer à la façon d’onglets.
{.is-info}


> Astuce : Vous pouvez également générer des primitives à l’écran (Cube, Sphere …), en appuyant sur le bouton  ![unreal-06-add_button.png](/images/videogames/unreal/unreal-06-add_button.png).
{.is-info}

> Pour plus de détail, rendez-vous directement sur la doc de Epic Games : https://dev.epicgames.com/documentation/fr-fr/unreal-engine/unreal-editor-interface
{.is-info}

# Focus : Content Drawer & Browser

> Elément central de votre projet, vous pouvez ouvrir votre explorateur de fichier de deux manières.
> - **Windows > Content Browser**, qui ouvrira une fenêtre indépendante, déplaçable comme un onglet.
> - En cliquant sur **Content Drawer** dans le **Bottom Panel**, ou en utilisant le raccourcie clavier **Ctrl + Esp**
> 
> ‎
{.is-success}


![unreal-07-content_drawer.png](/images/videogames/unreal/unreal-07-content_drawer.png)

# Terminologie | Convention de nommage

## Projet
> Un projet Unreal Engine 5 contient tout le contenu de votre jeu, avec des dossiers tels que Blueprints et Materials. Les dossiers peuvent être organisés à votre convenance. Chaque projet est associé à un fichier .uproject, qui permet de créer, ouvrir et enregistrer le projet.
{.is-success}


## Blueprint (le fameux)
> Le Blueprint est un système de scripting visuel qui utilise une interface par nœuds pour créer des éléments de gameplay. Il est utilisé pour définir des classes ou objets orientés objet (OO) dans l'éditeur Unreal.
{.is-success}


## Actors
> Tous les objets utilisés dans Unreal sont appelés des Actors (Acteurs). Un acteur est donc un objet pouvant être placé dans un niveau, comme une caméra ou un joueur. Il peut être transformé en 3D et manipulé via le code.
{.is-success}


## Pawn
Un pawn (pion) est un acteur représentant les personnages du jeu. Ils peuvent être contrôlés par le joueur ou l'IA.

Personnage
Un personnage est un type de pion avec des fonctionnalités supplémentaires pour le mouvement et les collisions.

Contrôleur de joueur
Il traduit les commandes du joueur en interactions dans le jeu, surtout en multijoueur où il gère les interactions réseau.

Contrôleur IA
Comme le contrôleur de joueur, mais pour les personnages non joueurs (PNJ).

État du joueur
Représente l'état d'un participant au jeu, avec des informations comme le score ou la santé. Il est synchronisé sur toutes les machines en multijoueur.

Mode de jeu
Le mode de jeu définit les règles du jeu (conditions de victoire, pause, etc.). En multijoueur, il n'existe que sur le serveur.

État du jeu
Contient les informations synchronisées pour tous les joueurs, comme le score ou l'état d'une partie.

Brosse
Une brosse est un acteur représentant une forme 3D, utilisée pour définir la géométrie du niveau.

Volume
Un volume est un espace 3D utilisé pour des effets variés, comme bloquer les acteurs ou infliger des dégâts.

Niveau
Un niveau est une zone de jeu définie, enregistrée sous forme de fichier .umap, contenant les acteurs et la géométrie.

Monde
Le monde est un conteneur pour tous les niveaux du jeu, gérant le streaming de niveaux et le spawn d'acteurs dynamiques.



