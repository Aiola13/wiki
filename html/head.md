---
title: L'entête
description: 
published: 1
date: 2022-10-02T15:59:41.185Z
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




## meta

La base