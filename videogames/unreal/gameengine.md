---
title: Les bases de Unreal
description: 
published: true
date: 2024-12-11T08:37:10.651Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:37:10.651Z
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

#  Convention de nommage

> Dans Unreal (et pas seulement), il existe pour tous les objets des conventions de nommage. 
{.is-success}

En se positionnant dans le dossier **StarterContent**, dossier importé au démarrage d'un projet (si la case a été coché), on s'apperçoit qu'il y a une nommenclature.
![unreal-08-namming-01.png](/images/videogames/unreal/unreal-08-namming-01.png)

![unreal-08-namming-02.png](/images/videogames/unreal/unreal-08-namming-02.png)

> La forme générale est : **[AssetTypePrefix]\_[AssetName]\_[Suffix]\_[OptionalVariantLetterOrNumber]**
{.is-success}

> - AssetTypePrefix : Identifie le type de ressource (ex. : texture, modèle).
> - AssetName : Nom propre de la ressource.
> - Suffix : Fournit des informations supplémentaires sur la ressource (ex. : carte de normal ou carte d'opacité pour une texture).
> - OptionalVariantLetterOrNumber : Permet de différencier les versions ou variantes d'une ressource.
> 
> ‎
{.is-info}

| Asset                    | Prefix |
|--------------------------|--------|
| HDRI                     | HDR_   |
| Material                 | M_     |
| Material Instance        | MI_    |
| Physics Material         | PM_    |
| Post Process Material    | PPM_   |
| Skeletal Mesh            | SK_    |
| Static Mesh              | SM_    |
| Texture                  | T_     |
{.align-center}

> Ne pas utiliser d'espace dans le nom de vos objets
{.is-warning}





