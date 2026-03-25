# 04-02-02 - Gestion de la responsivité et des thèmes avec CSS modernes

## Introduction

Un bon design d’interface utilisateur doit s’adapter à toutes les tailles d’écran et proposer différentes thématiques (ex : mode clair et sombre) pour répondre aux préférences utilisateurs. Cet article explique comment gérer efficacement la **responsivité** et les **thèmes** à l’aide des techniques CSS modernes, en s’appuyant sur Tailwind CSS, Sass, et CSS natif.

---

## 1. Responsivité : principes et mise en œuvre

La responsivité consiste à adapter le rendu et la disposition des éléments selon la taille et la résolution de l’écran.

### 1.1 Méthodes courantes

- **Media queries CSS** : règles conditionnelles typiques en CSS  
- **Classes utilitaires Tailwind responsive** : préfixes `sm:`, `md:`, `lg:`, etc.  
- **Flexbox et Grid** : layout fluides naturellement adaptables  

### 1.2 Exemple avec Tailwind responsive

```html
<div class="text-sm sm:text-base md:text-lg lg:text-xl">
  Texte adaptatif selon la largeur de l'écran
</div>
```

- `text-sm` par défaut  
- `text-base` dès 640px (`sm`)  
- `text-lg` dès 768px (`md`)  
- `text-xl` dès 1024px (`lg`)  

### 1.3 Exemple avec media queries classiques

```scss
.text {
  font-size: 14px;

  @media (min-width: 640px) {
    font-size: 16px;
  }

  @media (min-width: 768px) {
    font-size: 18px;
  }

  @media (min-width: 1024px) {
    font-size: 20px;
  }
}
```

---

## 2. Gestion des thèmes : mode clair et mode sombre

### 2.1 Utilisation de la fonctionnalité CSS `prefers-color-scheme`

Elle détecte la préférence système utilisateur et permet d’appliquer automatiquement un thème.

```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #eee;
  }
}
```

### 2.2 Thèmes avec Tailwind CSS

Tailwind intègre un mode sombre activable via la classe `dark` ou media query.

Dans `tailwind.config.js` :

```js
module.exports = {
  darkMode: 'class', // ou 'media'
}
```

HTML pour activer thème sombre :

```html
<html class="dark">
  <body class="bg-white dark:bg-gray-900 text-black dark:text-white">
    Contenu du site
  </body>
</html>
```

En Tailwind, classes spécifiques au mode sombre :

```html
<button class="bg-gray-300 dark:bg-gray-700 text-black dark:text-white">
  Bouton thème sombre et clair
</button>
```

---

## 3. Gestion dynamique : bascule thème via Javascript

```js
const toggleTheme = () => {
  document.documentElement.classList.toggle('dark')
}
```

HTML :

```html
<button onclick="toggleTheme()">Changer thème</button>
```

---

## 4. Variables CSS (Custom Properties) pour thèmes

### Exemple de déclaration

```css
:root {
  --color-bg: #fff;
  --color-text: #000;
}

.dark {
  --color-bg: #121212;
  --color-text: #eee;
}

body {
  background-color: var(--color-bg);
  color: var(--color-text);
}
```

Avantages :

- Possibilité d’animer la transition entre thèmes  
- Flexibilité extrême dans la gestion des couleurs, espacements, etc.

---

## 5. Diagramme Mermaid : gestion responsivité et thèmes

```mermaid
flowchart TD
  A[Chargement de la page] --> B[Lecture media queries + classes dark]
  B --> C[Application styles responsifs (ex: sm:) et thèmes (dark)]
  C --> D[Détection interaction utilisateur / JS]
  D --> E[Bascule thème mode clair/sombre]
  E --> F[Mise à jour CSS variables / classes]
```

---

## 6. Bonnes pratiques

- Utiliser Tailwind pour simplifier la responsivité via ses classes utilitaires  
- Définir une stratégie de gestion des thèmes (classe `dark` ou media query) adaptée au projet  
- Tester le rendu sur plusieurs appareils et configurations (navigateur, OS)  
- Exploiter les variables CSS pour les thèmes avancés (couleurs, typographie, espacements)  
- Associer des transitions CSS sur variables pour une bascule fluide  

---

## 7. Sources et références

- [MDN - Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)  
- [MDN - prefers-color-scheme](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme)  
- [Tailwind CSS - Dark Mode](https://tailwindcss.com/docs/dark-mode)  
- [CSS-Tricks - CSS Variables for Theming](https://css-tricks.com/theming-with-css-custom-properties/)  
- [Smashing Magazine - Responsiveness with Tailwind](https://www.smashingmagazine.com/2020/02/responsive-design-tailwind-css/)  

---

## Conclusion

Gérer la responsivité et les thèmes via CSS modernes rend le design adaptable et accessible. Entre la puissance des utilitaires Tailwind, la flexibilité des media queries classiques, et la force des variables CSS combinées à la détection système, il est possible d’offrir une expérience fluide, cohérente et personnalisable, adaptée à tous les utilisateurs et devices.