---
title: Réalité Virtuelle | OpenXR
description: 
published: true
date: 2024-12-11T08:33:32.912Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:33:32.912Z
---

# 1. Introduction à OpenXR

## 1.1 Qu'est-ce qu'OpenXR ?
> OpenXR est une norme ouverte développée par le consortium Khronos Group. Elle vise à standardiser le développement d'applications de réalité virtuelle (VR) et de réalité augmentée (AR), facilitant ainsi la création d'expériences VR/AR sur différents appareils et plateformes. C'est un outil puissant pour assurer la portabilité et la longévité de votre code VR.
{.is-success}


## 1.2 Pourquoi utiliser OpenXR en développement VR ?
- Intercompatibilité : OpenXR permet à vos applications de fonctionner sur une multitude de dispositifs VR sans avoir besoin de réécrire votre code pour chaque appareil spécifique.
- Futur-Proofing : En utilisant une norme ouverte, vous vous préparez pour les futures évolutions technologiques en VR.
- Communauté et Support : Bénéficiez d'une large communauté et du soutien de l'industrie.

# 2. Installation d'OpenXR dans un projet Unity

## 2.1 Prérequis
- Unity version 2020.3 LTS ou supérieure
- Un dispositif VR compatible (Oculus Quest 1\|2\|3, HTX vive, ect ...)

## 2.2 Étapes d'Installation

1. Créer un Nouveau Projet Unity :  
	- Ouvrez Unity Hub et créez un nouveau projet 3D.
  
![openxr-1.jpg](/images/videogames/unity/openxr/openxr-01.png)


2. Installer le XR Plugin Management :
	- Allez dans Window > Package Manager.
	- Recherchez et installez **XR Plugin Management**, **XR Interaction Toolkit** et **OpenXR Plugin**.
  - Installer également les samples de chaque Package.
  
![openxr-02.png](/images/videogames/unity/openxr/openxr-02.png)

3. Configurer OpenXR :
	- Dans Project Settings, allez dans XR Plugin Management.
	- Cochez OpenXR sous votre plateforme cible (par exemple, PC, Mac & Linux Standalone).
	- Dans l'onglet OpenXR, assurez-vous que les fonctionnalités requises sont activées.
  
![openxr-04.png](/images/videogames/unity/openxr/openxr-04.png)
  
4. Validation de l'Installation : 
	- Créez un environnement de test simple (un scene par exemple) pour vérifier que tout fonctionne correctement.
  - Insérer dans la hierachy via la vue project : **XR Device Simulator**, **XR Intreaction Setup**.
  - Supprimer la **Main Camera**
  
  |Hierarchy|XR Device Simulator|XR Interaction Setup|
  |
 |![openxr-05.png](/images/videogames/unity/openxr/openxr-05.png)|![openxr-06.png](/images/videogames/unity/openxr/openxr-06.png)|![openxr-07.png](/images/videogames/unity/openxr/openxr-07.png)|
  

> **XR Device Simulator** permet de se déplacer et d'intéragir grâce au clavier sans avoir de casque VR.
{.is-success}

> **XR Interaction Setup** permet de placer tous les éléments nécéssaire au fonctionnement de la VR dans la scène (dont la caméra).
{.is-success}
  
> Si jamais vous avez des erreurs dans la console implicant l'asset **Meta Gaze Adapter**, veuillez le supprimer.
{.is-warning}

![openxr-03.png](/images/videogames/unity/openxr/openxr-03.png =70%x)


# 3. Utilisation d'OpenXR

## 3.1 Activer les dispositifs

| Contrôleur gauche              | Casque                  | Contrôleur droit            | Grab | Trigger                    | Bouton Principal | Bouton Secondaire |
|--------------------------------|-------------------------|-----------------------------|------|----------------------------|------------------|-------------------|
| Maintenez la touche Maj gauche | Maintenez le clic droit | Maintenez la barre d'espace | G    | Appuyer sur le clic gauche | B                | N                 |


## 3.2 Grabbing

> Le terme "grabbing" en réalité virtuelle (VR) se réfère à l'action de saisir ou de tenir des objets virtuels à l'aide de contrôleurs VR. Cette interaction est fondamentale dans les expériences VR car elle permet aux utilisateurs d'interagir de manière naturelle et intuitive avec l'environnement virtuel, simulant l'acte de saisir des objets dans le monde réel.
{.is-success}

1. Sélectionnez l'objet dans votre scène Unity que vous voulez rendre saisissable.

2. Ajouter un Collider
	- Pour que l'objet soit saisissable, il doit avoir un Collider (par exemple, un BoxCollider ou SphereCollider). Assurez-vous que le Collider englobe la forme de l'objet de manière appropriée.
  - dans l'inspector > Add Component > Collider

3. Ajout du XR Grab Interactable
	- Ce composant permet à l'objet d'être reconnu comme saisissable par le système d'interaction XR.
	- dans l'inspector > Add Component > XR Grab Interactable
  
![openxr-08.png](/images/videogames/unity/openxr/openxr-08.png)

4. Configurer le Comportement de Grabbing
	- Dans les propriétés du composant "XR Grab Interactable", vous pouvez configurer plusieurs options telles que la précision du grabbing, la réponse physique de l'objet lorsqu'il est saisi, et d'autres comportements interactifs.

![openxr-09.png](/images/videogames/unity/openxr/openxr-09.png)

## 3.3 Snapping 

> Le terme "snapping" en réalité virtuelle (VR), désigne le processus par lequel un objet se positionne automatiquement dans un endroit spécifique ou adopte une orientation déterminée lorsqu'il est approché d'un certain point ou d'un autre objet. Cette fonctionnalité est souvent utilisée pour faciliter les interactions en VR, comme placer un objet à un emplacement précis avec une orientation correcte, ce qui peut être difficile à faire manuellement en raison des limitations de la perception de la profondeur en VR.
Le snapping est particulièrement utile pour des tâches comme assembler des pièces dans un puzzle VR, accrocher des outils sur un support, ou insérer un objet dans un emplacement précis.
{.is-success}

1. Choisissez l'objet dans votre scène Unity où vous souhaitez ajouter le socket interactor. Cet objet sera le point d'ancrage pour les objets interactifs.
2. Ajouter un Collider (Trigger) :
	- Un Collider est nécessaire pour que le Socket Interactor détecte quand un objet interactif est à proximité. Assurez-vous que le Collider est configuré pour englober la zone souhaitée pour le snapping et cocher la case Trigger.
3. Ajouter le Composant XR Socket Interactor 
	- Il agit comme une sorte de "docking station" pour les objets interactifs. C'est un point où des objets interactifs (généralement équipés de composants XR Grab Interactable) peuvent être "accrochés" ou "encastrés". Lorsqu'un objet interactif approche suffisamment d'un socket interactor, il peut se fixer automatiquement à ce point, souvent en s'alignant ou en s'ajustant pour s'adapter de manière précise.
	- Avec l'objet sélectionné, allez dans l'inspecteur et cliquez sur "Add Component".
	- Recherchez et ajoutez le composant "XR Socket Interactor".
4. Configurer le Socket Interactor :
	- Dans les paramètres du XR Socket Interactor, vous pouvez définir diverses options comme la distance à laquelle le snapping se déclenche, les conditions sous lesquelles un objet peut se fixer, et d'autres comportements de snapping.


![openxr-10.gif](/images/videogames/unity/openxr/openxr-10.gif)