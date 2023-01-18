---
title: Les instructions
description: 
published: 1
date: 2023-01-18T21:17:22.884Z
tags: algo, algorithmie, instructions
editor: markdown
dateCreated: 2023-01-18T21:17:22.884Z
---

# Les instructions

## Les expressions

Une expression représente une succession de calculs, elle peut faire intervenir des constantes, des variables, des fonctions et des opérateurs.

Une expression peut être :

- une valeur
- une variable
- une constante
- un appel à une fonction
- Opérateur Binaire
  - \<expression> opérateurBinaire \<expression>
- Opérateur Unaire
  - opérateurUnaire \<expression>
    - incrémetation $x++$
    - Opposé $-x$
    - Valeur Absolue $|x|$
    - Carré $x^2$
- Opérateur Logique (ce que nos appelons <span style="color:#D7BA7D">Expression Booléenne</span>)

### Les opérateurs :

### Les opérateurs arithmétiques

- Les classiques :
  - `–` (unaire) Changement de signe
  - `+` Addition
  - `–` Soustraction
  - `*` Multiplication
  - `/` Division flottante ou euclidienne
  - `%` Modulo (reste de la division entière)

N.B : Les opérandes peuvent être du type entier (le résultat est entier) ou réel (le résultat est à virgule), sauf pour la division flottante, où le résultat sera toujours de type réel et pour le **modulo**, où le resultat sera toujours un **entier**.

### Les opérateurs logiques (et binaires) (de comparaison)

Lorsque opérandes sont booléennes, on a alors une opération logique. Le résultat est un booléen. Les expressions booléennes sont utilisées comme conditions dans les structures de contrôles.

- Négation logique
  - En français (NON)
  - En anglais (NOT)
  - En signe (!)
- Et logique
  - En français (ET)
  - En anglais (AND)
  - En signe (&&)
- Ou logique
  - En français (OU)
  - En anglais (OR)
  - En signe (||)
- Ou exclusif (que l'on utilisera que très rarement)
  - En français (OUEX)
  - En anglais (XOR)
  - En signe (^)

**Rappels** : avec a et b des booléens ou des expressions booléennes :

- `a ET b`
  - n’est vrai que si a est vrai et b est vrai
  - est faux dès qu’un des deux est faux

![Mon image](<../images/ET_(Small).png>)

- `a OU b`
  - n’est faux que si a est faux et b est faux
  - est vrai dès qu’un des deux est vrai

![Mon image](<../images/OU_(Small).png>)

- `a OUEX b`
  - est vrai si un des deux seulement est vrai
  - est équivalent à `a != b` ou `a <> b`

![Mon image](<../images/OUEX_(Small).png>)

**Important** : Les opérateurs `et` et `ou` sont séquentiels : si l’évaluation de la première opérande suffit à donner le résultat, la deuxième n’est pas évaluée.

### Les opérateurs relationnels

Les deux opérandes doivent être de types compatibles. Le résultat est toujours de type booléen : vrai ou faux.

- `=` égal
- `<>` ou `!=` différent
- `<` strictement inférieur à
- `>` strictement supérieur à
- `<=` inférieur ou égal
- `>=` supérieur ou égal

### La concaténation de chaînes

L’opérateur « + » peut être utilisé avec les chaînes de caractères et les caractères pour la concaténation.

```
a ← 5
afficher("Ma variable est a = " + a)

$ Ma variable est a = 5
```

### Règles des priorités des expressions

Les mêmes règles s'appliquent qu'en mathétiques et arithmétiques ...

Classement par ordre décroissant :

- opérateurs unaires
- opérateurs arithmétiques
- opérateurs relationnels

![mon image](<../images/regles-priorite-operateurs_(Small).png>)

N.B :

- ⬅ Si nous avons une suite d'opérateurs binaires de la même classe, l'évaluation se fait en passant de la gauche vers la droite dans l'expression.
- ➡ Pour les opérateurs unaires (!,++,--) et pour les opérateurs d'affectation (=,+=,-=,\*=,/=,%=), l'évaluation se fait de droite à gauche dans l'expression.

## L’affectation

Cette instruction permet d’affecter une valeur à une variable. La valeur peut être n’importe quelle expression de type compatible avec la variable.

Syntaxe

```
maVariable ← <expression>
```

## Les appels aux fonctions et procédures

Qu'est ce qu'une procédure et une fonction ? Aussi appelées <span style="color:#D7BA7D">**routine**</span> (un bloc de code), elles prennent une liste d'arguments en paramètre (entre parenthèses) et se définissent par :

- Procédure : Instruction qui ne renvoi pas de valeur (ex : Une structure de comparaison)
- Fonction : Instruction qui a contrario renvoi une valeur

### Appel de procédure = une instruction

L’appel de procédure est une instruction à part entière :

```
procedure(param1, param2, ...)
```

#### Exemples de procédures : les entrées-sorties

- Les procédures d’affichage : ECRIRE ou AFFICHER
<p align="right">(En anglais : PRINT or DISPLAY)</p>

```
ECRIRE("Nombre de voitures : ", x)

"affiche sur l’écran (ou écrit dans un fichier) la chaîne ‘Nombre de voitures : ‘, suivi du contenu de la variable x."
```

OU

```
AFFICHE(12+a)

"affiche la valeur de l’expression12+a."
```

- La procédure de lecture : LIRE
<p align="right">(En anglais : READ)</p>

```
LIRE(x)

affecte à la variable x la valeur saisie (sur le clavier ou dans un fichier).
```

### Appel de fonction

L’appel de procédure est une instruction à part entière :

```
variable ← fonction(param1, param2, ...)
```

**Note** : un appel de fonction seul n’est pas une instruction !

# Boucles et Conditions

[comment]: #'CONDITIONS'

## Structure Alternative et de choix

### Structure Alternative

Admettons la condition suivante SI - ALORS - SINON

Fonctionnement : Si la condition (exprimée par l’expression booléenne) est vraie alors seule la suite d’instructions placée après le ALORS sera exécutée. Dans le cas contraire, si la partie SINON existe elle sera exécutée, si elle n’existe pas, rien ne se passe. Utilisation :

Syntaxe :

```
SI <expression booléenne> ALORS
    <instruction>
    ...
    SINON <instruction>
    ...
FIN_SI
```

<p align="right">(En anglais : IF - THEN - ELSE - ENDIF)</p>

Remarque : la partie SINON <instruction> est facultative.

Attention : Le FIN_SI est obligatoire ! Il en sera de même pour toutes les instructions structurées : cette marque de fin doit être présente même si il n’y a qu’une seule instruction.

##### Exemple

Pseudo-code

```
SI note >= 12
    ALORS afficher("Reçu avec mention AB")
    SINON SI note > 10
        ALORS afficher("Reçu mention Passable")
        SINON afficher("Insuffisant")
        FSI
    FSI
FSI
```

## Structure de Choix Multiple

Admettons la condition suivante SELON

Fonctionnement : Les instructions exécutées seront celles correspondant à la valeur de l’expression. Utilisation : L’expression doit être de type scalaire : les types entiers et le type caractère.

Pseudo-Code

```
SELON _<variable>_
    <liste_valeur> : <instruction>
            ...     : ...
      {AUTREMENT : <instruction> }
FIN_SELON
```

<p align="right">(En anglais :  CASE… OF – OTHERS – ENDCASE)</p>

##### Exemple - FaitLeTotal - équivalent boucle _POUR_

Pseudo-code

```
SELON abrevation
    "M": afficher("Monsieur")
    "Mme": afficher("Madame")
    "Mlle": afficher("Mademoiselle")
    AUTREMENT: afficher("Monsieur, Madame")
```

[comment]: #'BOUCLES'

## Structures de répétition

### Les boucles _TANT QUE ... FAIRE_ (While...EndWhile)

Fonctionnement : Répéter une suite d'instructions un certain nombre de fois. Utilisation : Structure itérative "universelle", elle peut être utilisé tout le temps.

Pseudo-code

```
TANT_QUE <expression logique booléenne vraie> faire
    <traitement> {suite d'instruction}
FIN_TANT_QUE
```

#### Sa sémantique

Mais que fait finalement cette structure ? 🤔

- Elle répète une suite d'instruction tant que la condition booléenne n'est pas atteinte.

##### Exemple - FaitLeTotal - Nbre d'itération inconnu

Pseudo-code

```
{Cette algorithme fait la somme des nbVal saisit, arrêt à la lesture de -1}

variables   stop : entiers
            valeur, totalValeurs : réels

Début
    stop ← -1
    totalValeurs ← 0
    afficher("Donner une valeur, " ,stop, " pour fini.")
    lire(valeur)

    TANT_QUE valeur <> stop faire
        totalValeurs ← totalValeurs + valeur
        afficher("Donner une autre valeur, " ,stop, " pour fini.")
        lire(valeur) {relance}
    FTQ

    afficher("Le total des valeurs saisies est ", totalValeurs)
Fin
```

##### Exemple - FaitLeTotal - équivalent boucle _POUR_

Pseudo-code

```
{Cette algorithme fait la somme des nbVal saisit, arrêt à la lesture de -1 ou après 5 saisies}

variables   nbVal, stop, max : entiers
            valeur, totalValeurs : réels

Début
    stop ← -1
    max ← 5
    nbVal ← 0
    totalValeurs ← 0
    afficher("Donner une valeur, " ,stop, " pour fini.")
    lire(valeur) {saisie de la 1ère donnée}

    TANT_QUE valeur <> stop ET nbVal < max faire
        totalValeurs ← totalValeurs + valeur
        nbVal ← nbVal + 1
        afficher("Donner une autre valeur, " ,stop, " pour fini.")
        lire(valeur) {relance}
    FTQ

    afficher("Le total des valeurs saisies est ", totalValeurs, " pour, ", nbVal, "  itérations.")
Fin
```

Mais ... 🤔🤔🤔 euh ... Je comprends pas ?

Pourquoi utilise t'on l'opérateur logique ET ? et pas le OU ?

Très belle question ! Tout est dans la logique et la reflexion, je vous explique : Avec les opérateurs OU, nous restons dans la boucle tant qu'une seule des 2 conditions est réalisée. Ici il est donc préférable d'utiliser l'opérateur logique ET.

### Les boucles _REPETER ... TANT QUE (ou Jusqu'à)_ (Do...While)

Fonction : Répéter une suite d'instructions au moins une fois et la répéter tant qu'un condition est remplie. Utilisation : Utilisée lorsque le nombre d'itération est connu.

Pseudo-code

```
REPETER
    <traitement> {suite d'instruction}
TANT_QUE <expression logique booléenne vraie>
```

#### Sa sémantique

Mais que fait finalement cette structure ? 🤔

- Elle traite les instructions
- Elle vérifie que la condition soie vraie
- Elle s'arrète ou continue selon la condition

##### Exemple - FaitLeTotal

Pseudo-code

```
{Cette algorithme fait la somme des nbVal saisit}

variables   nbVal, cpt : entiers
            valeur, totalValeurs : réels

Début

    afficher("Combien de valeurs voulez-vous saisir ?")
    lire(nbVal)
    totalVal ← 0

    REPETER
        afficher("Donner une autre valeur, " ,stop, " pour fini.")
        lire(valeur) {relance}
        totalValeurs ← totalValeurs + valeur
        nbVal ← nbVal + 1
    TANT_QUE valeur <> stop ET nbVal < max

    afficher("Le total des ", nbVal, "valeurs est ", totalValeurs)
Fin
```

### Différences entre les structures

Il existe effectivement plusieurs moyens pour réaliser des boucles d'instructions. Mais ... quelle est la structure la plus optimisée allez-vous me dire ? 🤔

Réponse ..... Il n'y en a pas. En effet, cela dépend essentiellement de ce que vous souhaitez faire.

Récapitulatif :

- Tant que : Cette structure permet de vérifier une condition particulière à chaque début de tour.
- Répéter ... Tant que : Celle-ci, permet de vérifie une condition à la fin de chaque tour et permet donc d'être exécutée au moins une fois.
- Pour : Quant a pour celle-ci, elle a pour particulariter d'être utilisée lorsque nous connaissons à l'avance le nombre d'itération.

### Les boucles _POUR_ (For...To)

Mais _POUR_ quoi ... 🙄. Blague à part, Fonction : Répéter une suite d'instructions un certain nombre de fois. Utilisation : Utilisée lorsque le nombre d'itération est connu.

Pseudo-code

```lolcode
POUR <compteur> de <valeurInitiale> à <valeurFinale> [par pas de  <incrément>] faire
    <traitement> {suite d'instruction}
FPOUR
```

#### Sa sémantique

Mais que fait finalement cette structure ? 🤔

- Elle initialise une variable de boucle (le compteur)
- Elle incrémente cette variable selon la valeur du "pas" indiqué
- Elle vérifie que cette variable ne dépasse pas ce "pas"

/!\ ❗❌⛔ Vous ne devez en aucun cas modifier ce compteur durant le traitement (les instructions)

##### Exemple - FaitLeTotal

Pseudo-code

```
{Cette algorithme fait la somme des nbVal saisit}

variables   nbVal, cpt : entiers
            valeur, totalValeurs : réels

Début
    {initialisation du traitement}
    afficher("Combien de valeurs voulez-vous saisir ?")
    lire(nbVal)
    {initialisation du total à 0 avant cumul}
    totalVal ← 0

    {traitement qui se répète nbVal fois}
    POUR cpt ← 1 à nbVal [faire par pas de 1]
        afficher("Donner une valeur : ")
        lire(valeur)
        totalValeurs ← totalValeurs + valeur {Cumul}
    FPOUR
    {édition des résultats}

    afficher("Le total des ", nbVal, "valeurs est ", totalValeurs)
Fin
```

---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](./Functions.md)