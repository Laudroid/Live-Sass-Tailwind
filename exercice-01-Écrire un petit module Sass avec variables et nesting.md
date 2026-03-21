Salut les apprenants !

Ce TP est conçu pour vous familiariser avec deux concepts fondamentaux de Sass : les **variables** et le **nesting**. Vous allez les utiliser pour créer un composant bouton réutilisable et facile à maintenir.

---

### TP : Création d'un composant Bouton avec Sass (Variables & Nesting)

**Contexte :**
Dans tout projet web, les boutons sont des éléments d'interface utilisateur omniprésents. Les styliser de manière cohérente et modulaire est essentiel pour la maintenabilité et l'évolutivité de votre CSS. Sass nous offre des outils puissants pour structurer ces styles efficacement.

**Objectifs d'apprentissage :**
À la fin de ce TP, vous serez capable de :
*   Maîtriser l'utilisation des **variables Sass** pour centraliser et gérer les propriétés de style.
*   Appliquer le **nesting Sass** pour organiser les styles de manière logique et lisible, notamment pour les variantes et les états interactifs d'un composant.
*   Développer un petit **module Sass** réutilisable pour un composant.
*   Comprendre l'organisation d'un fichier Sass partiel (`_nom.scss`).

**Prérequis :**
*   Connaissances de base en HTML et CSS.
*   Un environnement de développement avec Node.js installé (pour compiler Sass via la CLI).
*   Un éditeur de code (VS Code, Sublime Text, etc.).

---

**Consignes :**

**Étape 1 : Initialisation du projet**

1.  Créez un nouveau dossier pour votre projet, par exemple `sass-button-tp`.
2.  À l'intérieur de ce dossier, créez les fichiers et dossiers suivants :
    *   `index.html` (pour tester vos boutons)
    *   `style.scss` (votre fichier Sass principal)
    *   Un dossier `sass/`
    *   À l'intérieur de `sass/`, créez `_button.scss` (votre module de bouton).

3.  Lancez la compilation Sass en mode "watch" depuis votre terminal, à la racine de votre projet :
    ```bash
    sass --watch style.scss:style.css
    ```
    Cela compilera automatiquement `style.scss` en `style.css` à chaque modification.

**Étape 2 : Le module `_button.scss` (Variables)**

Ouvrez `sass/_button.scss`. C'est ici que nous allons définir les styles de notre bouton.

1.  **Définissez des variables Sass** pour les propriétés communes de vos boutons. Pensez aux couleurs, aux espacements, aux rayons de bordure, etc.
    *   Exemples :
        *   `$btn-primary-bg: #007bff;`
        *   `$btn-primary-color: #fff;`
        *   `$btn-secondary-bg: #6c757d;`
        *   `$btn-secondary-color: #fff;`
        *   `$btn-padding: 0.75em 1.5em;`
        *   `$btn-border-radius: 0.25em;`
        *   `$btn-transition-duration: 0.2s;`

**Étape 3 : Le module `_button.scss` (Base du bouton)**

Sous vos variables, créez le style de base pour un bouton générique.

1.  Utilisez le sélecteur `.btn`.
2.  Appliquez des propriétés CSS de base en utilisant vos variables lorsque c'est pertinent :
    *   `display: inline-block;`
    *   `padding: $btn-padding;`
    *   `border: 1px solid transparent;`
    *   `border-radius: $btn-border-radius;`
    *   `cursor: pointer;`
    *   `font-size: 1rem;`
    *   `line-height: 1.5;`
    *   `text-align: center;`
    *   `text-decoration: none;`
    *   `transition: all $btn-transition-duration ease-in-out;`
    *   Définissez une couleur de fond et de texte par défaut (par exemple, un bouton "light").

**Étape 4 : Le module `_button.scss` (Variantes avec Nesting)**

Maintenant, nous allons créer des variantes de boutons (primaire, secondaire) en utilisant le nesting Sass.

1.  À l'intérieur du sélecteur `.btn`, utilisez le nesting pour définir des variantes. Le `&` est très utile ici pour faire référence au parent.
    *   Exemple pour un bouton primaire :
        ```scss
        .btn {
          // Styles de base...

          &--primary {
            background-color: $btn-primary-bg;
            color: $btn-primary-color;
            border-color: $btn-primary-bg;
          }

          &--secondary {
            background-color: $btn-secondary-bg;
            color: $btn-secondary-color;
            border-color: $btn-secondary-bg;
          }
        }
        ```

**Étape 5 : Le module `_button.scss` (États interactifs avec Nesting)**

Ajoutez les styles pour les états interactifs (`:hover`, `:active`, `:focus`) de vos boutons, toujours en utilisant le nesting.

1.  À l'intérieur du sélecteur `.btn` (et potentiellement de chaque variante si les effets sont différents), ajoutez les styles pour `:hover`, `:active` et `:focus`.
    *   Exemple pour le `.btn` de base :
        ```scss
        .btn {
          // Styles de base...

          &:hover {
            opacity: 0.8; // Un exemple simple
            transform: translateY(-1px);
          }

          &:active {
            transform: translateY(0);
            box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
          }

          // ... et pour les variantes
          &--primary {
            // ...
            &:hover {
              background-color: darken($btn-primary-bg, 10%); // Exemple d'utilisation de fonction Sass
              border-color: darken($btn-primary-bg, 10%);
            }
          }
        }
        ```

**Étape 6 : Intégration et test**

1.  **Dans `style.scss` :** Importez votre module de bouton.
    ```scss
    @import 'sass/button';
    ```
2.  **Dans `index.html` :**
    *   Liez votre fichier CSS compilé (`style.css`) dans la section `<head>`.
    *   Créez plusieurs boutons pour tester vos styles :
        ```html
        <!DOCTYPE html>
        <html lang="fr">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <title>TP Boutons Sass</title>
            <link rel="stylesheet" href="style.css">
        </head>
        <body>
            <h1>Mes Boutons Sass</h1>

            <button class="btn">Bouton Standard</button>
            <button class="btn btn--primary">Bouton Primaire</button>
            <button class="btn btn--secondary">Bouton Secondaire</button>

            <a href="#" class="btn btn--primary">Lien Bouton Primaire</a>
        </body>
        </html>
        ```
3.  Ouvrez `index.html` dans votre navigateur et vérifiez que vos boutons sont stylés correctement et que les états `:hover` et `:active` fonctionnent.

---

**Livrables :**
*   Le fichier `_button.scss`
*   Le fichier `style.scss`
*   Le fichier `index.html`

---

**Conseils pour l'utilisation de l'IA :**

L'IA est un outil formidable pour vous aider à apprendre et à accélérer votre travail. N'hésitez pas à l'utiliser !

*   **Demandez des exemples :** "Donne-moi des exemples de variables Sass pour des couleurs de boutons." ou "Comment structurer les états `:hover` et `:active` avec le nesting Sass ?"
*   **Obtenez des propriétés CSS :** "Quelles sont les propriétés CSS courantes pour styliser un bouton ?"
*   **Comprenez, ne copiez pas aveuglément :** Si l'IA vous donne un bloc de code, prenez le temps de comprendre chaque ligne. Si quelque chose n'est pas clair, demandez-lui des explications : "Peux-tu m'expliquer à quoi sert `darken()` en Sass ?"
*   **Utilisez-la pour explorer :** "Comment pourrais-je rendre mes transitions de bouton plus fluides ?"

L'objectif est d'apprendre et de maîtriser les concepts, pas seulement d'obtenir un résultat. L'IA est votre assistant, pas votre remplaçant pour la compréhension !

---

**Pour aller plus loin (Bonus) :**

*   **Boutons de tailles différentes :** Ajoutez des variantes pour des boutons plus petits (`.btn--small`) ou plus grands (`.btn--large`) en utilisant des variables et le nesting.
*   **Bouton désactivé :** Créez un style pour l'état désactivé (`.btn:disabled`).
*   **Bouton "outline" :** Créez une variante de bouton avec un fond transparent et une bordure colorée (`.btn--outline-primary`).
*   **Mixins Sass :** Si vous vous sentez à l'aise, explorez comment une `@mixin` pourrait simplifier la création de nouvelles variantes de boutons.

Amusez-vous bien avec ce TP ! C'est une excellente façon de poser des bases solides en Sass.