---
title: Effets visuels et lumières
description: 
published: true
date: 2026-01-14T21:59:00.393Z
tags: 
editor: markdown
dateCreated: 2025-11-06T13:18:38.015Z
---

# Les Textures et Materials dans Unreal Engine 5

## Introduction : Donnons vie à nos objets 3D !

Vous avez créé un magnifique modèle 3D d'une épée ? Parfait ! Mais pour l'instant, elle ressemble à un objet gris et fade, pas très excitant pour un joueur. C'est là qu'interviennent les **textures** et les **materials** ! 

Imaginez que vous venez d'acheter une maison neuve. Les murs sont tous blancs et lisses. Les textures, ce sont comme le papier peint, la peinture, et tous les détails que vous allez ajouter pour transformer ces murs blancs en quelque chose de vivant. Le material, lui, c'est la recette qui dit comment appliquer tout ça !

Dans ce chapitre, nous allons découvrir ensemble comment habiller vos objets 3D pour les rendre réalistes et attrayants. Prêts ? C'est parti !

---

## Les Textures : L'image qui fait toute la différence

### Qu'est-ce qu'une texture ?

Une **texture** est tout simplement une image que vous allez plaquer sur la surface d'un objet 3D. Comme si vous enveloppiez un cadeau avec du papier décoré !

> Une texture seule ne fait rien ! Elle a besoin d'un Material pour être appliquée à un objet.
{.is-info}

### Les différents types de textures

Unreal Engine 5 utilise plusieurs types de textures, chacune ayant un rôle spécifique. Voyons les principales :

#### 1. Base Color (l'ancienne Albedo/Diffuse)

C'est **la texture la plus importante** ! Elle définit simplement la couleur et les motifs de votre objet. Vous voulez un mur de briques rouges ? C'est dans la Base Color que vous mettez votre image de briques !

> **Important** : Cette texture ne contient AUCUNE information de lumière ou d'ombre. Juste la couleur pure. Les ombres, c'est le moteur qui s'en occupe !
{.is-warning}

#### 2. Normal Map (la magie des détails)

Ah, la Normal Map ! C'est un peu la magicienne des textures. Elle permet d'ajouter des **détails de relief** sans ajouter de polygones à votre modèle 3D.

Vous voulez des rides sur un visage, des rayures sur du métal, ou des joints entre les briques ? La Normal Map simule tout ça en jouant avec la lumière. Génial, non ?

> **À retenir** : Dans Unreal, quand vous importez une Normal Map, veillez à ce que le **Compression Settings** soit bien sur **Normalmap** (normalement c'est déjà la cas dans UNREAL 5) dans les propriétés de la texture. Sinon, ça ne marchera pas correctement !
{.is-success}

#### 3. Metallic (Métal ou pas métal ?)

Cette texture indique au moteur : "Hé, cet objet est-il en métal ou non ?"

- **Blanc (valeur 1.0)** = Métal pur (comme de l'acier poli)
- **Noir (valeur 0.0)** = Pas du tout métallique (comme du bois ou du plastique)
- **Gris** = Un entre-deux (utile pour simuler de la poussière sur du métal !)

> **Le saviez-vous ?** Dans Unreal, on parle du workflow **Metallic/Roughness**, qui est devenu le standard de l'industrie !
{.is-info}

#### 4. Roughness (Rugueux ou lisse ?)

La Roughness définit à quel point la surface est **rugueuse ou lisse**. Plus c'est rugueux, plus le reflet de lumière sera flou et diffus.

- **Blanc (valeur 1.0)** = Surface très rugueuse (pierre, béton)
- **Noir (valeur 0.0)** = Surface parfaitement lisse (miroir, eau calme)

Pensez à la différence entre du papier de verre (rugueux) et un miroir (lisse) !

#### 5. Ambient Occlusion (AO)

L'AO, c'est comme les petites ombres naturelles qui se créent dans les recoins. Dans les plis d'un vêtement, entre les planches d'un parquet, dans les joints des briques...

Elle **assombrit les zones difficiles d'accès à la lumière**, ce qui donne de la profondeur et du réalisme à vos objets.

> L'AO peut aussi être calculée automatiquement par Unreal avec le Lumen, mais une texture AO bien faite donne toujours un résultat supérieur !
{.is-success}

#### 6. Emissive (Ça brille !)

L'Emissive, c'est pour tout ce qui **émet de la lumière** : néons, LEDs, écrans, runes magiques, lave en fusion...

Cette texture ne reçoit pas de lumière, elle en produit ! Parfaite pour créer des effets lumineux stylés.

#### 7. Specular (Le brillant)

> **Note** : Dans Unreal 5 avec le workflow Metallic/Roughness (par défaut), on utilise rarement le Specular. Mais il existe toujours pour des cas spécifiques !
{.is-info}

Le Specular contrôle comment la lumière **rebondit** sur la surface. C'est surtout utilisé dans des workflows plus anciens.


![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*7O2NbLfvMZQeUOSQfeb-4Q.jpeg)

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*dLrSFVXBSoI5yH7-2KQHtw.jpeg)

---
## Comprendre les textures
 
> Via sketchfab, vous pouvez voir l'ensemble des modèles et des textures corredpondantes. Voici un apperçu de différents modèles 3D et leurs textures :

<center><div class="sketchfab-embed-wrapper"> <iframe title="Brougham Carriage - Game Ready 3D Model" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share width="1280" height="720" src="https://sketchfab.com/models/85d1ce24e2fc4c08b8f354bb4afd704c/embed?autostart=1&dnt=1"> </iframe> <p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;"> <a href="https://sketchfab.com/3d-models/brougham-carriage-game-ready-3d-model-85d1ce24e2fc4c08b8f354bb4afd704c?utm_medium=embed&utm_campaign=share-popup&utm_content=85d1ce24e2fc4c08b8f354bb4afd704c" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Brougham Carriage - Game Ready 3D Model </a> by <a href="https://sketchfab.com/kardaczynski?utm_medium=embed&utm_campaign=share-popup&utm_content=85d1ce24e2fc4c08b8f354bb4afd704c" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Szymon Kardaczynski </a> on <a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=85d1ce24e2fc4c08b8f354bb4afd704c" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a></p></div></center>


<center><div class="sketchfab-embed-wrapper"> <iframe title="Scaphandre "pieds lourds" US NAVY" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share width="1280" height="720" src="https://sketchfab.com/models/36d7ef8a455d4aaea080263250631ae8/embed?autostart=1&ui_hint=2"> </iframe> <p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;"> <a href="https://sketchfab.com/3d-models/scaphandre-pieds-lourds-us-navy-36d7ef8a455d4aaea080263250631ae8?utm_medium=embed&utm_campaign=share-popup&utm_content=36d7ef8a455d4aaea080263250631ae8" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Scaphandre "pieds lourds" US NAVY </a> by <a href="https://sketchfab.com/PHIO?utm_medium=embed&utm_campaign=share-popup&utm_content=36d7ef8a455d4aaea080263250631ae8" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> PHIO </a> on <a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=36d7ef8a455d4aaea080263250631ae8" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a></p></div></center>

<center><div class="sketchfab-embed-wrapper"> <iframe title="Post-Processing Demo: Vivi Ornitier" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share width="1280" height="720" src="https://sketchfab.com/models/5f75aaec31754ec981fcadbefc1441ed/embed?autostart=1&ui_hint=2&dnt=1"> </iframe> <p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;"> <a href="https://sketchfab.com/3d-models/post-processing-demo-vivi-ornitier-5f75aaec31754ec981fcadbefc1441ed?utm_medium=embed&utm_campaign=share-popup&utm_content=5f75aaec31754ec981fcadbefc1441ed" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Post-Processing Demo: Vivi Ornitier </a> by <a href="https://sketchfab.com/Sketchfab?utm_medium=embed&utm_campaign=share-popup&utm_content=5f75aaec31754ec981fcadbefc1441ed" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Sketchfab </a> on <a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=5f75aaec31754ec981fcadbefc1441ed" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a></p></div></center>
  
<center><div class="sketchfab-embed-wrapper"> <iframe title="SPY-HYPERSPORT" frameborder="0" allowfullscreen mozallowfullscreen="true" webkitallowfullscreen="true" allow="autoplay; fullscreen; xr-spatial-tracking" xr-spatial-tracking execution-while-out-of-viewport execution-while-not-rendered web-share src="https://sketchfab.com/models/158b48d550144451a59731720f63650a/embed"> </iframe> <p style="font-size: 13px; font-weight: normal; margin: 5px; color: #4A4A4A;"> <a href="https://sketchfab.com/3d-models/spy-hypersport-158b48d550144451a59731720f63650a?utm_medium=embed&utm_campaign=share-popup&utm_content=158b48d550144451a59731720f63650a" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> SPY-HYPERSPORT </a> by <a href="https://sketchfab.com/Amvall.Vall?utm_medium=embed&utm_campaign=share-popup&utm_content=158b48d550144451a59731720f63650a" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;"> Amvall </a> on <a href="https://sketchfab.com?utm_medium=embed&utm_campaign=share-popup&utm_content=158b48d550144451a59731720f63650a" target="_blank" rel="nofollow" style="font-weight: bold; color: #1CAAD9;">Sketchfab</a></p></div></center>

## La taille des textures : Définition et Résolution

### Les tailles courantes

Vos textures peuvent avoir différentes **définitions** (nombre de pixels) :

| Taille | Pixels | Usage typique |
|--------|--------|---------------|
| Petite | 256 × 256 | Objets lointains, mobiles |
| Moyenne | 512 × 512 | Objets secondaires |
| Standard | 1024 × 1024 (1K) | Objets moyens |
| **Recommandée** | **2048 × 2048 (2K)** | **Standard actuel** |
| Haute définition | 4096 × 4096 (4K) | Gros plans, objets héros |

> **Attention au piège** : En France, on confond souvent "définition" et "résolution". Dans le jeu vidéo :
> - **Définition** = nombre de pixels (1024×1024)
> - **Résolution** = densité de pixels (72 dpi, 150 dpi)
> 
> Ne mélangez pas les deux termes !
{.is-warning}

### Textures Tileable (ou Seamless)

Une texture **tileable** (répétable) est une image qui peut se répéter côte à côte sans qu'on voie de jointure visible. 

Imaginez un carrelage : si vous en mettez plusieurs côte à côte, ils doivent s'emboîter parfaitement ! C'est exactement pareil avec les textures tileable.

**Utilisation typique** : Sols, murs, terrains, surfaces répétitives

---

## Les Materials dans Unreal : La recette magique

### Qu'est-ce qu'un Material ?

Un **Material** dans Unreal, c'est comme une recette de cuisine. Vous prenez plusieurs ingrédients (vos textures), vous les mélangez d'une certaine façon (avec des calculs), et vous obtenez le rendu final sur votre objet !

> **Important** : Un Material est appliqué à un objet 3D. Un Material peut utiliser plusieurs textures en même temps.
{.is-info}

### La révolution PBR (Physically Based Rendering)

**Petite histoire** : Avant, dans les jeux vidéo, chaque artiste créait ses matériaux un peu "au feeling". Résultat ? Deux objets côte à côte pouvaient avoir des réactions à la lumière complètement différentes. C'était un cauchemar !

Puis est arrivé le **PBR** (Rendu Basé sur la Physique). L'idée ? Simuler comment la lumière se comporte **VRAIMENT** dans la réalité. Résultat : un rendu photoréaliste et cohérent partout !

> Unreal Engine 5 utilise le PBR nativement. Vos materials réagiront donc correctement à la lumière, automatiquement !
{.is-success}

**Avantages du PBR** :
- Cohérence visuelle dans toute la scène
- Rendu réaliste sous différents éclairages
- Workflow standardisé dans l'industrie
- Réutilisabilité des materials

---

## Les Shaders : Le cerveau derrière tout ça

### Mais c'est quoi, un Shader ?

Un **Shader**, c'est un petit programme (du code) qui dit au GPU comment afficher votre objet à l'écran. C'est lui qui calcule les couleurs, les reflets, les ombres...

Dans Unreal, vous ne codez pas directement les shaders (ouf !). Vous utilisez le **Material Editor**, une interface visuelle avec des petits nœuds à connecter. C'est beaucoup plus simple !

**Exemple concret** : Vous voulez une feuille d'arbre visible des deux côtés ? Il suffit de cocher "Two Sided" dans les propriétés du Material. Le shader s'adapte automatiquement !

---

## En pratique : Créer votre premier Material

### Étape 1 : Créer un Material

Dans le **Content Browser** (l'explorateur de fichiers d'Unreal) :

1. **Clic droit** dans une zone vide
2. **Materials & Textures** > **Material**
3. Donnez-lui un nom, par exemple `M_MonPremierMaterial`

> **Convention de nommage** : Dans Unreal, on préfixe souvent les Materials avec `M_` pour les reconnaître facilement !
{.is-info}

**Autres conventions courantes** :
- `T_` pour les Textures
- `MI_` pour les Material Instances
- `MF_` pour les Material Functions

### Étape 2 : Ouvrir le Material Editor

**Double-cliquez** sur votre Material. Vous voilà dans le Material Editor ! 

Vous voyez un gros nœud à droite avec plein d'entrées (Base Color, Metallic, Roughness...). C'est le **Material Result Node**, le point final où tout se connecte.

### Étape 3 : Ajouter vos textures

1. Glissez-déposez vos textures depuis le Content Browser vers le Material Editor
2. Connectez chaque texture à l'entrée correspondante du Material Result Node :
   - Base Color → Base Color
   - Normal → Normal
   - Metallic → Metallic
   - Roughness → Roughness
   - Ambient Occlusion → Ambient Occlusion

> Utilisez le clic gauche sur la sortie d'un nœud et glissez vers l'entrée d'un autre pour créer une connexion !
{.is-success}

### Étape 4 : Appliquer le Material

Glissez votre Material depuis le Content Browser directement sur un objet dans votre scène. Tadaaa ! 🎉

### Étape 5 : Prévisualiser en temps réel

Dans le Material Editor, vous pouvez voir votre material en temps réel sur une sphère de prévisualisation. Utilisez les boutons en bas pour changer la forme de prévisualisation (cube, plan, cylindre...).

---

## Les Landscape Materials : Peindre votre terrain

### Qu'est-ce qu'un Landscape Material ?

Imaginez que vous devez créer un terrain avec de l'herbe, de la terre, des rochers et du sable. Vous n'allez pas créer 4 terrains différents ! Un **Landscape Material** vous permet de **mélanger plusieurs textures** sur un même terrain et de "peindre" où chaque texture apparaît.

C'est comme si vous aviez une grande toile blanche (votre terrain) et plusieurs pots de peinture (vos layers) que vous pouvez appliquer où bon vous semble !

> Les Landscape Materials sont essentiels pour créer des environnements naturels et réalistes dans Unreal Engine 5.
{.is-success}

### Le principe des Layers (couches)

Un Landscape Material fonctionne avec un système de **layers** (couches). Chaque layer représente un type de surface :

- **Layer 1** : Herbe
- **Layer 2** : Terre
- **Layer 3** : Roche
- **Layer 4** : Sable

Vous allez ensuite **peindre** sur votre terrain pour dire "ici je veux de l'herbe, là de la roche, etc."

### Méthode professionnelle : MakeMaterialAttributes

Nous allons utiliser une approche **modulaire et flexible** avec le nœud **MakeMaterialAttributes**. Cette méthode permet de :
- Organiser proprement chaque layer
- Faciliter les modifications futures
- Créer des Material Instances pour ajuster les paramètres sans recompiler
- Avoir un workflow professionnel utilisé dans l'industrie

> **Pourquoi MakeMaterialAttributes ?** Ce nœud regroupe toutes les propriétés d'un material (Base Color, Normal, Roughness...) en un seul "paquet" que vous pouvez connecter facilement. C'est beaucoup plus propre !
{.is-info}

---

### Étape par étape : Créer votre Landscape Material

#### Étape 1 : Importer vos textures

Pour chaque layer, vous aurez besoin de **4 textures** :
- **Base Color** (la couleur)
- **Normal Map** (le relief)
- **Roughness** (la rugosité)
- **Ambient Occlusion** (les ombres)

Importez toutes vos textures dans le Content Browser en les glissant-déposant.

> **Astuce** : Organisez vos textures dans des sous-dossiers par type de surface (Grass/, Dirt/, Rock/, Sand/) pour vous y retrouver facilement !
{.is-success}

**Organisation recommandée** :
```
Content/
├── Textures/
│   ├── Grass/
│   │   ├── T_Grass_BaseColor
│   │   ├── T_Grass_Normal
│   │   ├── T_Grass_Roughness
│   │   └── T_Grass_AO
│   ├── Dirt/
│   ├── Rock/
│   └── Sand/
```

#### Étape 2 : Créer le Material Master

1. **Clic droit** dans le Content Browser
2. **Materials & Textures** > **Material**
3. Nommez-le `M_Landscape_Master`
4. **Double-cliquez** pour l'ouvrir dans le Material Editor

> **Important** : Dans le panneau **Details** du Material Result Node, cochez **"Use Material Attributes"**. Cela active le mode Material Attributes qui simplifie grandement le travail !
{.is-warning}

Vous remarquerez que le Material Result Node n'affiche maintenant plus qu'une seule entrée : **Material Attributes**. Parfait !

#### Étape 3 : Configurer le Tiling (répétition des textures)

Avant de connecter nos textures, nous allons créer un système de **tiling paramétrable**. Cela permet de contrôler facilement la répétition des textures.

**Créer les nœuds de base** :

1. **Clic droit** > Tapez "**TextureCoordinate**" et créez le nœud
2. **Clic droit** > Tapez "**Multiply**" et créez le nœud
3. **Clic droit** > Tapez "**Scalar Parameter**" et créez le nœud
   - Nommez-le `Tiling` ou `Tiling_Grass` si vous voulez un tiling par layer
   - Donnez-lui une **valeur par défaut** (ex: 10.0)

**Connecter les nœuds** :

```
[TextureCoordinate] ──► [Multiply] ◄── [Scalar Parameter "Tiling"]
                             │
                             ▼
                    (vers les UV des textures)
```

> **À quoi ça sert ?** Le TextureCoordinate donne les coordonnées UV de votre terrain. En les multipliant par un nombre (le Tiling), vous répétez la texture. Avec Tiling = 10, la texture se répète 10 fois sur le terrain !
{.is-info}

#### Étape 4 : Créer un Layer avec MakeMaterialAttributes

Nous allons créer le premier layer (Herbe). Vous répéterez ensuite le processus pour chaque layer.

**Pour le layer "Grass"** :

1. **Glissez-déposez** vos 4 textures d'herbe dans le Material Editor
2. **Créez un nœud "MakeMaterialAttributes"** (clic droit > cherchez "Make Material Attributes")
3. Ce nœud a plein d'entrées : Base Color, Normal, Roughness, Specular, etc.

**Connecter les textures** :

```
                        [Scalar Parameter "Tiling"]
                                   │
[TextureCoordinate] ──► [Multiply]─┼─► (vers tous les UV)
                                   │
                                   ▼
[T_Grass_BaseColor] ──UV          RGB──► [MakeMaterialAttributes - Base Color]
[T_Grass_Normal] ────UV           RGB──► [MakeMaterialAttributes - Normal]
[T_Grass_Roughness] ──UV          R───► [MakeMaterialAttributes - Roughness]
[T_Grass_AO] ────────UV           R───► [MakeMaterialAttributes - Ambient Occlusion]
```

> **Détail important** : Pour la Normal Map, n'oubliez pas de configurer le **Sampler Type** sur "Normal" dans les propriétés de la texture (ou le Texture Sample node) !
{.is-warning}

**Vous obtenez maintenant un nœud MakeMaterialAttributes qui contient toutes les infos de votre couche d'herbe !**

#### Étape 5 : Répéter pour chaque Layer

**Répétez l'étape 4** pour chaque couche que vous voulez (Dirt, Rock, Sand...).

Vous aurez donc :
- Un groupe de textures + MakeMaterialAttributes pour l'herbe
- Un groupe de textures + MakeMaterialAttributes pour la terre
- Un groupe de textures + MakeMaterialAttributes pour la roche
- Un groupe de textures + MakeMaterialAttributes pour le sable

> **Astuce** : Vous pouvez utiliser un paramètre de Tiling différent pour chaque layer si certaines textures ont besoin d'être plus ou moins répétées que d'autres !
{.is-success}

**Conseil d'organisation** : Utilisez des **Comment Boxes** (touche C) pour encadrer chaque layer et le nommer. Ça garde votre graphe propre et lisible !

#### Étape 6 : Créer le Landscape Layer Blend

Maintenant, nous devons **mélanger** tous ces layers avec un nœud spécial.

1. **Clic droit** > Tapez "**Landscape Layer Blend**"
2. Sélectionnez le nœud **Landscape Layer Blend**
3. Dans le panneau **Details**, section "**Layers**"
4. Cliquez sur le **+** autant de fois que vous avez de layers (4 fois dans notre exemple)

**Pour chaque entrée du Layer Blend** :

| Propriété | Valeur | Exemple |
|-----------|--------|---------|
| **Layer Name** | Nom du layer | `Grass`, `Dirt`, `Rock`, `Sand` |
| **Blend Type** | Type de mélange | `LB_WeightBlend` |

> **Nommage crucial** : Les noms des layers sont **très importants** ! C'est avec ces noms que vous allez peindre sur le terrain. Choisissez des noms clairs et cohérents.
{.is-warning}

#### Étape 7 : Connecter les Material Attributes au Layer Blend

C'est le moment de tout connecter !

**Chaque sortie de MakeMaterialAttributes** se connecte à **une entrée du Landscape Layer Blend** :

```
[MakeMaterialAttributes - Grass] ──► [LandscapeLayerBlend - Layer 0 "Grass"]
[MakeMaterialAttributes - Dirt]  ──► [LandscapeLayerBlend - Layer 1 "Dirt"]
[MakeMaterialAttributes - Rock]  ──► [LandscapeLayerBlend - Layer 2 "Rock"]
[MakeMaterialAttributes - Sand]  ──► [LandscapeLayerBlend - Layer 3 "Sand"]
```

**Puis connectez la sortie du Layer Blend au Material Result** :

```
[LandscapeLayerBlend - Output] ──► [Material Result - Material Attributes]
```

> **Vérification** : Votre graphe devrait ressembler à 4 (ou plus) groupes de textures qui passent chacun par un MakeMaterialAttributes, puis tous se rejoignent dans le LandscapeLayerBlend, qui va vers le Material Result.
{.is-success}

**N'oubliez pas de sauvegarder votre Material !**

#### Étape 8 : Créer une Material Instance

Maintenant que votre Material Master est prêt, nous allons créer une **Material Instance**. C'est comme une "copie allégée" de votre material qui permet de modifier les paramètres (comme le Tiling) **sans recompiler** le material !

**Créer la Material Instance** :

1. **Clic droit** sur votre `M_Landscape_Master` dans le Content Browser
2. Sélectionnez **"Create Material Instance"**
3. Nommez-la `MI_Landscape_Master` (MI pour Material Instance)

> **Pourquoi une Material Instance ?** C'est beaucoup plus rapide ! Modifier un paramètre dans une Material Instance est **instantané**, alors que recompiler un Material peut prendre plusieurs secondes.
{.is-info}

#### Étape 9 : Appliquer la Material Instance au Landscape

1. Sélectionnez votre **Landscape** dans la scène (Viewport)
2. Dans le panneau **Details**, cherchez la section **Landscape Material**
3. Assignez votre `MI_Landscape_Master` (pas le Material Master, mais l'Instance !)

#### Étape 10 : Créer les Layer Info (Weight-Blended)

Avant de pouvoir peindre, vous devez créer les **Layer Info** pour chaque layer.

1. En haut de l'interface, cliquez sur le **mode Landscape** (ou appuyez sur **Shift+2**)
2. Dans le panneau Landscape, allez dans l'onglet **"Paint"**
3. Vous verrez vos layers listés : Grass, Dirt, Rock, Sand
4. À droite de chaque layer, cliquez sur le **bouton +**
5. Sélectionnez **"Weight-Blended Layer (normal)"**
6. Choisissez un emplacement pour sauvegarder le fichier (ex: `Content/Landscape/LayerInfos/`)

Répétez pour **chaque layer**.

> **À quoi servent les Layer Info ?** Ce sont des fichiers qui stockent les informations de peinture (le "poids" de chaque layer à chaque endroit du terrain). Sans eux, impossible de peindre !
{.is-warning}

#### Étape 11 : Configurer le Tiling dans la Material Instance

Maintenant que tout est en place, vous pouvez ajuster le tiling de vos textures !

1. **Double-cliquez** sur votre `MI_Landscape_Master`
2. Dans le panneau de gauche, vous verrez vos paramètres (dont "Tiling")
3. **Cochez la case** à gauche du paramètre pour l'activer
4. **Ajustez la valeur** (ex: 10, 20, 50...) pour voir la texture se répéter plus ou moins

> **Astuce** : Vous pouvez modifier cette valeur en temps réel et voir le résultat immédiatement dans le Viewport ! C'est l'avantage des Material Instances.
{.is-success}

**Valeurs typiques** :
- **5-10** : Textures très grandes (pour gros plans)
- **20-30** : Taille standard
- **50+** : Textures petites et répétées (pour éviter le flou de loin)

#### Étape 12 : Peindre votre Landscape !

Ça y est, tout est prêt ! 🎨

**En mode Landscape > Paint** :

1. **Sélectionnez un layer** dans la liste (ex: Grass)
2. **Réglez la taille du brush** avec **Brush Size**
3. **Réglez l'intensité** avec **Tool Strength** (0.1 à 1.0)
4. **Cliquez et glissez** sur le terrain pour peindre !

**Raccourcis ultra-utiles** :

| Raccourci | Action |
|-----------|--------|
| **Ctrl + Molette** | Ajuster la taille du brush |
| **Clic + Glisser** | Peindre le layer sélectionné |
| **Shift + Clic + Glisser** | Effacer le layer (réduire son poids) |

> **Les layers se mélangent automatiquement !** Quand vous peignez un nouveau layer, Unreal crée une transition douce avec les layers existants. Le résultat est naturel et réaliste.
{.is-success}

---

### Récapitulatif du Workflow

Voici un résumé de la méthode complète :

1. ✅ **Importer les textures** (Base Color, Normal, Roughness, AO)
2. ✅ **Créer le Material Master** et activer "Use Material Attributes"
3. ✅ **Créer le système de Tiling** (TextureCoordinate → Multiply → Scalar Parameter)
4. ✅ **Relier les textures aux UV** (sortie du Multiply vers les UV de toutes les textures)
5. ✅ **Créer les MakeMaterialAttributes** (un par layer)
6. ✅ **Relier les textures aux bonnes colonnes** du MakeMaterialAttributes
7. ✅ **Répéter pour chaque layer** (Grass, Dirt, Rock, Sand...)
8. ✅ **Créer le Landscape Layer Blend** et renommer les layers correctement
9. ✅ **Connecter les Material Attributes aux layers** du Layer Blend
10. ✅ **Connecter le Layer Blend au Material Result**
11. ✅ **Créer une Material Instance**
12. ✅ **Appliquer la Material Instance au Landscape**
13. ✅ **Créer les Layer Info** (Weight-Blended) via le bouton +
14. ✅ **Cocher/ajuster le Tiling** dans la Material Instance
15. ✅ **Peindre sur le terrain** !

---

### Schéma complet du workflow

```
POUR CHAQUE LAYER (Grass, Dirt, Rock, Sand) :

[TextureCoordinate] ──► [Multiply] ◄── [Scalar Parameter "Tiling"]
                             │
                      ┌──────┴──────┬──────────┬──────────┐
                      │             │          │          │
                     UV            UV         UV         UV
                      │             │          │          │
                      ▼             ▼          ▼          ▼
            [T_BaseColor]   [T_Normal]   [T_Rough]   [T_AO]
                  RGB           RGB          R          R
                   │             │           │          │
                   └─────────────┴───────────┴──────────┘
                                 │
                                 ▼
                      [MakeMaterialAttributes]
                                 │
                                 ▼
                    [LandscapeLayerBlend - Layer X]


TOUS LES LAYERS SE REJOIGNENT :

[LandscapeLayerBlend - Output] ──► [Material Result - Material Attributes]
```

---

### Astuces de pro

**1. Tiling différent par layer**

Certaines textures ont besoin d'être plus ou moins répétées. Créez un paramètre de Tiling **par layer** :
- `Tiling_Grass = 20`
- `Tiling_Dirt = 25`
- `Tiling_Rock = 15`
- `Tiling_Sand = 30`

**2. Variation procédurale**

Ajoutez du **Noise** pour casser la répétition :

```
[Noise] ──► [Multiply (0.2)] ──► [Add] ◄── [Tiling Parameter]
                                   │
                                   ▼
                        (vers TextureCoordinate)
```

**3. Optimisation des performances**

- **Maximum 4-6 layers** sur un Landscape
- Textures en **2K** (2048×2048) suffisent pour un terrain
- Activez le **Virtual Texturing** pour les très grands terrains

**4. Organisation du Content Browser**

```
Content/
├── Landscape/
│   ├── Materials/
│   │   ├── M_Landscape_Master
│   │   └── MI_Landscape_Master
│   ├── LayerInfos/
│   │   ├── Grass_LayerInfo
│   │   ├── Dirt_LayerInfo
│   │   ├── Rock_LayerInfo
│   │   └── Sand_LayerInfo
│   └── Textures/
│       ├── Grass/
│       ├── Dirt/
│       ├── Rock/
│       └── Sand/
```

> **Conseil final** : Testez votre Landscape en jeu (PIE - Play In Editor) régulièrement ! Vérifiez les performances, les transitions entre layers, et l'apparence sous différents angles et éclairages.
{.is-success}


---

## Pour aller plus loin

### Ressources recommandées

**Sites de textures gratuites** :
- [Fab](https://www.fab.com/) (intégré à Unreal Engine !)
- [Poly Haven](https://polyhaven.com/)
- [Textures.com](https://www.textures.com/)
- [CC0 Textures](https://cc0textures.com/)

**Documentation officielle** :
- [Unreal Engine Materials Documentation](https://docs.unrealengine.com/5.3/en-US/unreal-engine-materials/)
- [PBR Guide by Adobe (ex-Allegorithmic)](https://substance3d.adobe.com/tutorials/courses/the-pbr-guide-part-1)
<!--
### Prochaines étapes

Dans les prochains chapitres, vous découvrirez :
- Le Material Editor avancé
- Les Material Instances pour optimiser vos performances
- Les Material Functions pour réutiliser du code
- Les effets avancés (transparence, reflets, animations...)

> **Conseil de pro** : Entraînez-vous ! Téléchargez des textures gratuites et créez vos propres Materials. C'est en forgeant qu'on devient forgeron !
{.is-success}


**Bon courage, et amusez-vous bien !** 🚀 -->

 Material landscape
 
 Importer vos textures, makematerialattributes, relier les bonnes colonnes, 
 texcoordinate, multiply, tilling (param), relier canaux UV des textures, 
 
 répéter actions nombres de cpouches (layer) différentes sur landscape, 
 
 créer lanscapelayerblend, renommer corectement les layers et relier les attributs aux layer.
 
 Cocher USE MATERIAL ATTRIBUTE
 
 Créer une material instance et appliquer le material au lanscape.
 
 cliquer sur le plus pour créer le layer whiteblend
 
 cocher dans le material instance le tiling
 
 
 Activer le displacement, dans defaultengine.ini, coller : 
 r.Nanite.AllowTessellation=1
 r.Nanite.Tessellation=1
  
  
