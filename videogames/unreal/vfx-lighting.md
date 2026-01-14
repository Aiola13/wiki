---
title: Effets visuels et lumières
description: 
published: true
date: 2026-01-14T20:38:46.066Z
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

> **À retenir** : Dans Unreal, quand vous importez une Normal Map, veillez à ce que le **Compression Settings** soit bien sur **Normalmap** dans les propriétés de la texture. Sinon, ça ne marchera pas correctement !
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

## Récapitulatif

Vous avez maintenant compris :

- ✅ Ce qu'est une texture et les différents types (Base Color, Normal, Metallic, Roughness...)
- ✅ La différence entre définition et résolution
- ✅ Ce qu'est un Material et comment il utilise les textures
- ✅ Pourquoi le PBR a révolutionné le rendu 3D
- ✅ Ce qu'est un Shader et comment Unreal les rend accessibles
- ✅ Comment créer votre premier Material dans Unreal 5

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

  
  
  
