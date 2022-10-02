---
title: La Structure et les balises
description: 
published: 1
date: 2022-10-02T08:56:35.358Z
tags: 
editor: markdown
dateCreated: 2022-10-02T08:47:35.253Z
---

# La structure et les balises

## La Syntaxe

> Mais c'est quoi ça ??? `<foo>`, mais je vais jamais me retenir de tout ...

Pas de panique, c'est vrai il ne suffit pas simplement d'écrire du texte pour que ça fonctionne. On est pas magicien. Il faut bien donner des instructions à l'ordinateur. Cela passe par les **balises**.

Les balises sont entourées de **chevrons** (Oui, comme dans stargate !), les symboles `<` et `>`.
Elle permettent d'indiqué la nature de ce qu'elles encadrent.

Il existe 2 types de balises : 
- Les balises en paires (ouvrante et fermante)
- Les balises orphelines (auto-fermante)

### Balises en paires 

```html
<foo> 	Mon Texte 	</foo>
  | 									 |
  |                    |
  v                    v
Balise ouvrante       Balise fermante
```
On utilise ce type de balise lorsque l'on délimite un élèment, comme un paragraphe, un titre, ect ...

### Balises orphelines

```html
<foo />
```
Ce type de balise est utilisé généralement pour insérer un élément à un endroit donné, tel qu'un image.

## Les attributs

On peut comparer les attributs, aux options de la balise. Elles sont là pour compléter et donner des informations supplémentaires.

```html
<foo attribut="valeur"> 	Mon Texte 	</foo>
```

## Structure générale d'une page HTML5

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    
  </body>
</html>
```

> Les espaces avant certaines lignes permettent de rendre plus lisible le code. C'est ce qu'on appelle **l'indentation**.
{.is-success}



> `foo` (variable métasyntaxiques) est un terme utilisé pour les variables sans importance en programmation lorsque le programmeur est trop paresseux pour penser à un nom réel 😉
{.is-warning}