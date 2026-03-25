# 03-04-01 - Techniques pour rendre un site responsive avec Tailwind CSS

## Introduction

Créer un site **responsive** signifie qu’il s’adapte parfaitement à toutes les tailles d’écrans, du mobile au desktop. Tailwind CSS propose des outils puissants pour bâtir rapidement une interface fluide, maintenable et optimisée pour le responsive design. Cet article détaille les méthodes et meilleures pratiques à utiliser avec Tailwind CSS afin d’obtenir une UI responsive efficace.

---

## 1. Mobile-first avec Tailwind CSS

Tailwind est conçu selon une approche **mobile-first**. Par défaut, les classes s’appliquent à toutes les résolutions, puis vous ajoutez des variantes avec des breakpoints (`sm:`, `md:`, `lg:`...) pour les écrans plus larges.

```html
<div class="p-4 bg-blue-500 sm:bg-green-500 md:bg-red-500">
  Couleur différente selon la taille d’écran
</div>
```

- Par défaut (tous écrans) : bleu  
- À partir de 640px (`sm`) : vert  
- À partir de 768px (`md`) : rouge

---

## 2. Utiliser les breakpoints Tailwind

Les breakpoints par défaut Tailwind :

| Breakpoint | Min-Width (px) |
|------------|----------------|
| `sm`       | 640            |
| `md`       | 768            |
| `lg`       | 1024           |
| `xl`       | 1280           |
| `2xl`      | 1536           |

Cela traduit en classes utilisables :

```html
<div class="text-base md:text-lg lg:text-xl">
  Texte qui grossit sur écrans plus larges
</div>
```

---

## 3. Flexbox et Grid pour la mise en page responsive

### Flexbox

Facilite la disposition des éléments en ligne ou colonne, tout en restant adaptable.

```html
<div class="flex flex-col md:flex-row gap-4">
  <div class="flex-1 bg-gray-300 p-4">Colonne 1</div>
  <div class="flex-1 bg-gray-400 p-4">Colonne 2</div>
</div>
```

Sur mobile, éléments en colonne, sur tablette+ en rangée.

### Grid

Pour des layouts plus complexes, la grille Tailwind s'adapte aussi :

```html
<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
  <div class="bg-gray-200 p-4">Item 1</div>
  <div class="bg-gray-300 p-4">Item 2</div>
  <div class="bg-gray-400 p-4">Item 3</div>
</div>
```

---

## 4. Gestion des espacements et tailles

Utiliser des unités relatives comme `w-full`, `max-w-*`, `min-w-*` ou `aspect-ratio` pour garder des proportions responsives.

```html
<img src="image.jpg" alt="exemple" class="w-full max-w-md mx-auto" />
```

---

## 5. Cacher et afficher selon la taille d’écran

Avec les classes `hidden`, `block`, `inline-block` combinées aux breakpoints :

```html
<div class="block md:hidden">Visible uniquement sur mobile</div>
<div class="hidden md:block">Visible uniquement tablette et plus</div>
```

---

## 6. Exemple complet : header responsive

```html
<header class="flex flex-col md:flex-row items-center justify-between p-4 bg-gray-100">
  <h1 class="text-xl font-bold mb-2 md:mb-0">Logo</h1>
  <nav class="space-x-4">
    <a href="#" class="text-gray-700 hover:text-blue-600">Accueil</a>
    <a href="#" class="text-gray-700 hover:text-blue-600">À propos</a>
    <a href="#" class="text-gray-700 hover:text-blue-600">Contact</a>
  </nav>
</header>
```

Sur mobile, menu sous le logo (en colonne), sur desktop disposition ligne.

---

## 7. Diagramme Mermaid : processus responsive avec Tailwind CSS

```mermaid
flowchart TD
  A[Composer structure HTML] --> B[Appliquer classes utilitaires Tailwind]
  B --> C[Ajouter variantes breakpoints (ex: md:, lg:)]
  C --> D[Utiliser flexbox/grid pour layout adaptatif]
  D --> E[Cacher/afficher contenu avec responsive utilities]
  E --> F[Test multi-écrans, itérer ajustements]
```

---

## 8. Sources et références

- [Tailwind CSS Documentation - Responsive Design](https://tailwindcss.com/docs/responsive-design)  
- [MDN Web Docs - Responsive Design Basics](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)  
- [CSS-Tricks - Tailwind Flexbox and Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)  
- [Smashing Magazine - Responsive UI with Tailwind](https://www.smashingmagazine.com/2021/02/tailwindcss-build-responsive-ui/)  

---

## Conclusion

Avec Tailwind CSS, rendre un site responsive repose sur l’utilisation cohérente des classes utilitaires associées aux breakpoints, combinée aux layouts flexibles via Flexbox ou Grid. La simplicité de la syntaxe et la richesse des outils facilitent la création d’interfaces fluides, adaptées à tous types d’écrans, tout en assurant une maintenance efficace et claire.