---
title: Sass, Scss or Less ?
description: 
published: true
date: 2025-02-03T08:47:42.467Z
tags: 
editor: markdown
dateCreated: 2025-02-03T07:17:19.991Z
---

# SASS: Syntactically Awesome Style Sheets

SASS, ou **Syntactically Awesome Style Sheets**, est un préprocesseur CSS. Il s'agit d'un langage qui permet de générer du code CSS. Mais pourquoi ne pas écrire directement du CSS ? Pour bénéficier des avantages que procure SASS ! Parmi ces avantages, on trouve :

- Les **variables**
- Le **nesting** (imbrication)
- Les **partials**
- Les **mixins**
- Et bien d'autres !

## Utilisation

L'usage de SASS est très répandu. Plusieurs sites et librairies d'envergure l'utilisent, notamment :

- **Bootstrap**
- **AirBnB**
- **SidLee**
- Etc.

## Syntaxes

SASS offre deux syntaxes de base différentes : `.sass` et `.scss`.

### SASS

La syntaxe **SASS** fut la syntaxe originale de SASS (d'où son nom). Elle se base principalement sur l'indentation du code ainsi que les sauts de ligne. Afin de la différencier de SASS le préprocesseur, cette syntaxe est souvent surnommée la "**syntaxe indentée**".

Ici, nous nous concentrerons surtout sur la syntaxe `.scss`. Nous n'élaborerons donc pas trop sur la syntaxe `.sass`.

### SCSS

La syntaxe **SCSS** est la plus récente et la plus répandue. Elle ressemble au CSS traditionnel, ce qui la rend facile à apprendre pour quiconque comprend les bases du langage CSS, tout en incorporant les avantages de la syntaxe `.sass`. Cette syntaxe est souvent surnommée "**Sassy CSS**".

## CodePen

Pour écrire du SCSS dans **CodePen**, il suffit de cliquer sur la roue dentelée ⚙️ à gauche du titre de l'onglet CSS et de choisir l'option de préprocesseur **SCSS**.

<!--🤫  
Tous les exercices que je conçois dans le cadre de ce cours sont d’abord écrits en SCSS et sont ensuite convertis en CSS.-->

## Compilation

Il existe plusieurs solutions pour compiler du code SASS en CSS afin que les navigateurs puissent l'interpréter :

1. **La plus simple** : **SassMeister**, qui permet de convertir en ligne du code. Cependant, cette solution implique de recopier manuellement 🖐 son code à chaque fois que l'on souhaite le compiler.

2. **La solution intermédiaire** : Utiliser un logiciel qui se charge de la compilation. Par exemple, **Prepros** permet de surveiller votre code SASS et de le compiler à chaque changement.

3. **La solution idéale**, mais légèrement plus complexe : Utiliser un **bundler**. Par exemple : **webpack**, **Rollup**, **Vite**, etc. Ces bundlers peuvent être installés directement dans un projet, simplifiant et uniformisant ainsi le travail entre les membres d'une équipe.

C'est cette dernière qui sera plus interessante à utiliser. Vous verrez ces outils comme Vite, plus tard, avec les framework Javascript.
<!-- Dans le cadre de ce cours, nous verrons comment compiler du SASS via **Vite**.-->



# Les variables SCSS

Les variables SCSS sont simples à utiliser. Il suffit d'attribuer un nom à une variable et de le préfixer avec le symbole `$`. Ensuite, le délimiteur `:` permet de séparer le nom de la variable de sa valeur.

Par exemple, pour définir une variable `costume` contenant la couleur rouge 🔴 :

```scss
$costume: red;
```

## Contexte (scope)
Une variable SCSS définie à l'extérieur d'un sélecteur CSS est considérée comme globale. Autrement dit, elle peut être utilisée partout dans son fichier. En revanche, les variables SCSS définies à l'intérieur d'un sélecteur CSS sont considérées comme locales et ne peuvent être accédées qu'à l'intérieur des accolades {} qui les encapsulent.

Par exemple :

```scss
$costume: red; // Variable globale

.spider-man {
  $logo: blue; // Variable locale
  
  background-color: $costume; // ✅
  color: $logo; // ✅
}

.deadpool {
  background-color: $costume; // ✅
  color: $logo; // ❌
}
```

## Écraser une variable
En donnant un contexte plus spécifique, il est possible d'écraser la valeur d'une variable.

Par exemple :

```scss
$costume: red; // 🔴

.spider-man {
  background-color: $costume; // 🔴
}

.green-goblin {
  $costume: green; // 🟢

  background-color: $costume; // 🟢
}
```

Dans cet exemple, la variable $costume a la valeur red dans le contexte global. Ainsi, si un personnage n'écrase pas cette variable, son costume sera automatiquement rouge 🔴. Tandis que le sélecteur .green-goblin redéfinit la valeur de cette variable dans son propre contexte à green 🟢.

Même si un personnage est défini après .green-goblin, s’il utilise la variable $costume, celle-ci retournera red, car la valeur green n’est retournée qu’à l’intérieur du contexte du sélecteur .green-goblin.

## Variables CSS
À première vue, les variables CSS et les variables SCSS peuvent sembler interchangeables. Cependant, elles diffèrent sur certains points importants.

Variables SCSS : Ce sont des variables dites compilées. Une fois converties en CSS, il n'y a plus aucune trace de la variable en soi, car elle est remplacée par sa valeur.

Variables CSS : Elles existent en tout temps, ce qui permet de modifier une valeur directement dans le navigateur au besoin.

Par exemple, si vous inspectez la balise <html> de cette page, vous remarquerez que plusieurs variables CSS sont définies. Vous pouvez remplacer leurs valeurs et voir les changements s'appliquer immédiatement dans la page. En revanche, aucune trace de variable SCSS n'est visible.

## Pourquoi avoir inventé les variables SCSS ?
Il faut faire un saut dans le passé pour bien comprendre. Les variables Sass ont été inventées en 2006. À cette époque, c'était une grande avancée dans le monde du CSS, car, aussi étrange que cela puisse paraître, les variables CSS natives n'existaient pas encore. Ces dernières ont été introduites quelques années plus tard, et leur implémentation dans les différents navigateurs a nécessité encore quelques années de patience. Ainsi, leur utilisation réelle n'a commencé qu'environ 10 ans après les variables Sass.
  
  
# La règle `@extend`

La règle `@extend` permet de définir une classe ayant les mêmes règles de style qu'une autre classe spécifiquement.

## Exemple de classe de message

Par exemple, une classe de message pourrait ressembler à ceci :

```scss
.msg {
  border-radius: 10px;
  padding: 10px;
  background-color: blue;
}
  ```
Si d'autres types de messages doivent ensuite être créés et qu'ils doivent partager les mêmes styles de base que .msg, il serait possible d'étendre cette classe plutôt que de réécrire à chaque fois le même code.

Exemple d'extension de classe
```scss
.msg-error {
  @extend .msg;
  background-color: red;
}

.msg-success {
  @extend .msg;
  background-color: green;
}
  ```
Ce qui générerait le code suivant :

```scss
.msg, .msg-success, .msg-error {
  border-radius: 10px;
  padding: 10px;
  background-color: blue;
}

.msg-error {
  background-color: red;
}

.msg-success {
  background-color: green;
}
  ```
Les trois messages partageraient donc le même border-radius et le même padding tandis que la couleur de fond serait écrasée pour chaque variation.

## Placeholder
Parfois, il est pratique de définir des règles qui peuvent être étendues sans pour autant que ces règles existent en soi, d'où l'utilité des %placeholder. Ces règles commencent avec un % et ne génèrent aucun code à moins d'être étendues.

Exemple avec placeholder
L'exemple précédent pourrait être réécrit avec un placeholder afin d'éviter que la couleur de fond bleue soit écrasée par les variantes de messages :

```scss
%msg {
  border-radius: 10px;
  padding: 10px;
}

.msg {
  @extend %msg;
  background-color: blue;
}

.msg-error {
  @extend %msg;
  background-color: red;
}

.msg-success {
  @extend %msg;
  background-color: green;
}
  ```
Ce qui générerait le code suivant :

```scss
.msg-success, .msg-error, .msg {
  border-radius: 10px;
  padding: 10px;
}

.msg { background-color: blue; }
.msg-error { background-color: red; }
.msg-success { background-color: green; }
  ```
Les placeholders sont particulièrement utiles pour les règles de styles que nous utilisons régulièrement.

Exemple pratique : centrer des éléments
Par exemple, je sais que je centre régulièrement des éléments via transform. Plutôt que de taper à chaque fois :

```scss
.element {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
  ```
On peut donc se créer un placeholder similaire à ceci :

```scss
%centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
  ```
Et on l'utilisera sur des éléments que l'on désire centrer ainsi :

```scss
.element {
  @extend %centered;
}
```
  

# Les Fonctions

Les `@functions` permettent de gérer des opérations complexes, de manipuler un ou plusieurs paramètres et de retourner des résultats précis. Elles sont généralement utilisées afin de produire des valeurs.

Par exemple, une variable d'espacement `$gutter: 26px;` pourrait nécessitée d'être divisée en deux lorsque deux éléments l'utilisant se suivent afin d'éviter que l'espacement soit doublé. Pour palier à ce problème, il serait possible de se créer une fonction divisant cette valeur:

```scss
@function half($num) {
 @return $num / 2;
}
```

Ainsi il serait possible d'écrire:

```scss
.card {
  padding: half($gutter); // 13px
}
```

Remarquez `@return` qui indique quel élément dans la fonction doit être retourné.

Pourquoi ne pas utiliser `calc()` plutôt? La fonction `calc()` est interprété dans le navigateur donc demande quelques fractions de seconde de plus à votre navigateur afin d'afficher, tandis que tout calcul effectué directement via SASS est effectué au moment de la compilation et donc n'engendre aucun délais pour l'usager.
  
Imbrication
===========

Par défaut le langage CSS ne permet pas de faire d'imbrications, communément appelé *"nesting"* en anglais. Il est donc parfois nécessaire de répéter un sélecteur plusieurs fois dans son code CSS.

Heureusement, Sass apporte cette fonctionnalité à CSS, ce qui permet d'accélérer l'écriture de feuilles de styles et de simplifier leur lecture.

Imbrications de base[](https://smnarnold.com/cours/sass/imbrication#Imbrications%20de%20base)
---------------------------------------------------------------------------------------------

Afin d'éviter de répéter le sélecteur `.list` à plusieurs reprises, il est possible d'écrire en SCSS:

```scss
.list {
  position: relative;

  .item { display: inline-block; }

  .link { color: blue; }
}
```

Ce qui générera le code CSS suivant ⏬

```scss
.list { position: relative; }

.list .item { display: inline-block; }

.list .link { color: blue; }
```

### Niveaux d'imbrications

Vous pouvez imbriquer des éléments ainsi à l'infini. Dans l'exemple précédent, nous avions un seul niveau d'imbrication.

Voici maintenant un exemple contenant deux niveaux d'imbrications:

```scss
.list {
  position: relative;

  .item {
    display: inline-block;

    .link { color: blue; }
  }
}
```

Ce qui générera le code CSS suivant ⏬

```scss
.list { position: relative; }

.list .item { display: inline-block; }

.list .item .link { color: blue; } // 👈 ici
```

Évitez d'abusez des imbrications. Plus de trois niveaux d'imbrication est généralement considéré comme étant une mauvaise pratique et rendra votre code difficile à déboguer.

-   [nesting](https://sass-lang.com/documentation/style-rules/declarations#nesting)

Sélecteurs avancés[](https://smnarnold.com/cours/sass/imbrication#S%C3%A9lecteurs%20avanc%C3%A9s)
-------------------------------------------------------------------------------------------------

Les imbrications sont compatible avec tous les [sélecteurs CSS avancés](https://smnarnold.com/cours/css/selecteurs-avances).

Par exemple:

```scss
.list {
  > .item { display: inline-block; }

  + .logo { display: none; }
}
```

Générera le code CSS suivant ⏬

```scss
.list > .item { display: inline-block; }

.list + .logo { display: none; }
```

-   [selector combinator](https://sass-lang.com/documentation/style-rules#selector-combinators)

Sélecteur de parent[](https://smnarnold.com/cours/sass/imbrication#S%C3%A9lecteur%20de%20parent)
------------------------------------------------------------------------------------------------

Le sélecteur de parent `&` est un sélecteur spécial inventé par Sass permettant de faire référence au sélecteur parent courant.

Tout sélecteur imbriqué dans un autre se fait convertir par défaut en enfant du premier.

Autrement dit:

```scss
.selecteur1 {
  .selecteur2 { ... }
}
```

Générera le code CSS suivant ⏬

```scss
 .selecteur1 .selecteur2 { ... }
```

Remarquez l'espace entre les deux sélecteurs indiquant que `.selecteur2` est enfant de `.sélecteur1`.

Cependant grâce au sélecteur parent il est possible de contourner ce comportement. Voyons quelques usages de ce sélecteur.

### Pseudo-classes

Les imbrications Sass sont compatibles avec les [pseudo-classes](https://smnarnold.com/cours/css/pseudo-classes) lorsqu'un sélecteur parent est utilisé.

Par exemple:

```scss
.btn {
  background: blue;

  &:hover { background: lightblue; }
}
```

Générera le code CSS suivant ⏬

```scss
.btn { background: blue; }

.btn:hover { background: lightblue; }
```

Remarquez l'utilisation du sélecteur parent `&`. Celui-ci permet de faire une référence au sélecteur courant, en l'occurence `.btn`et de lui rabouter directement, sans espace, la pseudo-classe `:hover`.

### Pseudo-éléments

Les imbrications Sass sont compatibles avec les [pseudo-éléments](https://smnarnold.com/cours/css/pseudo-elements) lorsqu'un sélecteur parent est utilisé.

Par exemple:

```scss
.btn {
  background: blue;

  &::before { content: "🔘"; }
}
```

Générera le code CSS suivant ⏬

```scss
.btn { background: blue; }

.btn::before { content: "🔘"; }
```

### Renversé

Parfois, il souhaitable de spécifier que notre élément devrait avoir une apparence différente dans un certain contexte.

Par exemple, lorsqu'un bouton est affiché dans un menu, sa couleur de fond pourrait devoir être grise plutôt que bleue. Le sélecteur parent permet de couvrir ce cas de figure sans avoir à quitter le contexte du sélecteur du bouton en utilisant ce sélecteur comme suffix.

```scss
.btn {
  .menu & { background: grey; }
}
```

Générera le code CSS suivant ⏬

```scss
.menu .btn { background: grey; }
```
  
  
  
# La Nomenclature BEM

Le choix d'une nomenclature est un aspect important d'un projet. Il permet d'écrire un CSS de qualité et d'anticiper comment les autres membres de son équipe écriront leurs classes CSS. Ceci résulte en un code uniforme, facilement maintenable plutôt qu'une agglomération de différents styles de codes écrits par différents développeurs.

BEM est l'une des nomenclatures CSS les plus répandues. Elle permet d'éviter de nombreux effets secondaires *(side effects)* tout en améliorant la performance des feuilles de styles.

Lorsqu'un projet grossi, il n'est pas rare d'attribuer le même nom de classe à différentes composantes. Par exemple, imaginons que vous créez une composante de héros et que vous souhaitez afficher son titre en italique.

Vous écrivez donc le code suivant:

```scss
.title {
  font-style: italic;
}
```

Cependant, si vous ou l'un de vos collègues travaille éventuellement sur une composante d'article et qu'à l'intérieur de celle-ci se trouve aussi un titre, il est probable que son réflexe ou le votre soit de le cibler via la classe `.title` à nouveau, ce qui engendra des effets secondaires indésirables. Le titre de l'article héritera du style italique initialement attribué au titre du héros et tous les nouveaux styles appliqués au titre de l'article s'appliqueront aussi au titre du héros 🤮.

Heureusement, BEM permet d'éviter cette confusion!

Origine du nom[](https://smnarnold.com/cours/sass/nomenclature-bem#Origine%20du%20nom)
--------------------------------------------------------------------------------------

Le nom BEM provient de l'abréviation de: Blocs, Éléments et Modificateurs qui sont les trois piliers de cette nomenclature.

Blocs[](https://smnarnold.com/cours/sass/nomenclature-bem#Blocs)
----------------------------------------------------------------

Les blocs sont des noms de classes représentant des composantes de base pouvant être facilement identifiable dans une page par leur simple nom.

Par exemple: `.site-header`, `.hero`, `.article`, etc. sont tous des composantes que nous devrions être à même de reconnaitre.

```scss
<div class="hero">
  ...
</div>
```

Éléments[](https://smnarnold.com/cours/sass/nomenclature-bem#%C3%89l%C3%A9ments)
--------------------------------------------------------------------------------

Les éléments sont des sous-composantes avec des noms génériques ayant un lien étroit avec leur bloc.

Par exemple: `title`, `list`, `item`, etc. sont des noms de composantes génériques qui pourraient être présents dans chacun des blocs précédemment mentionnés. Styliser une de ces composantes à partir de son nom générique, par exemple `.title`, dans chacune de ces composantes entrainerait assurément des effets secondaires indésirables entre chacune d'entre elles.

Heureusement, avec la nomenclature BEM ces effets secondaires seraient évités, puisque la classe d'un élément est constituée du nom de son bloc suivi de deux barres de soulignement `__` et du nom de l'élément.

Par exemple:

```scss
<div class="hero">
  <h2 class="hero__title">Titre</h2>
</div>
```

Modificateurs[](https://smnarnold.com/cours/sass/nomenclature-bem#Modificateurs)
--------------------------------------------------------------------------------

Les modificateurs sont des drapeaux, ou en anglais: un *"flags"*, permettant de changer le comportement ou l'apparence d'un bloc ou d'un élément.

Par exemple: `active`, `disabled`, `big`, etc.

Avec BEM, un modificateur est séparé de son bloc ou de son élément à l'aide de deux tirets `--`.

Par exemple:

```scss
<div class="hero">
  <h2 class="hero__title hero__title--big">Titre</h2>
</div>
```

Remarquez qu'un modificateur ne remplace pas une classe de base, mais est ajouté en surplus.

Imbrication[](https://smnarnold.com/cours/sass/nomenclature-bem#Imbrication)
----------------------------------------------------------------------------

Il faut faire attention avec l'imbrication de BEM. Personne ne veut travailler dans un code où des classes CSS ressemblent à:

🚫

```scss
.homepage__hero__wrapper__title { ... }
```

Il est donc important de bien savoir diviser ses blocs. Dans l'exemple précédent, il serait logique d'avoir un bloc de départ `.homepage` ainsi qu'un bloc `.hero`.

Le bloc `.hero` pourrait avoir différents niveaux d'éléments, mais il n'est pas nécessaire de nommer chacun d'entre eux.

Par exemple, il n'est pas nécessaire dans son nom de classe de spécifier que le titre se trouve dans le wrapper. Ainsi une division de la sorte permettrait d'obtenir un code plus lisible:

👌

```scss
.hero__wrapper { ... }
.hero__title { ... }
```

🛠 Outil\
[Get BEM](http://getbem.com/)

Site de référence consacré uniquement à la nomenclature BEM.

![](https://smnarnold.com/img/asset/YXNzZXRzL3Rvb2xzL2dldC1iZW0uanBn?w=185&s=cd09ad37eacabc471df2c060b5b944d6)>

SASS[](https://smnarnold.com/cours/sass/nomenclature-bem#SASS)
--------------------------------------------------------------

### Nesting

Il peut être fastidieux de toujours répéter le même bloc au début de chaque nom de classe. D'où pourquoi la nomenclature BEM se marie si bien avec SASS. En tirant profit de l'imbrication (*nesting)* de SASS, il est possible de définir un bloc de ensuite ses éléments à l'intérieur de lui, sans jamais se répéter!

Par exemple:

```scss
.hero {
  &__wrapper { width: 100%; }
  &__title { font-style: italic; }
}
```

Ce qui générera le code CSS suivant:

```scss
.hero__wrapper { width: 100%; }
.hero__title { font-style: italic; }
```

### Modificateurs

Les modificateurs sont faciles à écrire à l'aide de `@extend`.

Par exemple

```scss
.hero__title {
  font-style: italic;

  &--big {
    @extend .hero__title;
    font-size: 40px;
  }
}
```

Ce qui générera le code CSS suivant:

```scss
.hero__title, .hero__title--big {
  font-style: italic;
}
.hero__title--big {
  font-size: 40px;
}
```

### Découpage

Il est fortement suggéré que chaque élément assez important pour être un bloc est son propre fichier SASS distinct.

Par exemple, le fichier *hero.scss* ne contiendrait qu'un seul bloc, soit `.hero`. Le fichier *site-header.scss* ne contiendrait que le bloc `.site-header` et ainsi de suite.