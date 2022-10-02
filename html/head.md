---
title: L'entête
description: 
published: 1
date: 2022-10-02T16:40:49.248Z
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

Cette balise a deux attributs très intéressant : `href` et `rel`.
- `href` :  Contient le nom et l'emplacement du lien du document à insérer 
- `rel` :  Contient le type de document à insérer

```html
<link rel="stylesheet" href="styles.css">
<link rel="icon" href="favicon.ico">
```

## la balise `<meta>`

|Attribut|Description|Valeur|
|:----:|:---------:|:----:|
|`<charset>`|Spécifie le type d'encodage de caractères à utiliser|ex : UTF-8|
|`<content>`| Vient spécifier deux attributs suivants| texte|
|`<http-equiv>`| Fournit les "entêtes HTTP" |	content-security-policy, content-type, default-style, refresh|
|`<name>`| Indique le nom de la méta |application-name, author, description, generator, keywords, viewport|



```html
<head>
  <meta charset="UTF-8"> <!-- Encodage des caractères, pour éviter les erreurs d'accents, de caractères spéciaux, etc ... -->
  <meta name="description" content="Le site de moi, pour apprendre  ... "> <!-- C'est ce qui apparaît dans votre recherche google sous le nom du site -->
  <meta name="keywords" content="HTML, Cours, Greta"> <!-- Etait utilisé par les moteurs de recherche pour connaître les thématiques de votre page -->
  <meta name="author" content="John Doe"> <!-- Précise l'auteur de la page -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Permet d'ajuster la largeur de la page par rapport à l'écran et définie le niveau de zoom initial -->
</head>
```


## les balisscript `<style>` et `<script>`

Ces deux balises servent respectivement à insérer directement dans le document du CSS et du Javascript. Nous reviendrons dessus plus tard.

```html
<script>
	document.getElementById("demo").innerHTML = "Hello JavaScript!";
</script>
<style>
  h1 {color:red;}
  p {color:blue;}
</style>
```


---

> Voici deux liens vers des documentations pour approfondir ce sujet : 
> https://developer.mozilla.org/fr/docs/Web/HTML/Element
> https://www.w3schools.com/tags/tag_head.asp
{.is-success}
