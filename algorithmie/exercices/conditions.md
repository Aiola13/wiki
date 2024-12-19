---
title: Exercices : Les conditions
description: 
published: true
date: 2024-12-19T13:13:57.885Z
tags: 
editor: markdown
dateCreated: 2024-12-08T10:23:59.220Z
---

# Exercice 2.1
Écrire un algorithme qui demande un nombre à l’utilisateur, et l’informe ensuite si ce nombre est positif ou négatif (on laisse de côté le cas où le nombre vaut zéro).

# Exercice 2.2
Écrire un algorithme qui demande deux nombres à l’utilisateur et l’informe ensuite si leur produit est négatif ou positif (on laisse de côté le cas où le produit est nul). Attention toutefois : on ne doit pas calculer le produit des deux nombres.

# Exercice 2.3
Écrire un algorithme qui demande trois noms à l’utilisateur et l’informe ensuite s’ils sont rangés ou non dans l’ordre alphabétique.

# Exercice 2.4
Écrire un algorithme qui demande un nombre à l’utilisateur, et l’informe ensuite si ce nombre est positif ou négatif (on inclut cette fois le traitement du cas où le nombre vaut zéro).

# Exercice 2.5
Écrire un algorithme qui demande deux nombres à l’utilisateur et l’informe ensuite si le produit est négatif ou positif (on inclut cette fois le traitement du cas où le produit peut être nul). Attention toutefois, on ne doit pas calculer le produit !

# Exercice 2.6
Écrire un algorithme qui demande l’âge d’un enfant à l’utilisateur. Ensuite, il l’informe de sa catégorie :
"Poussin" de 6 à 7 ans
"Pupille" de 8 à 9 ans
"Minime" de 10 à 11 ans
"Cadet" après 12 ans

Peut-on concevoir plusieurs algorithmes équivalents menant à ce résultat ?

# Exercice 2.7
Ecrire un algorithme qui demande **a l’utilisateur de taper un chiffre et qui l'ecrit ensuite en toute lettre** a l’ecran. 
Par exemple, si l’utilisateur tape le chiffre 9, le programme affichera neuf.
Note : on ne s’occupera que des chiffres et pas de nombres en dehors de l’intervalle [0 − 9]

# Exercice 2.8
Ecrire un algorithme qui permet d'identifier si une année est bisextille ou non.
Si l’année A n’est pas divisible par 4, alors elle n’est pas bissextile Si A est divisible par 4, l’année est bissextile sauf si
A est divisible par 100 et pas par 400.
Exemples :
– 1901 n’est pas bissextile car non divisible par 4
– 2004 est bissextile car divisible par 4 et pas par 100
– 2100 n’est pas bissextile car divisible par 4, divisible par 100 mais pas par 400
– 2000 est bissextile car divisible par 4, par 100 et par 400
Ecrire un programme qui d´etermine si une ann´ee est bissextile ou non.

# Exercice 2.10
Ecrire un algorithme qui permet a l’utilisateur de saisir une valeur d’échelle et qui en réponse affichera **a l’écran la description associée** a ce nombre. Vous n’oublierez pas de gérer le cas où le nombre tapé par l’utilisateur est ”hors-échelle”.

L’échelle de Richter permet de d´ecrire la magnitude des tremblements de terre :
| Echelle| Description                                                           |
|-|-------------------------------------------------------------------------------------------------------|
| 1| Micro tremblement de terre, non ressenti                                                             |
| 2| Très mineur. non ressenti mais détecté                                                            |
| 3| Mineur. causant rarement des dommages                                                                |
| 4| Léger. Secousses notables d’objets à l’intérieur des maisons                                      |
| 5| Modéée. Légers dommages aux édifices bien construits                                             |
| 6| Fort. Destructeur dans des zones allant jusqu’à 180 kilomètres à la ronde si elles sont peuplées |
| 7| Majeur. Dommages modérés à sévères dans des zones plus vastes.                                  |
|8| Important. Dommages s´erieux dans des zones à des centaines de kilomètres à la ronde|
|9| Dévastateur. Dévaste des zones sur des milliers de kilomètres à la ronde|

Si le nombre n’est pas compris entre 1 et 9 c’est qu’il y a erreur de saisie (si inférieur à 1) ou que c’est l’appocalypse (si
supérieur à 9).