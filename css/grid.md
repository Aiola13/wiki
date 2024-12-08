---
title: Grid
description: 
published: true
date: 2024-12-08T10:34:06.859Z
tags: responsive, grid
editor: markdown
dateCreated: 2024-12-08T10:34:06.859Z
---

# Grid

> Tout comme flexbox, la propriété display: grid;, ou sa variante display: inline-grid;, influence l'affichage de ses enfants. Cependant, contrairement à flexbox qui les positionne en fonction d'une seule dimension (x ou y), grid permet de les positionner sur une grille quadrillée en deux dimensions (x & y).
{.is-success}

![template-columns-rows-01.svg](/images/css/template-columns-rows-01.svg =500x)

## grid-template-columns

> Permets de définir indépendamment la taille de chaque colonne d'une grille. Le nombre de colonnes correspond au nombre de valeurs spécifiées.
{.is-success}


Par exemple, trois valeurs produisent trois colonnes:

```css
.container {
  display: grid;
  grid-template-columns: ...  ...  ...;
  /* e.g. 
      1fr 1fr
      minmax(10px, 1fr) 3fr
      repeat(5, 1fr)
      50px auto 100px 1fr
  */
}
```

## grid-template-rows

> Permets de définir indépendamment la taille de chaque ligne d'une grille. Le nombre de lignes correspond au nombre de valeurs spécifiées.
{.is-success}


Par exemple, trois valeurs produisent trois lignes:

```css
.container {
  display: grid;
  grid-template-rows: ...  ...  ...;
  /* e.g. 
      1fr 1fr
      minmax(10px, 1fr) 3fr
      repeat(5, 1fr)
      50px auto 100px 1fr
  */
}
```


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="zYbyOqQ" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/zYbyOqQ">
  Grid | grid-template-*</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## column-gap
> La propriété column-gap permet de définir l'espace entre les colonnes d'une grille.
{.is-success}

<p class="codepen" data-height="300" data-slug-hash="MWxZgRg" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/MWxZgRg">
  Grid | column-gap</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## row-gap
> La propriété row-gap permet de définir l'espace entre les rangées d'une grille.
{.is-success}

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="KKEbKMP" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/KKEbKMP">
  Untitled</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## gap
> La propriété gap permet de définir l'espace entre les colonnes et rangées d'une grille simultanément.
{.is-success}

Cette propriété accepte aussi de recevoir deux valeurs. Le cas échéant, la première correspond à l'espace entre les rangées et la deuxième, à celle entre les colonnes.

Par exemple:

```css
gap: 10px 50px;
```
Génère un espace de 10px entre les rangées ↕️ et de 50px entre les colonnes ↔️.

> Pratiquement toutes les unités, sauf les fr, peuvent êtres utilisées pour les propriété de type gap.
{.is-warning}

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="abMPbmJ" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/abMPbmJ">
  Grid | gap</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## fr
Afin de simplifier la gestion des colonnes et des rangées une nouvelle unité CSS vue le jour. Cette unité, intitulée fr pour fraction, permet de distribuer l'espace disponible de façon relative entre chaque élément ayant une valeur de ce type.

Par exemple, pour avoir trois colonnes identiques, il serait possible de faire:

```css
grid-template-columns: 1fr 1fr 1fr;
```


### Combinaison avec gap
À priori, cette unité peut sembler similaire aux pourcentages (%). Cependant, puisque les fractions basent leurs calculs sur l'espace disponible et non l'espace total de leur parent, ils peuvent-être utiliser avantageusement avec les propriétés de type gap.

Par exemple, si un column-gap: 5px est présent sur des éléments en pourcentages à gauche versus en fractions à droite.

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="Jjzwvgq" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/Jjzwvgq">
  Grid | % vs fr gap</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

### Combinaison avec unités tierce
Lorsqu'une unité tierce est introduite, les pourcentages continuent de se baser sur la dimension totale du parent, peu importe la dimension prise par cette unité, contrairement aux fractions qui se séparent l'espace disponible restant après que l'unité tierce est prise son espace.

Dans les exemples ci-dessous👇, la première colonne à une unité tierce de 50px. À gauche, on remarque que la combinaison avec des pourcentages produit un résultat indésirable, tandis qu'à droite, les fractions séparent également l'espace restant, produisant ainsi un résultat harmonieux.

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="oNVJyNv" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/oNVJyNv">
  Grid | % vs fr</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

### minmax()
Comme son nom l'indique, l'unité minmax() permet de définir une dimension minimale et maximale à une cellule de grille. Cette unité est particulièrement utile afin de créer une mise en page responsive tout en évitant que certains éléments se retrouve trop coincés.

Par exemple, deux grilles identiques avec toutes les cellule d'une largeur de 1fr à l'exception de la 2e cellule verte ayant une valeur de minmax(200px, 1fr).

<video width="600" autoplay>
 <source src="/images/css/grid-minmax.mp4" type="video/mp4">
</video>

## repeat
> Spécifier individuellement chaque colonne ou rangée n'est pas un problème lorsqu'une grille est de dimension relativement modeste. Cependant, lorsqu'une grille grossie, il peut devenir rapidement lassant et mélangeant d'écrire la dimension de chaque colonne ou rangée, surtout si celle-ci est identique.
{.is-success}


Par exemple:
```css
grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
```

Pour palier à cet enjeu, la commande repeat() fut créée.

L'exemple précédent pourrait donc être réécris ainsi:
```css
grid-template-columns: repeat(6, 1fr);
```

### auto-fit & auto-fill
Afin de pouvoir réaliser une grille responsive sans avoir à écrire une multitude de media queries, il est possible d'utiliser les valeurs auto-fit et auto-fill à la place d'un nombre spécifique de colonnes dans un repeat().

Par exemple avec auto-fit,
```css
grid-template-columns: repeat(auto-fit, 150px);
```
Permets d'afficher autant d'éléments sur une rangée qu'il y a d'espace disponible.

<video width="600" autoplay>
 <source src="/images/css/grid-repeat-fit-content.mp4" type="video/mp4">
</video>


La différence entre auto-fit et auto-fill étant la gestion de l'espace vide restant. Avec auto-fit, aucune cellule vide supplémentaire n'est ajoutée dans la grille, même si l'espace le permet, alors qu'avec auto-fill des cellules vides sont créées. Dans la majorité des cas, le résultat sera similaire. Cependant, cette particularité peut parfois s'avérer utile lorsque combinée avec d'autres propriétés de grille.


![grid-repeat-auto-fit-auto-fill.png](/images/css/grid-repeat-auto-fit-auto-fill.png)

En haut ⬆️, repeat(auto-fit, ...) aucune cellule vide de créée.
En bas ⬇️, repeat(auto-fill, ...) 2 cellules vides de créées.

### Combinaison avec d'autres unités
Il est aussi possible de combiner repeat() avec d'autres unités.

Par exemple:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="VwRqdYY" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/VwRqdYY">
  Grid | Repeat</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

---

## grid-column
La propriété grid-column est constituée de deux sous propriétés: grid-column-start et grid-column-end. Ces propriétés permettent de définir où un élément devrait être affiché en fonction d'une ligne verticale ↕️ de départ et de fin dans la grille.

> Afin de bien comprendre et visualiser ces lignes, il est fortement suggéré d’utiliser l’inspecteur.
{.is-info}

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="mdoaKJE" data-user="aiola" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/mdoaKJE">
  CodePen Home Grid - grid-column-start &amp; grid-column-end</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## grid-row
La propriété grid-row est constituée de deux sous propriétés: grid-row-start et grid-row-end. Ces propriétés permettent de définir où un élément devrait être affiché en fonction d'une ligne horizontale ↔️ de départ et de fin dans la grille.

Par exemple:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="Yzgdvqw" data-user="aiola" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/Yzgdvqw">
  Untitled</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

> Les nombres négatifs ne fonctionnent qu’avec les rows explicites.
{.is-info}


Ces propriétés peuvent être combinées en utilisant simplement grid-row.

Par exemple, le code suivant:

```css
grid-row-start: 1;
grid-row-end: 4;
```

Est équivalent à celui-ci:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="RwdEJRR" data-user="aiola" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/RwdEJRR">
  Grid | grid-row</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## span
La valeur span combinée aux propriétés grid-column & grid-row permets d'étendre un élément sur plus d'une d'une colonne ou une rangée dans une grille sans avoir à connaitre le numéro de ligne de début ou de fin.

Par exemple, pour étendre l'élément 2 🔵, il est possible de faire:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="zYbyaBb" data-user="aiola" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/zYbyaBb">
  Grid | Span</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## grid-area
La propriété grid-area permet de définir à la fois la valeur de  grid-row-start, grid-column-start, grid-row-end et grid-column-end.

Par exemple le code suivant:

```css
.no1 {
  grid-row-start: 1;
  grid-column-start: 2;
  grid-row-end: 3;
  grid-column-end: 4;
}
```

Est équivalent à celui-ci:

<p class="codepen" data-height="500" data-default-tab="result" data-slug-hash="Yzgdvyy" data-user="aiola" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/Yzgdvyy">
  Untitled</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## grid-template-areas
La propriété grid-template-areas permets de nommer des zones dans une grille. Cette approche permet de conceptualiser facilement la disposition des éléments.

Par exemple, si l'élément vert 🟢 représente un menu latéral, l'élément bleu 🔵 le contenu principal et l'élément rouge 🔴 un pied de page, il serait possible de les distribuer dans une grille grâce à grid-area:

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="JjzwZYQ" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/JjzwZYQ">
  Untitled</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


> Attention de ne pas mettre une virgule "," entre chaque ligne.
{.is-warning}


> ERREUR FRÉQUENTE
> grid-template-areas prend un "s" à la fin.
{.is-danger}

