---
title: Unity, qu'est-ce donc ?
description: 
published: 1
date: 2023-12-01T14:32:41.649Z
tags: 
editor: markdown
dateCreated: 2023-11-26T16:42:50.559Z
---



# Qu'est-ce que Unity ?

> **Unity** est un moteur de jeu (**Game Engine**) multiplateformes pour réaliser des jeux vidéos (2D ou 3D) et des médias interactifs.
{.is-success}

> C’est un **Environnement de Développement Intégré** (**IDE**|Integrated Developpment Environment) qui permet entre autre de faire :
- les terrains (en 3D)
- les animations
- les effets spéciaux 
- l’audio
- l'IA
- la programmation des interactions (scripting)
- Rendu 3D
- Moteur Physique
{.is-success}


# Histoire

> L'Aventure Commence en **2004**, lorsque trois amis et développeurs, **David Helgason** (CEO), **Joachim Ante** (CTO) et **Nicholas Francis** (CCO), se réunissent dans un appartement à Copenhague avec comme objectif initial de développer leur propre jeu : **Gooball**. Ils se rendent compte que les outils disponibles à l'époque ne répondraient pas à leurs besoins. C'est alors qu'ils ont décidé de créer leur propre **moteur de jeu** sous le nom **d'Over the Edge Entertainment**, un outil qui permettrait aux développeurs de créer facilement des jeux sophistiqués. La société change de nom en 2007 sous **Unity Software Inc.**
{.is-success}


![gooball.webp](/images/videogames/unity/gooball.webp)

![unity-technologies-founders.jpg](/images/videogames/unity/unity-technologies-founders.jpg)

# Unity Hub

> Unity hub est une application permettant une meilleure gestion de vos projets ainsi que des versions de Unity utilisées.
{.is-success}

![unity-01.png](/images/videogames/unity/unity-01.png)
 
Pour l’installer, il suffit de se rendre sur le site officiel de Unity et de créer un compte avec une licence personnel ou étudiante (pour avoir quelques avantages). 
Download : https://unity3d.com/fr/get-unity/download
Account : https://id.unity.com/account/new

# Interface

L’interface se présente comme ceci : 

![unity-02.png](/images/videogames/unity/unity-02.png)

1.	Hierarchy : C’est la vue qui indique l’ensemble des objets (GameObject) et leurs relation.
2.	Inspector : Ce sont les paramètres (Component) de l’objet (GameObject) sélectionné.
3.	Scene : C’est la vue d’édition d’Unity (réglages positions, orientations, ajout d’objets …).
4.	Game : Exécution de l’application, c’est la vue de la Camera.
5.	Project : C’est l’explorateur de votre projet.
6.	Console : La console affiche les erreurs relatives à votre projet. (Erreur de compilation)

Les interactions dans l’éditeur graphique peuvent se faire à partir des boutons suivants : 

![unity-03.gif](/images/videogames/unity/unity-03.gif){.align-center}

Dans l’ordre : Déplacement, Translation, Rotation, Echelle

L’exécution de l’application se fait à partir des boutons suivants :

![unity-04.png](/images/videogames/unity/unity-04.png)

> Astuce : En tout temps, vous pouvez modifier la disposition des “Layouts” en cliquant sur Window > Layouts. Ou les déplacer à la façon d’onglets.
{.is-info}


> Astuce : Vous pouvez également générer des primitives à l’écran (Cube, Sphere …), dans GameObject > 3D Object.
{.is-info}

# GameObjects & Components

Tous les objets utilisés dans Unity sont appelés des GameObjects (Objets de jeu).
Ils contiennent des propriétés (Composants) appelées Components.

![unity-05.png](/images/videogames/unity/unity-05.png)

> Astuce : Un objet vide contiendra uniquement un composant de type Transform permettant de gérer ses propriétés spatiales (position, orientation, échelle)
> Un solide possèdera en plus un Mesh Filter (sa géométrie), Mesh Renderer (rendu visuel), Collider (gestion des collisions). 
{.is-info}


Concrétement les composants sont le cœur de « la programmation » de l’application, ce sont eux qui donnent des propriétés et des comportements aux objets de la scène.

> Astuce : Vous pouvez ajouter un component via AddComponent et vous pouvez les modifier, les supprimer ou les désactiver via l’Inspector.
{.is-info}

> On peut programmer ses propres composants grâces au scripting : une fois associés à un objet, ils apparaissent sous la même forme que les autres composants (voir scripts)
{.is-warning}

## Propriétés spatiales : Transform

## Propriétés spatiales : Graphe de scène
