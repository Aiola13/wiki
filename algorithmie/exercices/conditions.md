---
title: Exercices : Les conditions
description: 
published: true
date: 2024-12-26T10:10:38.727Z
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


> Année bissextile c'est une année spéciale contenant un jour supplémentaire, soit un total de 366 jours dans une année. Une année est considérée comme une année bissextile si l'année est exactement divisible par 4 mais non divisible par 100. L'année est également une année bissextile si elle est exactement divisible par 400.
{.is-success}


# Exercice 2.9
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

# Exercice 2.10
Ecrire un algorithme qui permet de récupérer les touches tapées par l’utilisateur pour savoir dans quelle direction
déplacer un personnage de jeu. Demander à l’utilisateur de saisir un nombre puis qui en fonction du nombre saisi :
– 6 : affiche ”le personnage va à droite”.
– 4 : affiche ”le personnage va à gauche”.
– 8 : affiche ”le personnage va en haut”.
– 2 : affiche ”le personnage va en bas”.
– dans le cas d’un autre caractère, affiche : ”erreur de saisie, le personnage ne bouge pas”.

# Exercice 2.11

Les élections législatives, en Guignolerie Septentrionale, obéissent à la règle suivante :
- lorsque l'un des candidats obtient plus de 50% des suffrages, il est élu dès le premier tour.
- en cas de deuxième tour, peuvent participer uniquement les candidats ayant obtenu au moins 12,5% des voix au premier tour.

Vous devez écrire un algorithme qui permette la saisie des scores de quatre candidats au premier tour. Cet algorithme traitera ensuite le candidat numéro 1 (et uniquement lui) : il dira s'il est élu, battu, s'il se trouve en ballottage favorable (il participe au second tour en étant arrivé en tête à l'issue du premier tour) ou défavorable (il participe au second tour sans avoir été en tête au premier tour).


<!-- 

4.6

Les élections législatives, en Guignolerie Septentrionale, obéissent à la règle suivante :
● lorsque l'un des candidats obtient plus de 50% des suffrages, il est élu dès le premier
tour.
● en cas de deuxième tour, peuvent participer uniquement les candidats ayant obtenu
au moins 12,5% des voix au premier tour.
Vous devez écrire un algorithme qui permette la saisie des scores de quatre candidats au
premier tour. Cet algorithme traitera ensuite le candidat numéro 1 (et uniquement lui) : il dira
s'il est élu, battu, s'il se trouve en ballottage favorable (il participe au second tour en étant
arrivé en tête à l'issue du premier tour) ou défavorable (il participe au second tour sans avoir
été en tête au premier tour).


4.6 JAWED

var candi1       30
var candi2       25
var candi3        25
var candi4         30

début

afficher "Saisir score du candidat 1"
def candi1

afficher "Saisir score du candidat 2"
def candi2

afficher "Saisir score du candidat 3"
def candi3

afficher "Saisir score du candidat 4"
def candi4

SI candi1 > 50 ALORS 
    afficher "Le candidat 1 est élu dès le premier tour"
Sinon 
    Si candi1 < 12.5 ALORS 
        afficher "Le candidat 1 n'a pas assez de voix pour le 2ème tour."
    Sinon  
        Si candi1 > candi2 ET candi1 > candi3 ET candi1 > candi4
            ALORS afficher "Le candidat 1 est en ballotage favorable"
        Sinon 
            ALORS afficher "Le candidat 1 est en ballotage défavorable"
        finSi
    finSi
finSi




4.6 THOMAS

candidat1, candidat2, candidat3, candidat4 en numérique
position= 4 
ballotagef = True


if candidat1 > candidat2:
    position = position -1
if candidat1 > candidat3:
    position = position -1
if candidat1 > candidat4:
    position = position -1
if position == 1:
    if candidat1 > 50:
        print("Le candidat n°1 est élu dès le premier tour")
if position == 2:
    ballotagef = False
if position > 2:
    print("Le candidat n°1 s'arrête au premier tour")
if ballotagef == True and candidat1 <= 50:
    print("Le premier candidat se retrouve au second tour et se trouve en ballotage favorable")
if ballotagef == False:    
    print("Le premier candidat se retrouve au second tour et se trouve en ballotage défavorable")    
    


4.6  Loïc 

Variables A, B, C, D en numérique
Variables C1, C2, C3, C4 en Booléan
Debut
Ecrire "Entrez les scores des quatre prétendants :"
Lire A, B, C, D
C1 ← A > 50
C2 ← B > 50 ou C > 50 ou D > 50
C3 ← A >= B et A >= C et A >= D
C4 ← A >= 12.5
Si C1 ALORS
    Ecrire "Elu au premier tour"
Sinon Si C2  ou Non(C4) Alors 
    Ecrire "Battu, éliminé, sorti !!!"
Sinon Si C3 Alors
    Ecrire "Ballotage Favorable"
Sinon 
    Ecrire "Ballotage défavorable"
FinSi
Fin






4.7
Une compagnie d'assurance automobile propose à ses clients quatre familles de tarifs
identifiables par une couleur, du moins au plus onéreux : tarifs bleu, vert, orange et rouge. Le
tarif dépend de la situation du conducteur :
● un conducteur de moins de 25 ans et titulaire du permis depuis moins de deux ans,
se voit attribuer le tarif rouge, si toutefois il n'a jamais été responsable d'accident.
Sinon, la compagnie refuse de l'assurer.
● un conducteur de moins de 25 ans et titulaire du permis depuis plus de deux ans, ou
de plus de 25 ans mais titulaire du permis depuis moins de deux ans a le droit au tarif
orange s'il n'a jamais provoqué d'accident, au tarif rouge pour un accident, sinon il est
refusé.
● un conducteur de plus de 25 ans titulaire du permis depuis plus de deux ans
bénéficie du tarif vert s'il n'est à l'origine d'aucun accident et du tarif orange pour un
accident, du tarif rouge pour deux accidents, et refusé au-delà
● De plus, pour encourager la fidélité des clients acceptés, la compagnie propose un
contrat de la couleur immédiatement la plus avantageuse s'il est entré dans la maison
depuis plus de cinq ans. Ainsi, s'il satisfait à cette exigence, un client normalement
"vert" devient "bleu", un client normalement "orange" devient "vert", et le "rouge"
devient orange.
Écrire l'algorithme permettant de saisir les données nécessaires (sans contrôle de saisie) et
de traiter ce problème. Avant de se lancer à corps perdu dans cet exercice, on pourra
réfléchir un peu et s'apercevoir qu'il est plus simple qu'il n'en a l'air (cela s'appelle faire une
analyse !)

4.7 YANNIS
Var age en numérique
Var durée de permis en numérique
Var nb accidents en numérique
Var durée d'assurance en numérique
var Situation 

Début 
Ecrire "Indiquez votre âge"
Lire age
Ecrire "Depuis quand avez vous le permis ?"
Lire durée de permis
Ecrire "Avez vous déjà eu un accident ?"
Lire nb accidents

Si age < 25 ans ET durée de permis < 2 ans 
Alors
 Situation ← tarif rouge"
Si nb accident >= 1 ans
Alors
Situation ← "Refusé"

Si age < 25 ans ET durée de permis > 2 ans OU age > 25 ans ET durée de permis < 2 ans 
Alors 
Situation ← " Tarif orange"
Si nb d'accident = 1
Alors 
Situation ← "tarif rouge"
Sinon
Situation ← " Refusé"

Si age > 25 ans ET durée de permis > 2 ans
Alors
Situation ← "tarif vert"
Si nb d'accident = 1
Alors
Situation ← " tarif orange"
Si nb d'accident = 2
Alors
Situation ← "tarif rouge"
Sinon
Situation ← "refusé"
FinSi

Si durée d'assurance > 5 ans  Alors
    Si Situation = "tarif vert" Alors
        Situation ← tarif bleu
    Sinon Si Situation = "tarif orange" Alors
        Situation ← tarif vert
    Sinon Si Situation = "tarif rouge" Alors
        Situation ← tarif orange
FinSi

Ecrire "Voici votre situation : ", Situation
Fin

4.7 THOMAS

score, age, apermis, nb_accident,assure en numérique

print("Quel est votre age ?")
read age
print("Depuis combien d'année avez vous le permis ?")
read apermis
print("combien avez vous eu d'accident ?")
read nb_accident


if age > 25:
    score += 1
if Apermis >= 2:
    score += 1
If assure > 5:
    score += 1
score -= nb_accident

If score == 3:
    print("Vous bénéficiez du tarif Bleu.")
If score == 2:
    print("Vous bénéficiez du tarif Vert.")
If score == 1:
    print("Vous bénéficiez du tarif Orange.")
If score == 0:
    print("Vous bénéficiez du tarif Rouge.")
If score < 0:
    ("Vous ne pouvez pas être assuré")


Exercice 4.8
Écrivez un algorithme qui, après avoir demandé un numéro de jour, de mois et d'année à
l'utilisateur, renvoie s'il s'agit ou non d'une date valide.
Cet exercice est certes d’un manque d’originalité affligeant, mais après tout, en algorithmique
comme ailleurs, il faut connaître ses classiques ! Et quand on a fait cela une fois dans sa vie,
on apprécie pleinement l’existence d’un type numérique « date » dans certains langages…).
Il n'est sans doute pas inutile de rappeler rapidement que le mois de février compte 28 jours,
sauf si l’année est bissextile, auquel cas il en compte 29. L’année est bissextile si elle est
divisible par quatre. Toutefois, les années divisibles par 100 ne sont pas bissextiles, mais les
années divisibles par 400 le sont. Ouf !
Un dernier petit détail : vous ne savez pas, pour l’instant, exprimer correctement en
pseudo-code l’idée qu’un nombre A est divisible par un nombre B. Aussi, vous vous
contenterez d’écrire en bons télégraphistes que A divisible par B se dit « A dp B ».

4.8 SABRIN

Variable: Validité

Ecrire "veuillez insérer le jour"²
Lire "J"
Ecrire "veuillez insérer le mois"
Lire "M"
Ecrire "veuillez insérer l'année"
Lire "A"

Si M < 1 ou M > 12 Alors
    Ecrire ''Date Invalide"
Sinonsi M = 2
    Si A dp 400 Alors
        Si J < 1 ou J > 29 Alors
            Ecrire "Date Invalide"
        Sinon
            Ecrire "Date Valide"
        FinSi
    SinonSi A dp 100 ALors
        Si J < 1 ou J > 28 Alors
            Ecrire "Date Invalide"
        Sinon
            Ecrire "Date Val ide"
        FinSi
    SinonSi A dp 4 Alors
        Si J < 1 ou J > 29 Alors
            Ecrire "Date Invalide"
        Sinon
            Ecrire "Date Valide"
        FinSi
    Sinon
        Si J < 1 ou J > 28 Alors
            Ecrire "Date invalide"
        Sinon
            Ecrire "Date Valide"
        FiniSi
    FinSi
SinonSi M = 4 pi M = 6 ou M = 9 ou M = 11 Alors
    Si J < 1 ou J > 30 Alors
        Ecure "Date Invalide"
    Sinon 
        Ecrire "Date Valide"
    FinSi
Sinon
    Si J < 1 ou J > 31 Alors
        Ecrire "Date Invalide"
    SInon   
        Ecire "Date Valide"
    FinSi
FinSi
 


Exercice 5.1
Écrire un algorithme qui demande à l’utilisateur un nombre compris entre 1 et 3 jusqu’à ce
que la réponse convienne.


Variable Rep en caractere 
Debut 
Rep ← 0
Ecrire "Donnez un chiffre compris entre 1 et 3"
TantQue Rep < 1 ou Rep > 3 Alors
    Lire Rep
    Si Rep < 1 ou Rep > 3 Alors
        Ecrire "Vous devez donner un chiffre compris entre 1 et 3"
    FinSi
FinTant Que
Fin


Exercice 5.2
Écrire un algorithme qui demande un nombre compris entre 10 et 20, jusqu’à ce que la
réponse convienne. En cas de réponse supérieure à 20, on fera apparaître un message : «
Plus petit ! », et inversement, « Plus grand ! » si le nombre est inférieur à 10.

Jawed 5.2

var number en Nombre 
var bonneRep = Si number >= 10 ET number =< 20

début 

    number = -1
    afficher "Ecrivez un nombre entre 10 et 20" 
    def number
    tantQue number != -1
        si Non(bonneRep)
            Si number > 20 alors afficher "Plus petit"
            Sinon alors afficher "Plus grand"
        sinon alors afficher "Bien joué"
    finTantQue

fin


Variable number en entier
Debut
number ← 0
Ecrire "Entre un nombre entre 10 et 20"
TantQue number < 10 ou number > 20
    Lire number
    Si number < 10 alors
        Ecrire "Plus grand!"
    Sinon Si number > 20 Alors
        Ecrire "Plus petit!"
    FinSi
finTantQue
Fin



Exercice 5.3
Écrire un algorithme qui demande un nombre de départ, et qui ensuite affiche les dix
nombres suivants. Par exemple, si l'utilisateur entre le nombre 17, le programme affichera
les nombres de 18 à 27.

valeur en numérique
additioneur en numérique

Début
    Afficher "entrer une valeur"
    saisir valeur  
    additioneur ← valeur + 10    
    Tant que valeur != additioneur Faire
        valeur ← valeur + 1
        Afficher "valeur"
    Fin tant que
Fin

5.3

var number en numérique
var compteur en numérique (i)
Début
    Ecrire "Entrez une valeur"
    Lire number 
    i ← 0
    TantQue i < 10 
        i ← i + 1
        Ecrire number + i
    finTantQue
Fin



5.4 Réécrire l'algorithme précédent, en utilisant cette fois l'instruction Pour
var number en numérique
var compteur en numérique
Début
    Ecrire "Entrez une valeur"
    Lire number
    Pour compteur ← 1 à 10
        Ecrire number + i
    FinPour
Fin






5.5 Ecrire un algorithme qui demande un nombre de départ, et qui ensuite écrit la table de
multiplication de ce nombre, présentée comme suit (cas où l'utilisateur entre le nombre 7)


Var nombre en numérique
Var compteur en numérique
Début 
    Ecrire "Entrez un nombre"
    Lire nombre 
    Pour compteur ← 1 à  10   
        Ecrire "nombre*compteur =", nombre*compteur
    nombre suivant
Fin


5.6
Écrire un algorithme qui demande un nombre de départ, et qui calcule la somme des entiers
jusqu’à ce nombre. Par exemple, si l’on entre 5, le programme doit calculer

number en Entier
compter en Entiern
sum en Entier

début
    sum ← 0 
    afficher "entrer un nombre pour faire la suite"
    saisir number 
    pour compter ← 1 à number faire
        sum ← sum + compteur
        afficher sum
    FinPour
    Ecrire "La somme est : ", sum
FIN

Var nombre en numérique
Var compteur en numérique
var somme en numérique

Début 
    somme ← 0
    Ecrire "Entrez un nombre"
    Lire nombre 
    Pour compteur <-- 1 à nombre    
        somme ← somme + compteur
    Ecrire "La somme est : ", sum
Fin

5.7 Écrire un algorithme qui demande un nombre de départ, et qui calcule sa factorielle.
NB : la factorielle de 8, notée 8 !, vaut 1 x 2 x 3 x 4 x 5 x 6 x 7 x 8

somme ← 1
ecrire "entrez un nombre"
lire nombre   
Pour compteur ← 2à  nombre           
    somme ← somme * compteur  
FinPour
Ecrire "La factorielle est", somme
Fin

-->
