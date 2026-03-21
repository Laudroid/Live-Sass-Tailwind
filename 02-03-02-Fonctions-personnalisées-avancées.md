# 02-03-02 - Fonctions Personnalisées Avancées en Sass

## Introduction

Au-delà des fonctions de base fournies par Sass, il est possible de créer des fonctions personnalisées avancées pour enrichir et dynamiser vos feuilles de style. Ces fonctions permettent d’effectuer des calculs complexes, manipuler des listes ou maps, ou encore conditionner des valeurs CSS, renforçant la modularité et la maintenabilité du code. Cet article explique les principes de création et d’utilisation des fonctions personnalisées avancées avec des exemples pratiques.

---

## 1. Création d’une fonction personnalisée en Sass

### Syntaxe générale

```scss
@function nom-fonction($param1, $param2, ...) {
  // traitement
  @return valeur;
}
```

La fonction retourne une valeur utilisable dans les déclarations CSS.

---

## 2. Manipulation avancée des listes et maps

Les fonctions personnalisées peuvent manipuler des structures complexes comme les listes et maps, permettant des calculs dynamiques et une adaptation automatique des styles.

### Exemple : Fonction pour extraire une couleur d’une map

```scss
$palette: (
  primary: #3498db,
  secondary: #2ecc71,
  danger: #e74c3c,
);

@function palette-color($key) {
  @return map-get($palette, $key);
}

.button {
  background-color: palette-color(primary);
}
```

---

## 3. Utilisation de conditions et boucles dans les fonctions

Les fonctions peuvent contenir des conditions `@if` et boucles pour générer des valeurs en fonction de paramètres complexes.

### Exemple : Fonction de calcul de contraste pour texte lisible

```scss
@function contrast-color($color) {
  $r: red($color);
  $g: green($color);
  $b: blue($color);
  $brightness: (($r * 299) + ($g * 587) + ($b * 114)) / 1000;

  @if ($brightness > 125) {
    @return #000000;
  } @else {
    @return #ffffff;
  }
}

.button {
  background-color: #3498db;
  color: contrast-color(#3498db);
}
```

Cela assure que le texte est lisible quel que soit le fond.

---

## 4. Exemple avancé : Fonction pour générer un dégradé dynamique

```scss
@function dynamic-gradient($color1, $color2, $direction: to right) {
  @return unquote("linear-gradient(#{$direction}, #{$color1}, #{$color2})");
}

.header {
  background-image: dynamic-gradient(#3498db, #2ecc71);
}
```

---

## 5. Diagramme Mermaid : Fonction personnalisée avancée Sass

```mermaid
flowchart TD
  A[Appel de fonction] --> B[Traitement des paramètres]
  B --> C{Conditions (@if)}
  C -->|Vrai| D[Bloc A]
  C -->|Faux| E[Bloc B]
  D --> F[Boucles possibles (@for, @each)]
  E --> F
  F --> G[@return de la valeur]
  G --> H[Valeur utilisée dans styles]
```

---

## 6. Bonnes pratiques

- Toujours retourner une valeur adaptée à un contexte CSS (couleur, unité, chaîne, etc.).  
- Documenter les paramètres et comportements pour faciliter la réutilisation.  
- Éviter les traitements trop lourds pour ne pas ralentir la compilation.  
- Préférer la réutilisation des fonctions internes Sass (ex : `map-get()`, `red()`) pour garantir robustesse.

---

## 7. Sources et références

- [Sass Official Documentation - Functions](https://sass-lang.com/documentation/at-rules/function)  
- [CSS-Tricks - Building Custom Sass Functions](https://css-tricks.com/building-custom-sass-functions/)  
- [Smashing Magazine - Advanced Sass usage](https://www.smashingmagazine.com/2018/05/sass-architecture-patterns/#advanced-usage)  
- [Sass Guidelines - Functions](https://sass-guidelin.es/#functions)

---

## Conclusion

Les fonctions personnalisées avancées en Sass offrent un moyen puissant d’intégrer des logiques complexes dans vos feuilles de style, tout en améliorant leur modularité et réutilisabilité. En combinant manipulation de maps, conditions et boucles, elles permettent d’adapter finement vos styles aux besoins dynamiques des projets modernes.