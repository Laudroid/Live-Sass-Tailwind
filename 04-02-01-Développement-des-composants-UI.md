# 04-02-01 - Développement des composants UI

## Introduction

Construire une interface utilisateur (UI) fluide, cohérente et réutilisable nécessite de structurer les éléments visuels sous forme de **composants UI**. Cette approche offre un gain de productivité, facilite la maintenance et améliore la qualité générale du design. Cet article détaille les bonnes pratiques et méthodes modernes pour développer des composants UI efficaces, que ce soit avec CSS pur, Sass, Tailwind CSS, ou des frameworks JS.

---

## 1. Qu’est-ce qu’un composant UI ?

Un composant UI est un bloc visuel indépendant, encapsulant structure HTML, styles CSS et souvent comportement JS. Il doit être réutilisable, paramétrable, et découplé des autres parties.

### Exemples de composants classiques

- Boutons  
- Cartes (cards)  
- Modales (pop-ups)  
- Barre de navigation  
- Formulaires

---

## 2. Principes pour un bon composant UI

- **Isolation** : styles et structure indépendants, pour éviter effets de bord  
- **Réutilisabilité** : adaptable dans différents contextes  
- **Responsivité** : gestion des états et tailles d’écran  
- **Accessibilité** : respect des règles ARIA et navigabilité clavier  
- **Personnalisabilité** : configuration via variables CSS, classes utilitaires ou props (en JS)

---

## 3. Développer un composant bouton avec Tailwind CSS

Tailwind favorise une approche **utilitaire-first** pour construire les composants en chaînant les classes.

```html
<button class="bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded shadow">
  Bouton Tailwind
</button>
```

Si besoin, créer une classe réutilisable avec `@apply` :

```css
.btn-primary {
  @apply bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-4 rounded shadow;
}
```

Puis HTML :

```html
<button class="btn-primary">Bouton réutilisable</button>
```

---

## 4. Composant bouton avec Sass

Avec Sass, on peut structurer et gérer plus facilement la personnalisation par variables :

```scss
$btn-bg: #2563eb;
$btn-bg-hover: #1e40af;
$btn-padding: 0.5rem 1rem;
$btn-border-radius: 0.375rem;

.button {
  background-color: $btn-bg;
  color: white;
  font-weight: 600;
  padding: $btn-padding;
  border-radius: $btn-border-radius;
  box-shadow: 0 2px 4px rgb(0 0 0 / 0.1);
  cursor: pointer;

  &:hover {
    background-color: $btn-bg-hover;
  }
}
```

Usage HTML :

```html
<button class="button">Bouton Sass</button>
```

---

## 5. Gestion des états dans les composants

Pour indiquer feedback utilisateur (hover, focus, disabled), Tailwind fournit des variants et Sass permet de gérer pseudo-classes.

```html
<button class="btn-primary disabled:opacity-50 disabled:cursor-not-allowed" disabled>
  Bouton désactivé
</button>
```

```scss
.button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

---

## 6. Composants plus complexes : carte (Card) en Tailwind

```html
<div class="max-w-sm rounded overflow-hidden shadow-lg">
  <img class="w-full" src="image.jpg" alt="Image description"/>
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">Titre de la carte</div>
    <p class="text-gray-700 text-base">
      Description concise de la carte, expliquant son contenu.
    </p>
  </div>
  <div class="px-6 pt-4 pb-2">
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#tag1</span>
    <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#tag2</span>
  </div>
</div>
```

---

## 7. Diagramme Mermaid : cycle de développement d’un composant UI

```mermaid
flowchart TD
  A[Définir la fonction et usage] --> B[Structure HTML du composant]
  B --> C[Écrire styles CSS/Sass ou classes Tailwind]
  C --> D[Ajouter gestion états (hover, focus, disabled)]
  D --> E[Tester réactivité et accessibilité]
  E --> F[Réutiliser et documenter le composant]
```

---

## 8. Recommandations et bonnes pratiques

- Favoriser des composants petits et bien ciblés  
- Documenter chaque composant dans un style guide ou Storybook  
- Automatiser tests visuels (ex: Percy, Chromatic)  
- Respecter les standards ARIA pour accessibilité  
- Utiliser la composition (inclus composants dans composants plus grands)  

---

## 9. Sources et références

- [Tailwind CSS - Component Extract](https://tailwindcss.com/docs/extracting-components)  
- [Sass Guidelines on Components](https://sass-guidelin.es/#component-architecture)  
- [CSS-Tricks - Building UI Components](https://css-tricks.com/building-modular-css-with-component-based-design-patterns/)  
- [Smashing Magazine - UI Component Design](https://www.smashingmagazine.com/2019/06/ui-components/)  
- [MDN Web Docs - ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)  

---

## Conclusion

Le développement de composants UI structurés, réutilisables et adaptables est la clé pour une interface efficace et pérenne. Que ce soit via Tailwind CSS, Sass ou un mélange des deux, adopter une méthodologie claire assure la qualité et facilite la collaboration entre designers et développeurs.