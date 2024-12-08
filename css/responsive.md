---
title: Responsive Design
description: 
published: true
date: 2024-12-08T10:29:52.913Z
tags: responsive design, responsive
editor: markdown
dateCreated: 2024-12-08T10:29:52.913Z
---

# Qu'est-ce que le Responsive Design

> Les appareils mobiles prennent de plus en plus de place dans nos vies. En conséquence, il est impossible lors de la conception d'un site web de faire fi des multiples dimensions d'écrans qu'ils engendrent. D'où l'importance d'adopter une approche responsive | Adaptive.
{.is-success}

<center><video controls width="500" autoplay>
  <source src="/images/css/css-responsive.mp4" />
</video></center>


> Le terme responsive web design, introduit par Ethan Marcote en 2010, décrit un moyen technique qui ajuste la disposition d’un site Web selon la grandeur de l’écran de l’utilisateur. Avec cette méthode, l’utilisateur peut naviguer à travers le site avec autant de fluidité, peu importe l’appareil utilisé. La disposition du site et le contenu (layout) s’ajusteront donc en conséquence de la largeur du navigateur de l’appareil.
{.is-success}

> **Petite astuce** : Vous pouvez vérifier si un site Web est responsive en rapetissant et en agrandissant manuellement la fenêtre de votre navigateur.
{.is-info}


> Le responsive vous permet ainsi de n’avoir qu’un seul site Web. Le contenu, le design, la navigation et la méthode d’interaction sont ajustés pour fournir une expérience optimale à travers tous les formats de navigateurs.
{.is-success}


> Il n’est donc plus nécessaire de créer deux versions du site, une pour desktop et une pour mobile, comme c’était le cas dans le passé. Nous pouvions notamment reconnaître les sites mobiles avec leur adresse url commençant par « m. », comme dans m.facebook.com.
{.is-warning}

Il existe deux approches qui sont complémentaires :

> **Adaptive**
> L'approche adaptive utilise plusieurs mises en page prédéfinies (ex: mobile, tablette, grand écran, etc.) En fonction de la dimension du navigateur, la mise en page la mieux adaptée est affichée.
{.is-success}


> **Responsive**
> Le contenu est fluide et donc s'ajuste parfaitement à la dimension de l'écran, peu importe cette dernière.
{.is-success}

![3038367-inline-i-1-9-gifs-that-explain-responsive-design-brilliantly-01responsive-vs-adaptive-copy.gif](/images/css/3038367-inline-i-1-9-gifs-that-explain-responsive-design-brilliantly-01responsive-vs-adaptive-copy.gif){.align-center}


> **Responsive vs Adaptive**
> Les sites responsives et adaptives sont similaires, en ce sens où ils s'ajustent à leur environnement (généralement la largeur du navigateur), mais divergent dans leur façon de faire.
De plus, les termes responsive et adaptatif sont souvent mêlés puisqu’en pratique un site Web peut être créé en responsive ET en adaptatif. Plusieurs sites dits responsive ne le sont pas complètement et incluent un mélange des deux techniques.
{.is-success}

# Avant tout

Pour contrôler la manière dont une page web s'affiche, il faut tout d'abord placer cette balise meta dans votre head : 
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

> - **content** : L'attribut content contient les valeurs des informations définies par l'attribut name. Pour name="viewport", cet attribut définit comment la zone d'affichage doit se comporter sur l'appareil.
> 
> - **width=device-width** : Cette instruction indique que la largeur de la zone d'affichage (viewport) doit correspondre à la largeur de l'écran de l'appareil. Cela aide à s'assurer que le contenu de la page est correctement dimensionné et affiché sur des appareils de différentes tailles.
> 
> - **initial-scale=1.0** : Cela définit le niveau de zoom initial lorsque la page est chargée pour la première fois. Une valeur de 1.0 signifie que la page sera affichée à sa taille réelle, sans aucun zoom appliqué.
{.is-info}

# Les Media queries

> Les médias queries permettent d'adapter le contenu d'une page aux caractéristiques de l'appareil de l'utilisateur.
{.is-success}


Par exemple, pour distinguer l'écran d'un cellulaire versus l'écran plus large d'un ordinateur, on pourrait utiliser la media query suivante:

```
@media screen and (min-width: 1000px) { ... }
```

Dans ce cas j'ai:
- Une déclaration de media query @media
- Un type de média screen
- Un opérateur logique and
- Une caractéristique (min-width: 1000px)

Nous pourrions donc définir la couleur rouge comme couleur de fond de notre page:

```
body { background: red; }
```

Et si notre media query est respectée, être un écran et avoir une largeur minimale de 1000px, redéfinir cette couleur à bleu:

```
@media screen and (min-width: 1000px) { 
  body { background: blue; }
}
```

<center><video controls width="500" autoplay>
  <source src="/images/css/media-query.mp4" />
</video></center>

## Types de média

> Le type de média est optionnel. Il correspond au contexte utilisé pour consulter à la page.
{.is-success}

- **all**: couvre tous les types de médias de cette liste (par défaut).
- **screen**: Si quelqu'un consulte la page via un écran 📱/💻.
- **print**: Si quelqu'un décide d'imprimer la page 🖨️.
- **speech**: Si quelqu'un utilise un outil de synthèse vocale 🔊.

> Si le type est omis, les règles s’appliqueront à tous les types d’appareils. Autrement dit, `@media all and (min-width: 1000px) { ... }` et `@media (min-width: 1000px) { ... }` sont équivalent.
{.is-warning}

## Caractéristiques de média

> Les caractéristiques de média s'écrivent toujours entre parenthèses et testent si une condition spécifique est respectée.
{.is-success}

- **min-width/max-width** Basé sur la largeur du viewport (de la fenêtre). Ex: (min-width: 1000px)
- **min-height/max-height** Basé sur la hauteur du viewport (de la fenêtre). Ex: (max-height: 600px)
- **min-aspect-ratio/max-aspect-ratio** Le rapport largeur/hauteur du viewport (de la fenêtre). Ex: (min-aspect-ratio: 16/9)
- **orientation** portrait ou landscape
- **prefers-reduced-motion** no-preference ou reduce Certaines personnes sont sensibles aux animations 🤮. D'où pourquoi de plus en plus d'appareils laissent indiquer à l'utilisateur si il préfère un niveau d'animation normal ou réduit. Ex: (prefers-reduced-motion: reduce)
- **prefers-color-scheme** light ou dark ◻️/◼️. Ex: (prefers-color-scheme: dark)

<center><video controls width="500" autoplay>
  <source src="/images/css/prefer-color-scheme.mp4" />
</video></center>


> Apple Music se base sur une media query afin d’ajuster son thème en fonction de la préférence de l’usager.
{.is-warning}



## Opérateurs logiques
> Permettent d'indiquer le lien entre différentes parties de notre média query.
{.is-success}


- **and** Permet de combiner plusieurs requêtes média en une seule. Pour que la requête soit respectée, il faut que chacune des sous-requêtes soit vraie. ex: screen and (min-width: 1000px) s'appliquera sur tous les écrans de minimum 1000px de large.

- **not** Retourne le résultat opposé d'une requête média. S'il est utilisé dans une liste de requêtes séparées par des virgules, il ne nie que la requête sur laquelle il est appliqué. ex: not (orientation: landscape) s'appliquera sur tous les écrans dont l'orientation est portrait.

- **, (virgule)** Permet de combiner plusieurs requêtes. Chaque requête est traitée séparément. Il suffit qu'une seule de ces requêtes soit respectée pour que les styles s'appliquent. ex: (orientation: landscape), (min-width: 600px) s'appliquera sur les appareils dont l'orientation est landscape et/ou la largeur minimale est de 600px. Donc une tablette en mode portrait serait quand même affectée par les styles même si son orientation ne correspond pas.

EXERCICE

## Breakpoints
Même si notre site est parfaitement responsive, il est parfois souhaitable de faire un changement d'affichage dans certains contextes, afin d'éviter que la dimension de certains éléments devienne un enjeu.

Par exemple, deux sections juxtaposées sur un écran large font du sens. Cependant sur l'écran plus restreint d'un mobile, elles risquent d'être ridiculement coincées. D'où l'utilité à un certain point (Breakpoint) de changer les règles d'affichage via une media query.

<center><video controls width="500" autoplay>
  <source src="/images/css/breakpoints.mp4" />
</video></center>


Ainsi, les sections pourraient passées de demis:

```
.section { width: 50%; }
```
À pleines lorsque la largeur de l'écran est inférieur à 600px:
```
@media (max-width: 600px) { 
  .section { width: 100%; } 
}
```

## Quelques exemple de Media Queries​

```
/** Largeur min 400px AND paysage **/
@media screen and (min-width: 400px) and (orientation: landscape) {
  body {
    color: blue;
  }
}

@media (prefers-color-scheme: dark) {
  /** Thème sombre de votre mobile / ordinateur **/
}

@media (prefers-color-scheme: light) {
  /** Thème clair de votre mobile / ordinateur **/
}
```


## Des « Breakpoints générique » ?
```
// Small devices (landscape phones, 576px and up)
@media (min-width: 576px) {
  /* Votre CSS pour cette résolution */
}

// Medium devices (tablets, 768px and up)
@media (min-width: 768px) {
  /* Votre CSS pour cette résolution */
}

// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
  /* Votre CSS pour cette résolution */
}

// Extra large devices (large desktops, 1200px and up)
@media (min-width: 1200px) {
  /* Votre CSS pour cette résolution */
}
```



## min-width ou max-width ?

> Utilisation de min-width
> La propriété min-width est utilisée pour appliquer des styles à partir d'une certaine largeur d'écran et au-delà. Autrement dit, les styles définis dans une media query avec min-width s'appliquent quand la largeur de l'écran est égale ou supérieure à la valeur spécifiée.
{.is-success}


> Quand l'utiliser :
> 
> **Design mobile-first** : Si vous adoptez une approche mobile-first, vous commencerez par styler la version mobile de votre site. Ensuite, vous utiliserez des media queries avec min-width pour ajouter ou modifier des styles à mesure que l'écran s'agrandit (par exemple, pour les tablettes et les ordinateurs de bureau).
> **Ajouter des éléments ou des fonctionnalités** : Utilisez min-width lorsque vous souhaitez ajouter des éléments ou des fonctionnalités supplémentaires qui n'ont de sens que sur des écrans plus grands, comme des barres latérales ou des mises en page multicolumnes.
{.is-info}

> Utilisation de max-width
> La propriété max-width est utilisée pour appliquer des styles jusqu'à une certaine largeur d'écran. Les styles définis dans une media query avec max-width s'appliquent quand la largeur de l'écran est inférieure ou égale à la valeur spécifiée.
{.is-success}


> Quand l'utiliser :
> 
> **Design desktop-first** : Si vous concevez d'abord pour le bureau (desktop-first), vous pouvez utiliser des media queries avec max-width pour ajuster ou simplifier les styles à mesure que la taille de l'écran diminue, garantissant ainsi que votre site reste utilisable sur les appareils mobiles.
> **Cibler spécifiquement les appareils mobiles** : Utilisez max-width pour cibler les appareils mobiles et appliquer des styles qui améliorent l'expérience utilisateur sur ces petits écrans, comme des tailles de police plus grandes ou des mises en page simplifiées.
{.is-info}


