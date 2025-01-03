---
title: La complexité
description: 
published: true
date: 2025-01-03T14:37:19.026Z
tags: 
editor: markdown
dateCreated: 2025-01-03T14:37:19.025Z
---



Complexité
Calculer la complexité des fonctions ci-dessous :

fonction conversion(n : entier):
    variable h, m, s, t : entier

    h ← n // 3600
    m ← (n - 3600 * h) // 60
    s ← n % 60
    RETOURNE t[h,m,s]
FF
fonction puissanceMoinsUn(n):
  variable h, m, s : entier

   SI n % 2 == 0 ALORS
      res ← 1
      SINON
        res ← -1
    FSI

   RETOURNE res
FF
fonction sommeEntiers(tableau, n):
  variable somme, i : entier

  somme ← 0

  POUR i ← 0 à i < n
    somme ← sommme + tableau[i]
  FPOUR

  RETOURNE somme
FF
fonction factorielle(n):
  variable fact, i : entier

  fact ← 1 
  i ← 2

  TANT QUE i <= n
    fact ← fact * i
    i ← i + 1
  FTQ

  RETOURNE fact
FF
Procedure triSelection(tableau[], tailleTableau : entier)
  variables passage, compteur, indexMin, stock : entiers

    DEBUT
        POUR passage <- 0 à passage < tailleTableau - 1
            indexMin <- passage;

            POUR (compteur <- passage + 1 à compteur < tailleTableau
              SI (tableau[compteur] < tableau[indexMin]) alors
                  indexMin <- compteur;
              FSI
            FPOUR

            Si passage <> indexMin
                stock <- tab[passage];
                tab[passage] <- tab[indexMin];
                tab[indexMin] <- stock;
            FSI

        FPOUR
    FIN
FP