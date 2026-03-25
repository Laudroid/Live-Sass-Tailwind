# 03-02-03 - Gestion des breakpoints dans Tailwind CSS

## Introduction

Les **breakpoints** définissent les points d’arrêt qui permettent de rendre un site web responsive, c’est-à-dire adapté aux différentes tailles d’écrans (mobile, tablette, desktop). Tailwind CSS intègre une gestion des breakpoints simple et puissante, mais permet aussi une personnalisation fine via le fichier `tailwind.config.js`. Cet article explique le fonctionnement des breakpoints dans Tailwind, leur personnalisation, ainsi que la bonne pratique pour les gérer efficacement.

---

## 1. Breakpoints par défaut dans Tailwind CSS

Tailwind propose une configuration par défaut accessible via la clé `screens` dans le thème. Les valeurs correspondantes sont des largeurs min-width (mobile first) :

| Nom    | Min-Width   |
|--------|-------------|
| `sm`   | 640px       |
| `md`   | 768px       |
| `lg`   | 1024px      |
| `xl`   | 1280px      |
| `2xl`  | 1536px      |

Par exemple, la classe `md:bg-red-500` applique un fond rouge dès que la largeur de la fenêtre est égale ou supérieure à 768px.

---

## 2. Exemple d’utilisation des breakpoints

```html
<div class="bg-blue-500 sm:bg-green-500 md:bg-yellow-500 lg:bg-red-500">
  Conteneur adaptant sa couleur en fonction de la largeur d’écran
</div>
```

- Sur mobile <640px : bleu  
- À partir de 640px (sm) : vert  
- À partir de 768px (md) : jaune  
- À partir de 1024px (lg) : rouge

---

## 3. Personnaliser les breakpoints dans `tailwind.config.js`

Vous pouvez modifier les breakpoints, ajouter des points d’arrêt ou changer leurs noms.

### Exemple simple de personnalisation

```js
module.exports = {
  theme: {
    extend: {},
    screens: {
      'sm': '600px',
      'md': '900px',
      'lg': '1200px',
      'xl': '1536px',
      // ajout d’un breakpoint personnalisé
      '2xl': '1800px',
    },
  },
}
```

Les valeurs changent les points d’arrêt utilisés avec les préfixes `sm:`, `md:`, etc.

---

## 4. Définir des breakpoints max (mobile-first inversé)

Par défaut, Tailwind utilise des breakpoints "min-width", mais on peut aussi définir des "max-width" (breakpoints inversés) :

```js
module.exports = {
  theme: {
    screens: {
      'sm-max': {'max': '639px'},
      'md-max': {'max': '767px'},
      'lg-max': {'max': '1023px'},
    }
  }
}
```

Par exemple, la classe `sm-max:bg-red-500` s’applique uniquement en dessous de 640px.

---

## 5. Utilisation combinée (`min` et `max`)

Tailwind permet aussi des breakpoints entre deux valeurs :

```js
module.exports = {
  theme: {
    screens: {
      'tablet': {'min': '640px', 'max': '1023px'},
    }
  }
}
```

Ici `tablet:bg-green-500` sera appliqué entre 640px et 1023px.

---

## 6. Diagramme Mermaid : cycle de gestion des breakpoints dans Tailwind

```mermaid
flowchart TD
  A[Configuration 'screens' dans tailwind.config.js] --> B[Compilation Tailwind]
  B --> C[Génération des classes utilitaires responsives]
  C --> D[Utilisation des classes avec préfixes (ex: md:)]
  D --> E[CSS appliqué dynamique selon largeur d’écran]
```

---

## 7. Bonnes pratiques

- Utilisez la logique **mobile first** avec des breakpoints en `min-width`.  
- Nommer les breakpoints avec cohérence selon votre design system.  
- Evitez trop de breakpoints pour ne pas complexifier la maintenance.  
- Combinez avec les utilitaires Tailwind tels que `hidden`, `block`, `flex` pour masquer/afficher selon la taille.  
- Testez les points d’arrêt sur différents appareils pour garantir une expérience fluide.

---

## 8. Sources et références

- [Tailwind CSS Documentation - Responsive Design](https://tailwindcss.com/docs/responsive-design)  
- [Tailwind CSS Configuration - Screens](https://tailwindcss.com/docs/screens)  
- [CSS-Tricks - Responsive Design with Tailwind](https://css-tricks.com/responsive-design-with-tailwind-css/)  
- [MDN Web Docs - Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)  

---

## Conclusion

La gestion des breakpoints dans Tailwind CSS combine simplicité d’usage et grande personnalisation. Modifier ou étendre les points d’arrêt dans `tailwind.config.js` vous permet d’adapter précisément votre interface à tous types d’écrans, tout en s’appuyant sur une syntaxe claire et intuitive. Utiliser cette puissance garantit un développement responsive fluide et maintenable.