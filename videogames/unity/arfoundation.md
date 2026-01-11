---
title: Réalité Augmentée | ARFoundation
description: 
published: true
date: 2026-01-11T14:32:49.865Z
tags: 
editor: markdown
dateCreated: 2025-12-11T21:33:02.353Z
---

# 1. Introduction à ARFoundation
## 1.1 Qu'est-ce qu'ARFoundation ?

> **ARFoundation** est un framework développé par Unity qui permet de créer des applications de réalité augmentée (AR) multiplateformes. Il fournit une API unifiée pour développer des expériences AR qui fonctionnent sur différents appareils (**iOS ARKit** et **Android ARCore**), sans avoir à réécrire votre code pour chaque plateforme spécifique.
{.is-success}


> Le package ARCore Extensions for AR Foundation (optionnel) ajoute des fonctionnalités supplémentaires comme les Cloud Anchors, les filtres de configuration caméra, et l'enregistrement/lecture de sessions AR.
{.is-warning}

## 1.2 Pourquoi utiliser ARFoundation en développement AR ?

- Compatibilité Multiplateforme : Développez une seule fois et déployez sur iOS (ARKit) et Android (ARCore) sans modifications majeures.
- API Unifiée : Une seule interface de programmation pour gérer les fonctionnalités AR communes (détection de plans, tracking, anchors, etc.).
- Écosystème Unity : Intégration native avec l'éditeur Unity et ses outils de développement.
- Évolutivité : Mises à jour régulières avec de nouvelles fonctionnalités AR au fur et à mesure de leur disponibilité.

## 2. Installation d'ARFoundation dans un projet Unity
### 2.1 Prérequis

- Unity version 2019 LTS ou supérieure
- Un smartphone compatible AR (iOS 11+ avec ARKit ou Android 7.0+ avec ARCore)
- Pour iOS : Xcode 16.0 ou supérieur installé sur macOS
- Pour Android : Android SDK et JDK configurés (installés avec l'éditor via Unity Hub)

### 2.2 Étapes d'Installation

1. Ajouter les modules nécessaires : 
	- Naviguez vers Installs > Manage de votre version Unity
  - Cochez Android Build Support ou IOS Build Support selon votre cas.
  - Cliquez sur Continue

![arfoundation-00.png](/videogames/unity/arfoundation/arfoundation-00.png)

![arfoundation-01.png](/videogames/unity/arfoundation/arfoundation-01.png)

2. Créer un Nouveau Projet Unity :
	- Ouvrez Unity Hub et créez un nouveau projet 3D (ou utilisez le template AR Core).


3. Installer les Packages Nécessaires :
	- Allez dans Window > Package Manager.
	- Recherchez et installez les packages suivants :
  		- AR Foundation (package principal)
		- ARCore XR Plugin (pour Android)
		- ARKit XR Plugin (pour iOS)
	- Installez également les Samples de AR Foundation pour des exemples de scènes.

![arfoundation-02.jpg](/videogames/unity/arfoundation/arfoundation-02.png)

![arfoundation-03.jpg](/videogames/unity/arfoundation/arfoundation-03.png)

![arfoundation-04.jpg](/videogames/unity/arfoundation/arfoundation-04.png)


4. Configurer XR Plugin Management :
	- Dans **Edit > Project Settings > XR Plugin Management**.
	- Cochez ARCore (pour Android) ou ARKit (pour iOS) selon votre plateforme cible
  	- Cochez XRSimulation (dans la catégorie PC)


5. Configuration des Paramètres de Build :
	- Pour Android :
		- Dans Project Settings > Player > Android.
		- Définissez Minimum API Level à Android 7.0 (API 24) ou supérieur.
		- Décochez Auto Graphics API et assurez-vous que Vulkan est en premier (ou supprimez OpenGLES3).

	- Pour iOS :
  		- Dans Project Settings > Player > iOS.
		- Définissez Target minimum iOS Version à 11.0 ou supérieur.
		- Ajoutez la Camera Usage Description (requis pour accéder à la caméra).
    
![arfoundation-05.jpg](/videogames/unity/arfoundation/arfoundation-05.png)
  
  
  
> BONNUS : Configurer les Paramètres de Build pour iOS et Android
	- Allez dans **File > Build Settings**.
	- Sélectionnez Android ou iOS comme plateforme cible et cliquez sur Switch Platform.
{.is-warning}

| Paramètre | Valeur |
| :--- | :--- |
| **Other Settings > Rendering** | Décochez Auto Graphics API et retirez Vulkan |
| **Other Settings > Package Name** | Format Java : `com.example.monAppAR` |
| **Other Settings > Minimum API Level** | API Level 24 (Android 7.0) minimum |
| **Other Settings > Scripting Backend** | IL2CPP (pour support ARM64) |
| **Other Settings > Target Architectures** | Activer ARM64 et ARMv7 |

> Important : ARFoundation nécessite un appareil physique pour tester. L'éditeur Unity ne peut pas simuler complètement les fonctionnalités AR.
> C'est pour cela qu'existe dans la categorie PC **XRSimulation**
{.is-warning}


# 3. Utilisation classique d'ARFoundation
## 3.1 Configuration de Base d'une Scène AR

1. Créer une Nouvelle Scène :
	- Créez une nouvelle scène vide ou supprimez les éléments par défaut.

2. Supprimer la Main Camera :
	- Supprimez la caméra par défaut de la scène.


3. Ajouter les Composants AR Essentiels :
	- AR Session : Clic droit dans la Hierarchy > XR > AR Session
		- Ce GameObject gère le cycle de vie de l'application AR (démarrage, arrêt, mise à jour du tracking)
  	- AR Session Origin (ou XR Origin selon la version) : Clic droit dans la Hierarchy > XR > XR Origin
		- Ce GameObject contient la caméra AR et gère le système de coordonnées AR vers Unity.

Une fois ces étapes terminées, votre fenêtre Hierarchy devrait ressembler à ceci :

```
Hierarchy
│
├── AR Session
└── XR Origin (ou AR Session Origin)
    └── AR Camera
```
    
> **AR Session** est obligatoire pour initialiser le système AR de l'appareil.
{.is-success}

> **XR Origin** contient automatiquement une caméra configurée pour l'AR qui remplace la Main Camera.
{.is-success}

## 3.2 Détection de Plans (Plane Detection)

> La détection de plans permet à l'application de reconnaître les surfaces planes dans l'environnement réel (sols, tables, murs). C'est une fonctionnalité essentielle pour placer des objets virtuels de manière réaliste dans le monde réel.
{.is-success}

1. Ajouter l'AR Plane Manager :
	- Sélectionnez le GameObject XR Origin dans la Hierarchy.
	- Dans l'Inspector, cliquez sur Add Component.
	- Recherchez et ajoutez AR Plane Manager.

![arfoundation-06.jpg](/images/videogames/unity/arfoundation/arfoundation-06.png)

2. Créer un Prefab pour Visualiser les Plans :
	- Créez un nouveau GameObject (clic droit > Create Empty).
	- Ajoutez un Mesh Renderer et un Mesh Filter.
	- Ajoutez le composant AR Plane et Line Renderer (pour visualiser les contours).
	- Sauvegardez ce GameObject comme Prefab.


3. Configurer l'AR Plane Manager :
	- Dans les paramètres de l'AR Plane Manager, assignez votre Prefab au champ Plane Prefab.
	- Choisissez le type de détection : Horizontal, Vertical, ou Both.

![arfoundation-07.jpg](/images/videogames/unity/arfoundation/arfoundation-07.png)

> Vous pouvez utiliser les prefabs fournis dans les Samples d'AR Foundation pour gagner du temps.
{.is-info}

## 3.3 Placement d'Objets avec Raycast

> Le Raycast AR permet de détecter où l'utilisateur touche l'écran dans l'espace 3D réel. C'est la méthode standard pour placer des objets virtuels dans l'environnement AR.
{.is-success}


1. Créer un Script de Placement :

Créez un nouveau script C# appelé ARObjectPlacement.cs

```csharp
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.XR.ARFoundation;
using UnityEngine.XR.ARSubsystems;

public class ARObjectPlacement : MonoBehaviour
{
    [SerializeField] private GameObject objectToPlace;
    [SerializeField] private ARRaycastManager raycastManager;
    
    private List<ARRaycastHit> hits = new List<ARRaycastHit>();

    void Update()
    {
        // Vérifier si l'utilisateur touche l'écran
        if (Input.touchCount > 0)
        {
            Touch touch = Input.GetTouch(0);
            
            // Seulement au moment du premier contact
            if (touch.phase == TouchPhase.Began)
            {
                // Effectuer un raycast depuis la position du touch
                if (raycastManager.Raycast(touch.position, hits, TrackableType.PlaneWithinPolygon))
                {
                    // Récupérer la position du hit
                    Pose hitPose = hits[0].pose;
                    
                    // Instancier l'objet à cette position
                    Instantiate(objectToPlace, hitPose.position, hitPose.rotation);
                }
            }
        }
    }
}
```


2. Attacher le Script :
	- Attachez ce script au GameObject XR Origin (ou créez un GameObject vide pour les scripts).
	- Assignez l'AR Raycast Manager (ajoutez le composant si nécessaire).
	- Assignez l'objet que vous souhaitez placer dans le champ Object To Place.


![arfoundation-08.jpg](/images/videogames/unity/arfoundation/arfoundation-08.png)

3. Ajouter l'AR Raycast Manager :
	- Sur le GameObject XR Origin, ajoutez le composant AR Raycast Manager si ce n'est pas déjà fait.

## 3.4 Utilisation des Anchors

> Les Anchors (ancres) permettent de "fixer" des objets virtuels à une position spécifique dans le monde réel. Le système AR ajuste automatiquement leur position pour compenser les changements de tracking, garantissant que les objets restent alignés avec l'environnement réel même si le tracking est temporairement perdu.
{.is-success}

1. Ajouter l'AR Anchor Manager :
	- Sur le GameObject XR Origin, ajoutez le composant AR Anchor Manager.


2. Créer un Anchor Programmé :
	- Modifiez votre script de placement pour créer un anchor :


```csharp
using UnityEngine.XR.ARFoundation;

public class ARObjectPlacement : MonoBehaviour
{
    [SerializeField] private GameObject objectToPlace;
    [SerializeField] private ARRaycastManager raycastManager;
    [SerializeField] private ARAnchorManager anchorManager;
    
    private List<ARRaycastHit> hits = new List<ARRaycastHit>();

    void Update()
    {
        if (Input.touchCount > 0)
        {
            Touch touch = Input.GetTouch(0);
            
            if (touch.phase == TouchPhase.Began)
            {
                if (raycastManager.Raycast(touch.position, hits, TrackableType.PlaneWithinPolygon))
                {
                    Pose hitPose = hits[0].pose;
                    
                    // Créer un anchor à cette position
                    ARAnchor anchor = anchorManager.AddAnchor(hitPose);
                    
                    // Attacher l'objet à l'anchor
                    if (anchor != null)
                    {
                        Instantiate(objectToPlace, anchor.transform);
                    }
                }
            }
        }
    }
}
```

> Les Anchors améliorent considérablement la stabilité des objets placés, particulièrement lors de sessions AR longues.
{.is-success}


## 3.5 Tester sur Appareil

1. Build et Déploiement :
	- Connectez votre appareil Android ou iOS.
	- Allez dans File > Build Settings.
	- Cliquez sur Build And Run.


2. Test de l'Application :
	- Lancez l'application sur votre appareil.
	- Déplacez lentement la caméra pour permettre au système de détecter les plans.
	- Touchez l'écran sur une surface détectée pour placer un objet.


> **Astuce** : Pour une meilleure détection, assurez-vous d'avoir un bon éclairage et évitez les surfaces uniformes sans texture.
{.is-success}

# 4. Utilisation avancée d'ARFoundation : Image Tracking

> L'Image Tracking (suivi d'images) permet à l'application AR de reconnaître et de suivre des images de référence dans le monde réel. Lorsque la caméra détecte une image enregistrée, vous pouvez afficher du contenu 3D superposé à cette image. C'est idéal pour créer des expériences AR déclenchées par des posters, des cartes, des couvertures de livres, etc.
{.is-success}

## 1.1 Préparer les Images de Référence

1. Choisir des Images Appropriées :
	- Les images doivent avoir des détails distinctifs et des contrastes élevés.
	- Évitez les images uniformes, floues ou avec trop de zones de couleur unie.
	- Format recommandé : JPG ou PNG, résolution minimum 300x300 pixels.

> **Astuce** : Les images avec des motifs géométriques, du texte, ou des logos fonctionnent généralement très bien.
{.is-success}

2. Créer une Reference Image Library :
	- Dans le dossier Project, clic droit > Create > XR > Reference Image Library.
	- Nommez-la (par exemple "MyImageLibrary").

![arfoundation-09.jpg](/videogames/arfoundation/arfoundation-09.png)

3. Créer une Reference Image Library :
	- Sélectionnez votre Reference Image Library.
	- Cliquez sur Add Image.
	- Assignez une texture (votre image de référence).
	- Donnez un nom à l'image.
	- Optionnel : Spécifiez les dimensions physiques réelles de l'image (en mètres) pour améliorer la précision.

![arfoundation-10.jpg](/videogames/arfoundation/arfoundation-10.png)

> Il est fortement recommandé de spécifier la taille physique réelle de l'image pour un meilleur tracking.
{.is-warning}


## 1.2 Configurer l'AR Tracked Image Manager

1. Ajouter le Composant :
	- Sélectionnez le GameObject XR Origin.
	- Dans l'Inspector, ajoutez le composant AR Tracked Image Manager.

![arfoundation-11.jpg](/videogames/arfoundation/arfoundation-11.png)

2. Configurer le Manager :
	- Dans Serialized Library, assignez votre Reference Image Library créée précédemment.
	- Dans Max Number Of Moving Images, définissez le nombre maximum d'images pouvant être trackées simultanément (0 = statiques uniquement, 1+ = images en mouvement).
	- Optionnel : Assignez un Tracked Image Prefab qui sera instancié sur chaque image détectée.

![arfoundation-12.jpg](/images/videogames/unity/arfoundation/arfoundation-12.png)

## 1.3 Configurer l'AR Tracked Image Manager

1. Créer un Prefab de Contenu :
	- Créez un GameObject avec le contenu 3D que vous souhaitez afficher (modèles, texte, effets).
	- Sauvegardez-le comme Prefab.


2. Assigner le Prefab :
	- Dans l'AR Tracked Image Manager, assignez votre Prefab au champ Tracked Image Prefab.
	- Unity instanciera automatiquement ce Prefab à chaque image détectée.


## 1.4 Tester l'Image Tracking

1. Build l'Application :
	-  Compilez et déployez sur votre appareil.


2. Test :
	- Imprimez vos images de référence ou affichez-les sur un écran.
	- Pointez la caméra vers l'image.
	- Le contenu 3D devrait apparaître automatiquement sur l'image.


> **Important** : Pour de meilleurs résultats, assurez-vous que l'image est bien éclairée et visible en entier.
{.is-warning}

<!-- 
# 5. Utilisation avancée d'ARFoundation : Face Tracking

> Le Face Tracking permet de détecter et de suivre les visages humains en temps réel. Cette fonctionnalité est particulièrement utile pour créer des filtres AR (comme Snapchat ou Instagram), des masques virtuels, ou des expériences interactives basées sur les expressions faciales.
{.is-success}


> Attention : Le Face Tracking nécessite un appareil avec une caméra frontale compatible. Sur iOS, seuls les appareils avec TrueDepth (iPhone X et supérieurs) supportent pleinement cette fonctionnalité. Sur Android, la disponibilité varie selon les appareils.
{.is-warning}


## 1.1 Vérifier la Compatibilité

Appareils compatibles :
	- iOS : iPhone X et supérieurs (avec caméra TrueDepth)
	- Android : Appareils supportant ARCore avec face tracking (liste limitée, vérifier la documentation Google ARCore)

## 1.2 Configurer le Face Tracking

1. Ajouter l'AR Face Manager :

Sélectionnez le GameObject XR Origin.
Ajoutez le composant AR Face Manager.

![arfoundation-13.jpg](/images/videogames/unity/arfoundation/arfoundation-13.png)

2. Créer un Prefab de Visage :

Créez un nouveau GameObject vide.
Ajoutez le composant AR Face.
Ajoutez un Mesh Filter et un Mesh Renderer (pour visualiser le mesh du visage).
Sauvegardez comme Prefab.


3. Configurer l'AR Face Manager :

Dans l'AR Face Manager, assignez votre Prefab au champ Face Prefab.
Configurez Maximum Face Count selon le nombre de visages à détecter simultanément (généralement 1 ou 2).


![arfoundation-14.jpg](/images/videogames/unity/arfoundation/arfoundation-14.png)

## 1.3 Changer la Caméra pour la Caméra Frontale

> Par défaut, ARFoundation utilise la caméra arrière. Pour le face tracking, nous devons basculer sur la caméra frontale.
{.is-info}

## 1.4 Vérifier la Compatibilité


## 1.5 Vérifier la Compatibilité


## 1.6 Vérifier la Compatibilité


## 1.7 Vérifier la Compatibilité

-->