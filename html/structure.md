---
title: La Structure et les balises
description: 
published: 1
date: 2022-10-02T08:47:35.253Z
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



> `foo` (variable métasyntaxiques) est un terme utilisé pour les variables sans importance en programmation lorsque le programmeur est trop paresseux pour penser à un nom réel 😉
{.is-warning}