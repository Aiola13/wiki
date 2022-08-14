---
title: Javascript
description: 
published: 1
date: 2022-08-14T08:19:21.958Z
tags: 
editor: markdown
dateCreated: 2022-08-14T08:19:21.958Z
---

# Cours Javascript

### Qui a conçu Javascript ?

Le concepteur de javascript est 'Brendan Eich' il travaillait pour l'un des premier navigateur <em>NetScape</em>

## Javascript c'est quoi !

> JavaScript est un langage de programmation de scripts principalement employé dans les pages web interactives et à ce titre est une partie essentielle des applications web.

💡 Javascript n'a aucun rapport avec le langage Java, c'est juste pour la fame que javascript s'appel 'Java'script
à la base c'est mocha, puis ensuite livescript pour être maintenant dans la norme <b>ECMAScript</b> connue aussi sous le nom EScript

Voilà la timeline de javascript

![timeline](images/timeline.png)

Pour connaitre les compatibilités avec les navigateurs, il y a ce petit [récap](http://kangax.github.io/compat-table/es5/) qui fait plaisir.

Javascript est un langage interprété
à l'inverse, il existe un autre langage compilé (comme C qui est traduit de 0 et 1 d'un block et ensuite il est exécuté)

Ex du langage interprété Javascript:

Traduit en langage machine à la volé par le moteur javascript V8

![js interprete](./images/langageInterprete.png)

### Un langage côté client

Le javascript est un langage coté client, ça veut dire que mes fichiers JS sont hébergé sur un serveur à coté des fichiers html css.
Quand un utilisateur va accéder à ma page, c'est la que le tout est envoyé.

À l'inverse, PHP, ASP.NET, Ruby on Rails sont des techno coté serveur qui par le suite envoie sur le navigateur.

### Environnement d'éxécution (runtime en anglais)

Savez vous ce que c'est qu'un environnement d'éxécution ?

Si oui donnez moi un exemple 😄

Node.JS est un environnement d'éxécution contruit sur le moteur Javascript V8 de Chrome

Un schéma du runtime environement

![Environnement execution](./images/runtime.png)

Pour faire fonctionner Javascript il faut :

-   Un Runtime Environnement
-   Un Moteur Javascript

💡 Petit parrallele un peu sale, vous avez un moteur ça fait pas avancer..
Il a peut être des particularités il lui faut donc un véhicule, c'est pourquoi il faut l'environnement d'éxécution.

C'est les 2 ensembles qui fait avancer le projet

EX : Dans le navigateur on retrouve le moteur JS ainsi que l'environnement d'éxécution (lui même)

<b>#Question</b>
Est ce que selon vous, tout les navigateurs ont le même moteur Javascript ?

<details>
  <summary>Réponse</summary>
  <b>Non</b> chaque navigateur a son propre moteur, cependant, ils suivent tous la même norme ECMAScript.

![moteur nav](./images/moteur_nav.png)

</details>

Lien utile : [Javascript](https://fr.wikipedia.org/wiki/JavaScript)

### ECMA le début d'une norme

> ECMAScript est un ensemble de normes concernant les langages de programmation de type script et standardisées par Ecma International dans le cadre de la spécification ECMA-262.

Lien utile : [ECMAScript](https://fr.wikipedia.org/wiki/ECMAScript)

ECMAScript c'est du Javascript avec plein de petit outils en plus

## Babel

C'est quoi babel ? C'est simple, comme vous avez pu le voir sur la timeline, javascript grandi vite alors que les navigateurs n'intègre pas forcément toutes les fonctionnalités de javascript.

C'est pourquoi, il existe [babel](https://babeljs.io/) qui permet de transpiler du JS moderne en plus ancien pour la compatibilité des anciens navigateur.

## Backend

Nous pouvons faire l'analogie suivante avec NodeJS.

Dans notre navigateur, nous avons différentes variables disponible comme document, location. C'est la même chose avec NodeJS mais pas du tout les mêmes comme http, fs, OS etc.

![chrome-node](./images/chrome-node.png)

## Les outils

Nous allons travailler avec l'extention Live Server disponible sur VSCode, il faudra aussi télécharger Nodejs (Ça permet de faire du javascript dans le terminal)

## Sondage !

Une extension utile pour travailler en JavaScript avec Visual Studio Code s'appelle **\_**.

-   Navigator
-   Live Server
-   Simul.js
-   JS client

<details>
  <summary>Réponse</summary>
Live Server
</details>

---

JavaScript est standardisé par **\_**.

-   l'ISO
-   Mozilla
-   l'ECMA
-   Apache
<details>
  <summary>Réponse</summary>
l'ECMA
</details>

---

JavaScript est un langage **\_**.

-   déclaratif
-   fonctionnel
-   interprété
-   compilé

<details>
    <summary>Réponse</summary>
interprété
</details>

---

JavaScript est une version de scripting de Java.

-   Vrai
-   Faux

<details>
  <summary>Réponse</summary>

Faux

</details>

---

JavaScript est une technologie **\_**.

-   côté client
-   de balisage
-   compilé
-   machine

  <details>
      <summary>Réponse</summary>

côté client

</details>

### Exemple d'application Full Javascript

<details>
  <summary>Exemples</summary>
  
- Discord
- Slack
- Facebook (Créateur REACT)
- MongoDB (BDD NoSQL) > NoSQL = Not Only SQL

</details>

---

# Nous allons commencer à prendre en main javascript !

-   [Lien vers la prise en main](./PriseEnMainJS/README.md)
-   [Lien vers les tests unitaires](./TestUnitaire/README.md)

# Pour ensuite prendre en main NodeJS !

-   [Lien vers la prise en main](./PriseEnMainNode/README.md)

# Les exercices

-   [Les conditions](./Exercice/README.md)
-   [Les fonctions](./Exercice/README.md)