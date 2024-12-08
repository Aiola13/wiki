---
title: Les tableaux
description: 
published: true
date: 2024-12-08T10:20:56.130Z
tags: 
editor: markdown
dateCreated: 2024-12-08T10:19:01.531Z
---

# Algorithmie et Tableaux

"Ne trompez jamais un compilateur ; il se vengera." - Henry Spencer.

Après avoir couvert les quatre structures logiques fondamentales de la programmation, explorons maintenant les tableaux.

### Utilité des Tableaux

Gérer plusieurs valeurs (ex. : 12 notes pour une moyenne) peut devenir complexe avec des variables distinctes (Note1, Note2, etc.). Les tableaux simplifient cela en regroupant les valeurs sous un nom commun, où chaque valeur est indexée numériquement.

**Exemple simple** :
- Sans tableau : Note1, Note2, ..., Note12
- Avec tableau : Note[0], Note[1], ..., Note[11]

### Définition et Usage

Un tableau est une collection de valeurs portant le même nom et différenciées par un indice. Les indices commencent généralement à 0.

**Déclaration d'un tableau** :
```pseudo
Note : tableau[0..11] de entier
```

**Utilisation** :
Pour lire ou assigner des valeurs, on utilise l'indice :
```pseudo
Note[0] = 15
Note[1] = 17
```

**Calcul de moyenne avec un tableau** :
```pseudo
Somme : entier = 0
Pour i de 0 à 11 Faire
    Somme = Somme + Note[i]
Fin Pour
Moyenne : entier = Somme / 12
```

### Tableaux Dynamiques

Quand le nombre d'éléments n'est pas connu à l'avance, on utilise des tableaux dynamiques. Ils sont déclarés sans taille initiale et redimensionnés dynamiquement.

**Exemple d'utilisation** :
```pseudo
Tableau Notes dynamique
Taille : entier
Lire Taille
Redimensionner Notes[Taille]
```

Cela permet de gérer efficacement les ressources, en adaptant la taille du tableau aux besoins réels du programme.