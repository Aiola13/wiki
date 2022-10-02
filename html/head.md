---
title: L'entête
description: 
published: 1
date: 2022-10-02T16:16:54.253Z
tags: 
editor: markdown
dateCreated: 2022-10-02T15:59:41.185Z
---

# L'entête `<head>`

J'en ai parlé plus tôt, l'entête est là pour ajouter des informations à propos de la page.
Que pouvous-nous y trouver ? 🤔

> Je sais pas ... le titre ?

Oui, en effet mais pas que ...

Voici un échantillon de ce que l'on peut retrouver : 

|Balise|Description|
|:----:|:---------:|
|`<title>`| Obligatoire dans toutes pages, elle indique le titre de la page (situez dans le nom de l'onglet)|
|`<link>`| Permet de lier la page avec un document / une page externe comme une feuille de style (CSS)|
|`<meta>`| Représente toutes les méta-données qui ne peuvent pas être utilisées avec les balises suivantes|
|`<style>`| (❌ à ne pas utiliser) Elle permet de mettre du style directement dans votre page|
|`<base>`| Elle spécifie une URL par défaut pour l'ensemble de vos liens |
|`<script>`| Permet d'intégrer un code JavaScript dans la page |
|`<noscript>`| Est exécutée si le navigateur ne supporte pas JavaScript|


## la balise `<title>`

Imaginons que nous créions un site à propos d'un gîtes ou d'une hauberge dans les montagnes. Dans ce cas, quel serait le titre de notre page ?

```html
<!DOCTYPE html>
<html>
	<head>
    <title> L'hauberge de haute montagne dans le Queyras </title>
  </head>
</html>
```

![balise_title.png](/images/html/balise_title.png)

## la balise `<link>`



## la balise `<meta>`

Cette balise peut prendre différents attributs.


|Attribut|Description|Valeur|
|:----:|:---------:|:----:|
|`<charset>`|Spécifie le type d'encodage de caractères à utiliser|ex : UTF-8|
|`<content>`| Vient spécifier deux attributs suivants| texte|
|`<http-equiv>`| Fournit les "entêtes HTTP" |	content-security-policy, content-type, default-style, refresh|
|`<name>`| Indique le nom de la méta |application-name, author, description, generator, keywords, viewport|



```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="Free Web tutorials">
  <meta name="keywords" content="HTML, CSS, JavaScript">
  <meta name="author" content="John Doe">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```