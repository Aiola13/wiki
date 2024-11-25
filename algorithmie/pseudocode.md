---
title: Un Pseudo-code
description: 
published: 1
date: 2024-11-25T00:56:44.237Z
tags: code, pseudo, pseudocode
editor: markdown
dateCreated: 2023-01-16T00:24:34.269Z
---

# Un Pseudo-Code

> Il n'existe aucun **standard** ni de **normalisation** pour l'écriture d'un algorithme en pseudo-code. Mais voici quelques **conventions** et bonnes pratiques 😉.
{.is-warning}

## Structure générale

```
ALGORITHME
    <partie déclarations>
    Début
        <partie instructions>
    Fin
```

## Conventions et règles d'écriture

### Conventions

Nous utiliserons les conventions suivantes :

- __mots clés__
- *identifiants*
- <élément à développer>
- {élément facultatif}
- ... pour indiquer que la structure peut être répétée

### Identifiants

> En programmation, un identifiant (ou identificateur) est un mot choisi (par le programmeur), qui peut désigner : 
> - une constante
> - une variable
> - une procédure
> - une fonction
> - l’algorithme principal
> 
> ‎
{.is-success}

> Les noms d’identifiants ne peuvent contenir que des caractères compris dans les intervalles suivants :
> - ‘a’..’z’
> - ‘A’..’Z’  
> - ‘0’..’9′
> - On peut également utiliser le caractère \_ (souligné/underscore)
> 
> ‎
{.is-warning}


> Voici la bible de la construction d'un identifiant (Et oui, il y toujours des règles à respecter 😁) :
> - il ne doit pas commencer par un chiffre.
> - il doit être déclaré avant d'être utilisé
> - il ne doit pas ressembler à un mot-clé existant
> - il doit être explicite
> 
> ‎
{.is-success}

Exemple, un identifiant contenant la largeur d'une image : 

<center>
  
|Bonne pratique|Mauvaise pratique|
|:------------:|:----------------:
|largeur_image|li|
|largeurImage|image|
  
</center>


### Mots-Clés

> Les mots clés sont des mots utilisés pour construire les algorithmes, ils sont préféfinis. 
{.is-warning}

Liste des principaux mots clés du langage et leurs équivalent en anglais:

<div style="display:flex; justify-content:space-around ">

|Français|Anglais|
|:------:|:-----:|
|ALGORITHME|ALGORITHM|
|PROCÉDURE|PROCEDURE|
|CONSTANTES|CONSTANTS|
|VARIABLES|VARIABLES|
|DÉBUT|BEGIN|
|FIN|END|
|FONCTION|ALGORITHM|  
 
  
|Français|Anglais|
|:------:|:-----:|
|SI|IF|
|ALORS|THEN|
|SINON|ELSE|
|POUR|FOR|
|TANT QUE|WHILE|
|RÉPÉTER|REPEAT|
|JUSQU’À|UNTIL|
|SELON|CASE|
  
  
|Français|Anglais|
|:------:|:-----:|
|BOOLÉEN|BOOLEAN|
|ENTIER|INTEGER|
|RÉEL|FLOAT|
|CARACTÈRE|STRING|
|OU|OR|
|ET|AND|
|ECRIRE ou AFFICHER|PRINT or DISPLAY|
|LIRE|READ|
  
</div>

### Les symboles spéciaux

Voici la liste des caractères spéciaux utilisés en Pseudo-Code :

<center>

| ← | ^ | . | , | : | `{ }` | [ ] | `<=` | >= | <> | = | + | - | \* | / | () | \` | 
|---|---|---|---|---|-----|-----|----|----|----|---|---|---|----|--|---|----|

</center>

### Les commentaires

Pour aider à la compréhension, il faut ajouter des commentaires. Les blocs de commentaires seront délimités par les caractères // :

`// un commentaire`

---

# Prêt pour la prochaine partie ? 😉 [C'est par ici](/algorithmie/data)