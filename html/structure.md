---
title: La Structure et les balises
description: 
published: 1
date: 2022-10-02T14:18:39.117Z
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

Voici la structure simple :

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

> Les espaces avant certaines lignes permettent de rendre plus lisible le code. C'est ce qu'on appelle **l'indentation**. On met au même niveau les mêmes balises.
{.is-success}


On s'apperçoit que les balises s'ouvrent et se ferment dans un ordre très précis. Les balises se ferment dans le sens inverse de leur ouverture.

```html
<html><body></body></html>
```

### Le doctype

La première ligne est le **DOCTYPE** qui reprèsente la version HTML dans laquelle on écrit notre document. Elle est héritée des anciennes versions de HTML.
```html
<!DOCTYPE html>
```

> Rappelez vous un peu plus haut, dans l'historique, depuis la version 5, le HTML est en évolution continue. 
> Pour la version 1, le DOCTYPE était sous cette forme 
`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">`
> Elle permettait d'indiquer les règles que l'on allait utiliser selon la version utilisée


### La balise `<html>`

Elle englobe tout le contenu HTML de votre page. On l'appelle l'élèment **racine**.

```html
<html>
  
</html>
```

### L'entête `<head>`

Elle permet de définir des informations générales à propos de votre page web (comme l'encodage des caractères, qui a écrit la page, ect ...). Ces informations ne sont pas destinées à être visible à l'écran.

```html
<head>
  
</head>
```


### Le corps `<body>`

C'est ici que se trouve tout le corps du document, ce qui sera affiché à l'écran.

```html
<body>
  
</body>
```

---

> `foo` (variable métasyntaxiques) est un terme utilisé pour les variables sans importance en programmation lorsque le programmeur est trop paresseux pour penser à un nom réel 😉
{.is-warning}