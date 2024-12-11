---
title: Lexique
description: 
published: true
date: 2024-12-11T08:35:09.589Z
tags: 
editor: markdown
dateCreated: 2024-12-11T08:35:09.589Z
---

# Léxique

## Nanite
> **Nanite** est une technologie de rendu de géométrie virtuelle qui utilise un **système de micropolygones adaptatifs**. Elle permet de gérer et de rendre en temps réel des modèles avec des milliards de triangles (polygones), en optimisant dynamiquement les niveaux de détail (**LOD**) sans intervention manuelle (en utilisant un streaming adaptatif). Nanite optimise les ressources GPU en ne rendant que les polygones visibles à l'écran. Pour cela, il utilise un culling hiérarchique à base de clusters et un streaming efficace de données géométriques, réduisant ainsi l'impact sur la mémoire et le GPU tout en maintenant une qualité visuelle optimale.
{.is-success}

## Lumen
> **Lumen** est un système de global illumination dynamique qui calcule en temps réel (sans baking) la lumière indirecte et les réflexions. Il repose sur une combinaison de techniques de ray tracing et d'illumination voxelisée pour simuler la lumière rebondissante et les réflexions multi-bounces.
{.is-success}

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
> Un pawn (pion) est un acteur représentant les personnages du jeu. Ils peuvent être contrôlés par le joueur ou l'IA.
{.is-success}


## Character
> Un personnage est un type de pion avec des fonctionnalités supplémentaires pour le mouvement et les collisions.
{.is-success}


## Player Controller
> Il traduit les commandes du joueur en interactions dans le jeu, surtout en multijoueur où il gère les interactions réseau.
{.is-success}
