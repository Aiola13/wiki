---
title: Les concepts du moteur Unity
description: 
published: true
date: 2024-12-11T08:32:46.175Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:32:46.175Z
---

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

Il existe un composant qui est présent sur tout objet (même vide) : Transform.
Le Transform stocke la position, l’orientation et l’échelle de l’objet sur lequel il est placé sous forme de vecteur selon un axe XYZ (représenté par des flèches de couleur RGB). 

> Astuce : Ces propriétés peuvent être modifiées :
> •	En édition via l’outil    ou directement via l’inspector.
> •	En exécution via scripting avec les méthodes appropriées.
{.is-info}


## Propriétés spatiales : Graphe de scène

Le graphe de scène permet une organisation des différents objets de la scène dans une hiérarchie.
•	Chaque objet n’a qu’un seul parent mais peut avoir plusieurs enfants.
•	Toute opération spatiale effectuée sur un objet est répercutée sur ses enfants.
•	L’objet en haut de la hiérarchie est la racine (root)

IMAGE

Comme dans tout espace 3D, il existe ce que l’on appelle un repère, qui permet d’identifier l’emplacement (les coordonnées) d’un objet dans l’espace. Il existe deux repères :
•	Coordonnées Locales définie par rapport à son parent
•	Coordonnées Globales définie par rapport à l’origine de la scène

IMAGE

> Astuce : Le transform d’un objet dans l’inspector est forcément local. On peut cependant accéder aux coordonnées globales et locales via script.
> NB : Pour que votre programme n’ait pas de comportement imprévu, il est recommandé de  toujours manipuler des modèles à une échelle uniforme (1, 1, 1). Pour cela il faut donc créer les modèles à la taille voulu dans un logiciel de modélisation 3D.
> 1 unité Unity = 1 mètre (100cm).
{.is-info}



## Propriétés géométriques et visuelles

IMAGE

Vous avez appris pour qu’un objet « existe », il faut que cet objet ait un maillage et sois rendu par la carte graphique. 
C’est ce à quoi servent respectivement les composants Mesh Filter & Mesh Renderer.


## Textures

IMAGE 
IMAGE

Une texture est une image repr�sentant une surface offrant la possibilit� de simuler l�apparence de celle-ci lorsqu'elle est plaqu�e sur un objet 3D.

Il existe plusieurs types de texture pour simuler différent effet :

1.  Albedo (ou Diffuse)![](Unity_Course_v1_fichiers/image034.gif)

L'Albedo est le type de texture le plus courant. Il définit la couleur et le motif de l'objet.

Astuce : Elle ne contient aucune information de lumi�re.

2.  Normal Map

La Normal Map est une technique utilis�e pour ajouter des détails à une surface sans augmenter le nombre de polygones. Elle peut repr�senter les détails de surface comme les rides, les rayures et les bords biseaut�s.![](Unity_Course_v1_fichiers/image036.jpg)![](Unity_Course_v1_fichiers/image038.gif)

Astuce : Ne pas oublier, dans les param�tres de la texture de Normal Map de la passer en Texture Type > Normal Map.

3.  Metallic

La Metallic Indique au shader si l�objet est en m�tal ou non. Il peut y avoir des valeurs de gris de transition, cela permet de simuler de fa�on satisfaisante des imperfections, ou la pr�sence d'un d�p�t de mati�re non m�tallique comme la poussi�re, sur la surface des m�taux, sans requ�rir � une meilleure r�solution de texture. ![](Unity_Course_v1_fichiers/image040.gif)

Astuce : M�tal brut = 1.0 (Blanc) et non m�tallique = 0.0 (Noir) / On la retrouve parfois de couleur rouge. En effet, car une texture est compos�e de plusieurs canaux (RGBA) et la metallic utilise le canal Rouge (R).

4.  Ambient Occlusion![](Unity_Course_v1_fichiers/image042.jpg)

L�Ambient Occlusion indique comment les diff�rents points de la surface sont expos�s � la lumi�re du milieu environnant. Elle permet d'assombrir les zones naturellement difficiles d'acc�s � la lumi�re. Cela a pour effet de faire ressortir les d�tails et la profondeur de la surface des objets.

5.  Emissive

L�Emissive ne re�oit pas d��clairage, de sorte que les pixels sont affich�s � pleine intensit�. Elle peut �tre utilis�e pour ajouter un effet de lueur, comme des runes magiques sur une �p�e, le mat�riau chauff� sur une torche ou une LED de veille sur une TV.

6.  Specular

La Specular contrôle la quantit� de lumi�re qui rebondit / est r�fl�chie par la surface d�un objet.

7.  Roughness

La Roughness d�crit la dispersion des rayons lumineux sur la surface d'un objet. Plus la surface est rugueuse, plus le reflet sera sombre et large. On peut l'apparenter à un reflet flous.

Astuce : Rugueux = 1.0 (Blanc) et Lisse = 0.0 (Noir) / Pour le shader �Standard� de Unity elle se situe dans la couche (A) Alpha de la Metallic Map.

![dessin illustrant la r�solution](Unity_Course_v1_fichiers/image044.jpg)

Ces textures peuvent avoir différentes définitions :

1.  256 \* 256 pixels
2.  512 \* 512 pixels
3.  1024 \* 1024 pixels (1k)
4.  2048 \* 2048 pixels (2k)
5.  4096 \* 4096 pixels (4k)

et peuvent avoir différentes résolutions :

1.  72 dpi
2.  150 dpi

Astuce : En France, nous avons souvent tendance à faire un abus de langage à propos de la 'Définition' que nous appelons 'Résolution'. Attention, dans le jeu vidéo à ne pas confondre les deux. ![](Unity_Course_v1_fichiers/image046.jpg)

On parle souvent également de textures dites 'Tileable' ou de temps en temps vous pourrez croiser ce terme 'Seamless', en des termes simples, une texture tileable est une image qui peut être placée à côté d'elle-même (au-dessus, au-dessous ou côte à côte) sans créer une disparité, une jonction ou une limite évidente entre les copies de l'image.

## Materials (PBR)

## Shader

## Camera

# Global Illumination

## Lights
