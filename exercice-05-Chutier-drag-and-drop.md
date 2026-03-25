
# TP — Plugin Tailwind : Chutier Drag & Drop réutilisable

# Objectifs pédagogiques

* Créer un plugin avec **Tailwind CSS**
* Implémenter un **drag & drop natif HTML5**
* Concevoir un composant **réutilisable et configurable**
* Gérer les interactions DOM complexes
* Structurer du JS modulaire (logique “plugin”)

---

# Contexte

Vous devez créer un plugin Tailwind :

```bash
tailwind-dnd-chutier
```

Il permet de générer une interface avec :

* une zone gauche → **chutier (liste de produits)**
* une zone droite → **zones de dépôt (slots)**


# Résultat attendu

## UI cible

```
+-------------------+--------------------------+
|     CHUTIER       |        ZONES             |
|-------------------|--------------------------|
| Produit A         | [  Zone 1  ]             |
| Produit B         | [  Zone 2  ]             |
| Produit C         | [  Zone 3  ]             |
+-------------------+--------------------------+
```

Drag & Drop :

* gauche → droite
* droite → gauche
* entre zones droites (bonus)

---

# Architecture proposée du projet

```bash
project/
|
|-- index.html
|-- main.js
|-- data.js
|
|-- plugins/
|   |-- dndChutier.js
|
|-- tailwind.config.js
```

---

# HTML générique

```html
<div class="tw-dnd-container">

  <div class="tw-chutier" id="chutier"></div>

  <div class="tw-dropzones">
    <div class="tw-dropzone" data-zone="1"></div>
    <div class="tw-dropzone" data-zone="2"></div>
    <div class="tw-dropzone" data-zone="3"></div>
  </div>

</div>
```

---

# Données

`data.js`

```js
const products = [
  { id: 1, name: "Produit A" },
  { id: 2, name: "Produit B" },
  { id: 3, name: "Produit C" },
  { id: 4, name: "Produit D" },
  { id: 5, name: "Produit E" }
];
```

---

# Initialisation

```js
initDndChutier({
  chutierSelector: '#chutier',
  dropzoneSelector: '.tw-dropzone',
  data: products
});
```

---

# Fonction principale

```js
function initDndChutier(config) {
  const { chutierSelector, dropzoneSelector, data } = config;

  const chutier = document.querySelector(chutierSelector);
  const dropzones = document.querySelectorAll(dropzoneSelector);

  renderChutier(chutier, data);
  enableDragAndDrop(chutier, dropzones);
}
```

---

# Rendering

```js
function renderChutier(container, data) {
  /*TODO*/
}
```

---

# Drag & Drop

## Logique globale

* `dragstart`
* `dragover`
* `drop`
* `dragend`


```js
function enableDragAndDrop(chutier, dropzones) {
 /*TODO*/
}
```
---

# Plugin Tailwind (UI)

`plugins/dndChutier.js`

```js
module.exports = function ({ addComponents }) {
  addComponents({
    '.tw-dnd-container': {
      display: 'flex',
      gap: '2rem',
    },

    //UI des différentes zones
    /*
    .tw-chutier: {

    }

     etc...
     */
  });
};
```

---

# Contraintes obligatoires

* Réutilisable sur plusieurs pages
* Aucune dépendance externe
* Pas de CSS custom hors Tailwind plugin

---

# Bonus — Sauvegarde état

```js
localStorage.setItem(...)
```

---

# Livrables

* Plugin fonctionnel
* Code JS modulaire
* UI propre avec Tailwind
* README :

```md
## Usage

Ajouter :
.tw-dnd-container
```

