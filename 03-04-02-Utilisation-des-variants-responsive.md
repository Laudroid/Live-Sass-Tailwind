# 03-04-02 - Utilisation des variants responsive et hover dans Tailwind CSS

## Introduction

Tailwind CSS facilite la création d’interfaces interactives et responsives grâce à ses variants intégrées, notamment les **variants responsive** (pour adapter le style selon la taille d’écran) et **hover** (pour gérer les interactions au survol). Cet article explique comment utiliser ces variants, illustré par des exemples concrets et best practices.

---

## 1. Les variants responsive dans Tailwind

Tailwind propose une syntaxe simple pour appliquer des styles à partir d’un breakpoint donné, grâce aux préfixes `sm:`, `md:`, `lg:`, `xl:`, `2xl:`.

### Exemple simple

```html
<button class="bg-blue-500 text-white px-4 py-2
               sm:bg-green-500
               md:bg-yellow-500
               lg:bg-red-500">
  Bouton coloré selon la largeur d’écran
</button>
```

- Par défaut : fond bleu  
- À partir de 640px (`sm`): fond vert  
- À partir de 768px (`md`): fond jaune  
- À partir de 1024px (`lg`): fond rouge

---

## 2. Variant hover

Le variant `hover:` applique un style quand l’utilisateur survole l’élément.

### Exemple

```html
<a href="#" class="text-gray-800 hover:text-blue-600 underline">
  Lien avec changement de couleur au survol
</a>
```

- Texte gris par défaut  
- Bleu au passage de la souris  

---

## 3. Combiner responsive et hover

Vous pouvez chaîner les variants pour un contrôle très précis.

### Exemple : changer la couleur au hover, uniquement à partir d’un breakpoint

```html
<button class="bg-gray-300 text-black px-4 py-2
               hover:bg-gray-400
               md:hover:bg-purple-600 md:hover:text-white">
  Bouton avec hover réactif selon breakpoint
</button>
```

- Sur mobile, hover modifie seulement léger fond  
- À partir de 768px (`md`), hover modifie fond et texte

---

## 4. Utilisation pratique dans un menu responsive

```html
<nav class="space-x-4">
  <a href="#" class="text-gray-600 hover:text-blue-600 md:text-black md:hover:text-purple-700">
    Accueil
  </a>
  <a href="#" class="text-gray-600 hover:text-blue-600 md:text-black md:hover:text-purple-700">
    Services
  </a>
</nav>
```

Sur mobile, le lien est gris avec un hover bleu, sur desktop texte noir avec hover violet.

---

## 5. Ajouter plusieurs variants en même temps

Quelques variantes utiles avec responsive et hover : `focus:`, `active:`, `disabled:`. Exemple :

```html
<button class="bg-green-500 hover:bg-green-600 focus:ring-4 focus:ring-green-300 md:hover:bg-green-700">
  Bouton interactif
</button>
```

---

## 6. Diagramme Mermaid : fonctionnement des variants Tailwind

```mermaid
flowchart TD
  A[Écrire classe utilitaire Tailwind] --> B[Ajouter préfixe variant (ex: hover:, md:)]
  B --> C[Compilateur Tailwind génère CSS ciblant état/breakpoint]
  C --> D[Navigateur applique style dynamique selon état et taille d’écran]
  D --> E[Interface responsive et interactive]
```

---

## 7. Résumé des principales variantes responsive

| Variant      | Description                            | Exemple d’utilisation             |
|--------------|------------------------------------|---------------------------------|
| `sm:`        | Styles à partir de 640px            | `sm:text-lg`                    |
| `md:`        | Styles à partir de 768px            | `md:flex`                      |
| `lg:`        | Styles à partir de 1024px           | `lg:grid-cols-3`                |
| `hover:`     | Styles au survol                    | `hover:bg-gray-200`             |
| `focus:`     | Styles au focus (clavier/souris)   | `focus:ring-2`                  |
| `active:`    | Styles lors de l’activation (clic) | `active:scale-95`               |

---

## 8. Sources et références

- [Tailwind CSS Documentation - Responsive Design](https://tailwindcss.com/docs/responsive-design)  
- [Tailwind CSS Documentation - Hover, Focus, and Other States](https://tailwindcss.com/docs/hover-focus-and-other-states)  
- [CSS-Tricks - Using States in Tailwind](https://css-tricks.com/tailwindcss-states-hover-focus-active/)  
- [MDN Web Docs - CSS Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)  

---

## Conclusion

Les variants responsive et hover dans Tailwind CSS permettent une personnalisation flexible et fine des interfaces. Combinés, ils favorisent la création de sites fluides, adaptatifs et vivants, en conservant une syntaxe claire, intuitive et concise. Maîtriser ces variants est une étape clé pour construire des UI modernes et accessibles.