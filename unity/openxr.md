---
title: Réalité Virtuelle | OpenXR
description: 
published: 1
date: 2023-11-26T12:21:45.663Z
tags: 
editor: markdown
dateCreated: 2023-11-26T11:23:40.707Z
---

# 1. Introduction à OpenXR

## 1.1 Qu'est-ce qu'OpenXR ?
> OpenXR est une norme ouverte développée par le consortium Khronos Group. Elle vise à standardiser le développement d'applications de réalité virtuelle (VR) et de réalité augmentée (AR), facilitant ainsi la création d'expériences VR/AR sur différents appareils et plateformes. C'est un outil puissant pour assurer la portabilité et la longévité de votre code VR.
{.is-success}


## 1.2 Pourquoi utiliser OpenXR en développement VR ?
- Intercompatibilité
- Futur-Proofing
- Communauté et Support

# 2. Installation d'OpenXR dans un projet Unity

## 2.1 Prérequis
- Unity version 2020.3 LTS ou supérieure
- Un dispositif VR compatible (Oculus Quest 1\|2\|3, HTX vive, ect ...)
|
## 2.2 Étapes d'Installation
1. Créer un Nouveau Projet Unity
2. Installer le XR Plugin Management
3. Configurer OpenXR
4. Validation de l'Installation

# 3. Utilisation d'OpenXR pour le Grabbing en VR

## 3.1 Concepts Clés
- Action Manifest
- Action
- Grabbing

## 3.2 Mise en Place
1. Créer un Action Manifest
2. Configurer les Interactions
3. Programmer le Grabbing

## 3.3 Exemple de Script
```csharp
using UnityEngine;
using UnityEngine.XR.OpenXR.Input;

public class GrabScript : MonoBehaviour {
    // Votre code ici
}