
# TP Plugin Tailwind : Table triable réutilisable
## Objectifs pédagogiques

* Créer un **plugin Tailwind**
* Concevoir une **feature réutilisable**
* Découpler :

  * UI (Tailwind)
  * logique (JS)
* Manipuler le DOM de manière générique
* Penser comme un **éditeur de librairie**

---

# Contexte

Vous devez créer un plugin nommé :

```bash
tailwind-sortable-table
```

Ce plugin permet d’ajouter un comportement triable à **n’importe quel tableau HTML**.

L’utilisateur peut :

Cliquer sur une colonne pour trier les données :
🔼 ordre croissant
🔽 ordre décroissant
Recliquer pour inverser le tri

---

# Résultat attendu

Un simple HTML comme :

```html
<table class="tw-table-sortable">
  <thead>
    <tr>
      <th data-key="name">Nom</th>
      <th data-key="age">Âge</th>
      <th data-key="city">Ville</th>
    </tr>
  </thead>
  <tbody>
    <!-- contenu -->
  </tbody>
</table>
```

devient automatiquement triable.

---

# Architecture exemple du projet

```bash
project/
|
|-- index.html
|-- main.js
|-- data.js
|
|-- plugins/
|   |-- sortableTable.js
|
|-- tailwind.config.js
```

---

# Base Tailwind

Dans `tailwind.config.js` :

```js id="l8l1ar"
module.exports = {
  content: ["./index.html", "./main.js"],
  theme: {
    extend: {},
  },
  plugins: [
    require('./plugins/sortableTable')
  ],
};
```

---

# Création du plugin Tailwind

`plugins/sortableTable.js`

```js
module.exports = function ({ addComponents }) {
  addComponents({
    '.tw-table-sortable th': {
      cursor: 'pointer',
      position: 'relative',
    },
    '.tw-table-sortable th::after': {
      content: '""',
      marginLeft: '8px',
    },
    '.tw-sort-asc::after': {
      content: '"▲"',
    },
    '.tw-sort-desc::after': {
      content: '"▼"',
    }
  });
};
```

---

# Style via Tailwind

Contraintes :

* Hover sur lignes
* Colonne active stylée
* Responsive

Exemple :

```html
<table class="tw-table-sortable min-w-full border">
```

---

# Logique JS générique

`main.js`

comprenant :

* Initialisation automatique
Par exemple :

```js id="3e2n6m"
document.querySelectorAll('.tw-table-sortable').forEach(initSortableTable);
```

---

* Fonction principale
Par exemple :

```js id="vwnk4d"
function initSortableTable(table) {
  const headers = table.querySelectorAll('th');
  const tbody = table.querySelector('tbody');

  ...
}
```

* Fonction de tri DOM
Par exemple :

```js id="p7ymme"
function sortTable(tbody, key, order) {
  const rows = Array.from(tbody.querySelectorAll('tr'));

 ...
}
```

* Mise à jour UI
Par exemple :

```js id="5j3nsh"
function updateSortUI(headers, activeTh, order) {
  ...
}
```

---

# HTML des données - data.js

```js
const users = [
  { name: "Alice", age: 25, city: "Paris" },
  { name: "Bob", age: 30, city: "Lyon" },
  { name: "Charlie", age: 22, city: "Marseille" },
  { name: "David", age: 35, city: "Toulouse" },
  { name: "Eve", age: 28, city: "Nice" }
];
```

---

# Tests

Vérifier :

* plusieurs tableaux sur la page
* tri indépendant
* types différents (string / number)

---


# Livrables attendus

* Plugin fonctionnel
* Code modulaire
* UI propre avec Tailwind
* Documentation d’utilisation README.md :

```md
# Usage

Ajouter la classe :
.tw-table-sortable
```


