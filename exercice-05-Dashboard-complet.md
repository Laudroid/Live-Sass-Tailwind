

# TP - Dashboard modulaire avec plugins Tailwind

## Contexte

Vous travaillez dans une équipe frontend chargée de développer un **dashboard modulaire réutilisable** basé sur **Tailwind CSS**.

L’objectif est de concevoir un système permettant d’intégrer dynamiquement plusieurs widgets dans une interface flexible.

## Objectif

Développer un **dashboard dynamique basé sur une architecture plugin**, capable d’intégrer plusieurs widgets :

* Widget statistiques (`stats`)
* Widget tableau triable (`table`)
* Widget drag & drop (`chutier`)

---

## Contraintes techniques

Vous devez respecter les points suivants :

### 1. Architecture modulaire obligatoire

* système de **registry de widgets**
* chaque widget dans un fichier séparé
* aucune logique “hardcodée” dans le dashboard

### 2. Plugin Tailwind

Créer un plugin Tailwind pour :

* `.tw-dashboard`
* `.tw-widget`
* `.tw-widget-header`

### 3. Dashboard dynamique

Le dashboard doit être généré à partir d’une configuration JS :

```js
const config = [
  { type: 'stats', data: [...] },
  { type: 'table', data: [...] },
  { type: 'chutier', data: [...] }
];
```

### 4. Drag & Drop des widgets

* déplacer les widgets dans le dashboard
* réorganiser dynamiquement

---

# Partie 1 — Widget Stats

Créer un widget `stats.js` :

### Contraintes :

* affichage de cartes statistiques
* utilisation de Tailwind
* rendu dynamique basé sur des données

### Exemple attendu :

* Users
* Orders
* Revenue

# Partie 2 — Widget Table triable

Créer un widget `table.js` :

### Contraintes :

* tableau HTML dynamique
* tri sur clic de colonne
* tri ascendant / descendant
* indicateur visuel (▲ / ▼)


# Partie 3 — Widget Chutier

Créer un widget `chutier.js` :

### Contraintes :

* zone gauche : liste d’éléments
* zone droite : 3 zones vides
* drag & drop :

  * gauche → droite
  * droite → gauche

# Partie 4 — Core Dashboard

Créer :

### un registry de widgets

```js
registerWidget()
getWidget()
```

### un moteur de rendu

* lecture du config
* injection des widgets

### drag & drop global des widgets

---

# Contraintes UI

* utilisation de Tailwind uniquement
* design propre et lisible
* responsive (minimum tablette)

---

# Livrables

* projet complet (HTML / JS / Tailwind)
* code structuré
* README expliquant :

  * comment ajouter un widget
  * comment utiliser le dashboard

---

## Bonus Persistance

* sauvegarde du layout (localStorage)

## Bonus Communication entre widgets

Par ex :

* stats = nombre d’éléments dans le chutier

## Bonus Ajout dynamique de widget

## Bonus Widget supplémentaire

Par ex :

* notifications
* chart mock

---

# Les Attendus pédagogiques

On attend de vous :

* une **logique modulaire**
* une **bonne séparation des responsabilités**
* une **capacité à factoriser**
* une **approche “plugin”**

---

# Conseil

Commencez par :

1. le registry
2. le dashboard
3. les widgets



