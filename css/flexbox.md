---
title: Flexbox
description: 
published: true
date: 2025-01-13T09:54:45.597Z
tags: responsive, flexbox
editor: markdown
dateCreated: 2024-12-08T10:33:02.533Z
---

# Flexbox

> Le Principe :
> **Un conteneur et des éléments à l'intérieur.**
> ![](https://hedgedoc.privatehomelab.ovh/uploads/e1596f36-50f3-4ac9-bf48-a2a1c31a8b0e.png)
{.is-success}

```html
<div class="container">
    <div class="element-1">Elément 1</div>
    <div class="element-2">Elément 2</div>
    <div class="element-3">Elément 3</div>
</div>
```

```css
.container
{
    display: flex;
}
```


# Propriétés du conteneur parent (container)

- Gérer en colonne et en ligne
- Gérer l'ordre d'affichage
- Gérer le centrage

## flex-direction

> Comme son nom l'indique, la valeur de cette propriété définit la direction qu'auront ses enfants.
{.is-success}

```html
.container {
    flex-direction: row |row-reverse | column | column-reverse;
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/21251d1d-c35f-46b7-95e5-69b86ec6a5f9.svg)

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="raBvNzo" data-pen-title="Flex | flex-direction" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/raBvNzo">
  Flex | flex-direction</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## justify-content

> Un peu comme Word ou Google Doc, flexbox vous permet de justifier votre contenu horizontalement ↔️ afin d'atteindre l'affichage désiré.
{.is-success}

```html
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/ae3126e3-c262-48a7-94eb-163b9f2c4781.svg =300x)


<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="mybLdxO" data-pen-title="Flex | justify-content" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/mybLdxO">
  Flex | justify-content</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

## align-items

> Dans la même lignée que justify-content, mais cette fois à la verticale ↕️.
{.is-success}

```html
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/3f6f663f-9126-418f-b09d-d1ab4c4aef83.svg =300x)



# Propriétés des éléments enfants (items)

## align-self

> La propriété align-self est pratiquement identique à la propriété align-items à la différence qu'elle s'applique sur un élément en particulier, et non le parent, afin de l'aligner de façon différente aux autres.
{.is-success}


```html
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/dbd870e9-300a-40f3-b8b6-e7af84174565.svg)

<p class="codepen" data-height="300" data-default-tab="result" data-slug-hash="EaYLxpB" data-pen-title="Flex | align-self" data-user="aiola" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/aiola/pen/EaYLxpB">
  Flex | align-self</a> by aiola (<a href="https://codepen.io/aiola">@aiola</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## flex-grow

> Propriété appliquée à un enfant donc le parent est en display: flex.
> 
> Cette propriété permet à un élément d'ajuster sa taille (peut importe son width) pour occuper plus d'espace dans le conteneur "flex".
> 
> Elle se définit par un chiffre qui indique combien l'élément peut s'étendre au-delà de sa largeur initiale. Si elle n'est pas spécifiée, elle est de 0, signifiant que l'élément ne s'étendra pas automatiquement.
{.is-success}

```html
.item {
  flex-grow: 2; /* default 0 */
}
```

![flex-grow.svg](/images/css/flex-grow.svg)


## flex-shrink

> Propriété appliquée à un enfant donc le parent est en display: flex.
> 
> Cette propriété détermine comment un élément se réduit pour s'adapter à un espace plus petit dans un conteneur 'flex'. 
> 
> Elle utilise un nombre pour indiquer le taux de réduction par rapport aux autres éléments. En d'autres termes, elle fonctionne de manière opposée à 'flex-grow', permettant à l'élément de diminuer de taille. La valeur par défaut est 1, ce qui signifie que l'élément peut se réduire automatiquement si nécessaire
{.is-success}

```html
.item {
  flex-shrink: 3; /* default 1 */
}
```

![](https://hedgedoc.privatehomelab.ovh/uploads/9a3f23d9-85c2-4563-b135-d0f89b8146a9.png)


## flex-basis

> Propriété appliquée à un enfant donc le parent est en display: flex.
> 
> Cette propriété spécifie la taille initiale d'un élément dans un conteneur 'flex', avant tout flex-grow ou flex-shrink. Elle peut utiliser toutes les unités de mesure CSS pour définir cette dimension de base.
> Dans le contexte d'un parent en flex-direction: row;, c'est en quelque sorte l'équivalent de la propriété width, tandis qu'en flex-direction: column; c'est l'équivalent du height.
{.is-success}


> Si la propriété **flex-basis** est spécifiée sur un élément, la propriété **width** est ignorée.
{.is-warning}

```html
.item {
  flex-basis:  value | auto; /* default auto */
}
```


## order

> Définis la priorité d'affichage d'un enfant dans un parent ayant la propriété display: flex;.
> 
> Par défaut, cette valeur est à 0.
> 
> Par défaut tous les éléments ont la même valeur d'ordre, ils s'affichent donc en fonction de leur ordre d'apparition dans le code, puisqu'aucun élément n'est jugé plus prioritaire qu'un autre. Cependant, si un élément à un ordre inférieur à 0 🔽, il se positionnera avant tous ceux ayant la valeur par défaut de 0. À l'inverse, si un élément à un ordre est supérieur à 0 🔼, il se positionnera après tous ceux ayant la valeur par défaut de 0.
{.is-success}

```html
.item {
  order: 5; /* default is 0 */
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/2273b7a1-104e-466e-b5a2-8b6b5cf1ca6c.svg =500x)

# Propriétés spéciales

## flex-wrap

> Par défaut, flex essaie de tout afficher sur une même ligne.
> 
> Cependant, il est possible de lui spécifier d'afficher sur plus d'une ligne au besoin grâce à la propriété flex-wrap.
{.is-success}

```html
.container {
    flex-wrap: nowrap | wrap | wrap-reverse;
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/2c67878c-ac4a-4d7c-8ab3-a903365f78a2.svg)


## align-content

> Dans la même lignée que align-items, mais au lieu d'aligner les éléments directement, cette propriété aligne les différentes lignes générées par flex-wrap. Autrement dit, pour avoir un effet, cette propriété dépend de la présence de flex-wrap.
> 
{.is-success}

```html
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
  /* Fonctionne seulement si `flex-wrap: wrap` */
}
```
![](https://hedgedoc.privatehomelab.ovh/uploads/c19ab45f-aa47-49f6-9ec2-e253c98f5f38.svg =300x)


## flex
> Ecriture Short hand
> Cette propriété permet de définir le flex-grow, flex-shrink et flex-basis d'un élément en une seule propriété. Il s'agit en fait d'une propriété raccourcis.
{.is-success}

Par exemple, si un élément à les propriétés:
```css
flex-grow: 1;
flex-shrink: 0;
flex-basis: 25%;
```
Il est possible de faire l'équivalent simplement via:

```html
flex: 1 0 25%;
```

## flow

> Ecriture Short hand
> Cette propriété permet de définir le flex-direction et flex-wrap en une seule propriété. Il s'agit d'une propriété raccourcis.
{.is-success}

Par exemple:

```html
flex-direction: row-reverse;
flex-wrap: wrap;
```

est équivalent à
```html
flex-flow: row-reverse wrap;
```

# Pour la fin

## Inspecteur 🕵️‍♂️


<video width="600" autoplay>
 <source src="/images/css/flex-inspecteur.mp4" type="video/mp4">
</video>

