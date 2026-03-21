# 02-03-01 - Contrôles de Flux en Sass : Directives `@if`, `@for`, `@each` et `@while`

## Introduction

Sass étend les capacités du CSS classique en intégrant des directives de contrôle de flux inspirées des langages de programmation. Ces directives permettent d’écrire des styles dynamiques, répétitifs et conditionnels dans vos feuilles de style. Cet article détaille l’usage des directives `@if`, `@for`, `@each` et `@while`, accompagnées d’exemples concrets.

---

## 1. Directive `@if` : Conditions simples et multiples

Le `@if` permet d’appliquer des styles uniquement sous certaines conditions. Il peut être combiné avec `@else if` et `@else`.

### Syntaxe

```scss
@if (condition) {
  // styles
} @else if (autre condition) {
  // styles alternatifs
} @else {
  // styles par défaut
}
```

### Exemple

```scss
$theme: dark;

body {
  @if $theme == light {
    background-color: #fff;
    color: #222;
  } @else if $theme == dark {
    background-color: #222;
    color: #eee;
  } @else {
    background-color: gray;
    color: black;
  }
}
```

---

## 2. Directive `@for` : Boucle pour répéter des styles un nombre donné de fois

La boucle `@for` est utilisée pour exécuter un bloc de styles un nombre fixe de fois, généralement avec un compteur.

### Syntaxe

```scss
@for $i from <start> through <end> {
  // styles utilisant $i
}
```

`through` inclut la valeur finale, `to` l’exclut.

### Exemple : classes de margin

```scss
@for $i from 1 through 5 {
  .m-#{$i} {
    margin: $i * 4px;
  }
}
```

Génère `.m-1` à `.m-5` avec marges correspondantes.

---

## 3. Directive `@each` : Iteration sur les listes ou maps

La directive `@each` parcourt une liste ou une map pour générer des styles avec différentes valeurs.

### Syntaxe

```scss
@each $item in <liste> {
  // styles
}
```

Pour une map :

```scss
@each $key, $value in <map> {
  // styles
}
```

### Exemple : boucler sur couleurs

```scss
$colors: red, green, blue;

@each $color in $colors {
  .text-#{$color} {
    color: $color;
  }
}
```

Génère `.text-red`, `.text-green` et `.text-blue`.

---

## 4. Directive `@while` : Boucle conditionnelle

`@while` répète un bloc tant qu’une condition est vraie. Moins utilisée en Sass, elle offre plus de flexibilité dans certaines itérations.

### Syntaxe

```scss
$counter: 1;

@while $counter <= 3 {
  .w-#{$counter} {
    width: $counter * 20px;
  }
  $counter: $counter + 1;
}
```

---

## 5. Diagramme Mermaid : Contrôle de flux Sass

```mermaid
flowchart TD
  A[Début] --> B[@if]
  A --> C[@for]
  A --> D[@each]
  A --> E[@while]

  B --> F[Exécuter styles si condition vraie]
  C --> G[Répetition basée sur compteur]
  D --> H[Iteration sur liste ou map]
  E --> I[Répetition tant que condition vraie]
```

---

## 6. Avantages pratiques

- Production dynamique de classes (ex : utilitaires, grilles).
- Rédaction de styles variables selon état ou thème.
- Réduction de la redondance grâce aux boucles.
- Maintenabilité accrue par centralisation logique.

---

## 7. Sources et références

- [Sass Official Documentation - Control Directives](https://sass-lang.com/documentation/at-rules/control)  
- [CSS-Tricks - Sass Control Directives](https://css-tricks.com/sass-control-directives/)  
- [Smashing Magazine - Harness Powerful Sass Control Directives](https://www.smashingmagazine.com/2017/04/sass-control-directives-loops/)  
- [MDN - Sass Programming](https://developer.mozilla.org/en-US/docs/Web/CSS/Sass)

---

## Conclusion

Les directives de contrôle de flux `@if`, `@for`, `@each` et `@while` sont des outils incontournables pour exploiter pleinement la puissance de Sass. Elles permettent d’automatiser la génération de styles tout en restant lisibles et maintenables. Maîtriser ces directives est une étape clé dans la production de feuilles de style avancées et évolutives.