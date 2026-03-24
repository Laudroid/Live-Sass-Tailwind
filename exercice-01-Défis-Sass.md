
# Défi 1 — Design tokens dynamiques

### Objectif

Créer un système de design basé sur des variables Sass.

### Contraintes

* Définir :

  * Couleurs (primary, secondary, danger…)
  * Typographie
  * Espacements
* Générer automatiquement :

  * classes `.text-*`
  * classes `.bg-*`

### Indice

Utiliser des maps :

```scss
$colors: (
  primary: #3490dc,
  danger: #e3342f
);
```

### Créer une fonction pour accéder aux couleurs :

```scss
color('primary')
```

---

# Défi 2 — Générateur de grille responsive

### Objectif

Créer un système de grille type Bootstrap en Sass.

### Contraintes

* 12 colonnes
* breakpoints :
  * sm / md / lg
* classes dynamiques :

```css
.col-6
.col-md-4
.col-lg-3
```

---

# Défi 3 — Système de spacing intelligent

### Objectif

Créer un système de spacing cohérent.

### Contraintes

Générer automatiquement :

```css
.mt-1, .mt-2, .mt-3...
.p-1, .px-2, .py-4...
```

### Techniques

* boucles
* maps
* interpolation (`#{} `)

---

# Défi 4 — Composants réutilisables (buttons)

### Objectif

Créer un système de boutons scalable.

### Contraintes

* variantes :

  * primary
  * secondary
  * outline
* tailles :

  * sm / md / lg

### Approche

* mixins
* placeholders (%)
* héritage intelligent

---

# Défi 5 — Théming (light / dark mode)

### Objectif

Gérer plusieurs thèmes avec Sass.

### Contraintes

* 2 thèmes :

  * light
  * dark
* Changement via classe `.theme-dark`

### Approche

* maps imbriquées
* mixins de thème

---

# Défi 6 — Architecture 7-1 complète

### Objectif

Mettre en place une architecture Sass professionnelle.

### Contraintes

Créer :

```
sass/
abstracts/
base/
components/
layout/
pages/
themes/
vendors/
```

### Mission

Refactorer un projet CSS fourni (style-pour-exercice-01.css)
1. Centraliser les variables
2. Supprimer les duplications
3. Créer des mixins
4. Améliorer le responsive
5. Améliorer la sémantique CSS
6. Respecter les contraintes de perf (poids CSS minimum mais le code doit rester lisible - pas de minification)

### Évaluation

* lisibilité
* découpage
* maintenabilité

---

# Défi 7 — Mini framework CSS maison

### Objectif

Créer un micro-framework inspiré de **Tailwind CSS**

### Contraintes

* classes utilitaires :

  * margin / padding
  * flex
  * couleurs
* naming cohérent :

```css
.flex
.justify-center
.items-center
```

### Concepts

* génération massive de classes
* DRY
* performance
