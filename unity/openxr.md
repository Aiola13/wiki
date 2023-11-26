---
title: Réalité Virtuelle | OpenXR
description: 
published: 1
date: 2023-11-26T13:52:57.502Z
tags: 
editor: markdown
dateCreated: 2023-11-26T11:23:40.707Z
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


1. Ajouter un Collider
	- Pour que l'objet soit saisissable, il doit avoir un Collider (par exemple, un BoxCollider ou SphereCollider). Assurez-vous que le Collider englobe la forme de l'objet de manière appropriée.
  - dans l'inspector > Add Component > Collider

2. Ajout du XR Grab Interactable
	- Ce composant permet à l'objet d'être reconnu comme saisissable par le système d'interaction XR.
	- dans l'inspector > Add Component > XR Grab Interatable
  
![openxr-08.png](/images/videogames/unity/openxr/openxr-08.png)

3. Cnfigurer le Comportement de Grabbing
	- Dans les propriétés du composant "XR Grab Interactable", vous pouvez configurer plusieurs options telles que la précision du grabbing, la réponse physique de l'objet lorsqu'il est saisi, et d'autres comportements interactifs.

![openxr-09.png](/images/videogames/unity/openxr/openxr-09.png)

Dans les propriétés du composant "XR Grab Interactable", vous pouvez configurer plusieurs options telles que la précision du grabbing, la réponse physique de l'objet lorsqu'il est saisi, et d'autres comportements interactifs.
Ajouter des Colliders :

Pour que l'objet soit saisissable, il doit avoir un Collider (par exemple, un BoxCollider ou SphereCollider). Assurez-vous que le Collider englobe la forme de l'objet de manière appropriée.
