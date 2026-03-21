# 01-02-03 - Exemple simple d'utilisation de Sass

## Introduction

Sass est un préprocesseur CSS qui facilite la gestion et la maintenance des styles grâce à des fonctionnalités avancées comme les variables, l’imbrication, les mixins, etc. Cet article présente un exemple simple d’utilisation de Sass, illustrant son fonctionnement, la syntaxe et la compilation vers CSS classique.

---

## 1. Structure de base d’un fichier Sass

Voici un fichier Sass minimaliste nommé `styles.scss` qui utilise plusieurs fonctionnalités clés :

```scss
// Variables pour les couleurs et les espacements
$primary-color: #3490dc;
$secondary-color: #ff6347;
$padding: 1rem;
$border-radius: 5px;

// Mixin pour les boutons
@mixin button-styles($bg-color) {
  background-color: $bg-color;
  color: white;
  padding: $padding;
  border: none;
  border-radius: $border-radius;
  cursor: pointer;

  &:hover {
    opacity: 0.8;
  }
}

// Styles du header avec nesting
header {
  background-color: $primary-color;
  padding: $padding;

  h1 {
    color: white;
    font-size: 2rem;
  }

  nav {
    a {
      color: white;
      margin-right: 1rem;
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}

// Application du mixin pour différents boutons
.button-primary {
  @include button-styles($primary-color);
}

.button-secondary {
  @include button-styles($secondary-color);
}
```

---

## 2. Compilation en CSS

Après compilation avec un outil comme Dart Sass, ce fichier générera le CSS suivant :

```css
header {
  background-color: #3490dc;
  padding: 1rem;
}
header h1 {
  color: white;
  font-size: 2rem;
}
header nav a {
  color: white;
  margin-right: 1rem;
  text-decoration: none;
}
header nav a:hover {
  text-decoration: underline;
}
.button-primary {
  background-color: #3490dc;
  color: white;
  padding: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button-primary:hover {
  opacity: 0.8;
}
.button-secondary {
  background-color: #ff6347;
  color: white;
  padding: 1rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.button-secondary:hover {
  opacity: 0.8;
}
```

---

## 3. Pourquoi utiliser Sass ici ?

- **Variables** : Centralisent les couleurs et espacements, facilitant la modification à un seul endroit.
- **Mixin** : Évite la duplication des styles de bouton tout en permettant des variantes grâce aux paramètres.
- **Nesting** : Simplifie la lecture et la structure, rappelant l’organisation HTML.

---

## 4. Diagramme Mermaid illustrant le workflow Sass

```mermaid
flowchart TD
    A[Sass (styles.scss)] --> B[Variables, Mixins, Nesting]
    B --> C[Outil de compilation (ex: Dart Sass)]
    C --> D[Feuille CSS finale]
    D --> E[Application dans le navigateur]
```

---

## 5. Conclusion

Cet exemple simple montre comment Sass peut transformer un CSS répétitif et peu organisé en un code plus compact, modulaire et facile à maintenir. L’utilisation de ses fonctionnalités de base accélère le développement, réduit les erreurs, et facilite les mises à jour.

---

## Sources et références

- [Sass Official Guide – Using Sass](https://sass-lang.com/guide)
- [Dart Sass – The primary implementation of Sass](https://sass-lang.com/dart-sass)
- [Sass Basics – CSS-Tricks](https://css-tricks.com/sass-basics/)
- [Sass mixins and variables examples – MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Sass)

---

Cet article fournit une mise en pratique claire et opérationnelle de Sass, ouvrant la voie à son utilisation dans des projets plus complexes.