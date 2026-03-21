Bonjour à toutes et à tous !

Ce TP est conçu pour vous permettre d'explorer la puissance des mixins Sass pour créer des composants réutilisables et responsifs, un atout majeur dans tout projet web, y compris ceux utilisant Tailwind CSS.

---

### TP : Mixin de Bouton Responsif avec Sass et Intégration Tailwind

**Objectif du TP :**
Écrire des mixins Sass personnalisés pour encapsuler des styles complexes et responsifs, et comprendre leur interaction potentielle dans un projet utilisant Tailwind CSS.

**Contexte :**
Les boutons sont des éléments interactifs essentiels. Assurer leur cohérence visuelle et leur adaptabilité sur différentes tailles d'écran est une tâche récurrente. Plutôt que de répéter du code CSS ou de jongler avec de nombreuses classes utilitaires pour chaque variation, un mixin Sass permet de centraliser cette logique, rendant votre code plus DRY (Don't Repeat Yourself), plus maintenable et plus expressif.

**Prérequis :**
*   Bases de Sass (variables, mixins, imbrication).
*   Bases de Tailwind CSS (classes utilitaires, configuration).
*   Notions de responsive design (media queries).
*   Un environnement de développement avec Sass et Tailwind CSS configurés (par exemple, via PostCSS et un script de build).

---

### Mise en place du projet (si ce n'est pas déjà fait) :

1.  **Structure de fichiers suggérée :**
    ```
    mon-projet/
    ├── public/
    │   └── index.html
    ├── src/
    │   ├── main.scss
    │   ├── _variables.scss
    │   ├── _mixins.scss
    │   └── _base.scss
    ├── tailwind.config.js
    ├── postcss.config.js
    ├── package.json
    ```
2.  **Configuration Sass/Tailwind :**
    Assurez-vous que votre `main.scss` importe vos fichiers Sass et que Tailwind est correctement inclus et compilé.
    *   Dans `src/main.scss` :
        ```scss
        @import 'tailwindcss/base';
        @import 'tailwindcss/components';
        @import 'tailwindcss/utilities';

        @import 'variables';
        @import 'mixins';
        @import 'base';

        // Vos styles personnalisés ici
        ```
    *   Votre `tailwind.config.js` devrait contenir vos breakpoints par défaut ou personnalisés.

---

### Exercice : Création du Mixin de Bouton Responsif

Votre mission est de créer un mixin Sass qui génère des styles complets pour un bouton, incluant sa responsivité.

**Étape 1 : Définir les Variables et Breakpoints**

*   Dans `src/_variables.scss`, définissez des variables pour :
    *   Les couleurs de base des boutons (ex: `$primary-color`, `$secondary-color`, `$text-light`, `$text-dark`).
    *   Les tailles de police par défaut et pour différents breakpoints (ex: `$font-size-base`, `$font-size-md`, `$font-size-lg`).
    *   Les paddings par défaut et pour différents breakpoints (ex: `$padding-base`, `$padding-md`, `$padding-lg`).
    *   Vous pouvez réutiliser les breakpoints de Tailwind dans vos media queries Sass pour une meilleure cohérence (ex: `$breakpoint-md: 768px;`).

**Étape 2 : Écrire le Mixin de Bouton de Base**

*   Dans `src/_mixins.scss`, créez un mixin nommé `button-responsive`.
*   Ce mixin devra accepter des paramètres pour personnaliser le bouton. Voici quelques suggestions de paramètres :
    *   `$bg-color`: Couleur de fond du bouton.
    *   `$text-color`: Couleur du texte.
    *   `$hover-bg-color`: Couleur de fond au survol.
    *   `$hover-text-color`: Couleur du texte au survol.
    *   `$border-radius`: Rayon des bordures.
    *   `$padding-y-base`, `$padding-x-base`: Padding vertical et horizontal de base.
    *   `$font-size-base`: Taille de police de base.
*   Commencez par les styles de base (non responsifs) :
    *   `display: inline-flex;` (ou `inline-block`)
    *   `align-items: center;` (si `inline-flex`)
    *   `justify-content: center;` (si `inline-flex`)
    *   `padding`, `font-size`, `border-radius`, `border`, `cursor`, `transition`.
    *   Ajoutez les styles pour l'état `:hover`.

**Étape 3 : Intégrer la Responsivité**

*   À l'intérieur de votre mixin `button-responsive`, utilisez des media queries Sass pour ajuster les propriétés du bouton en fonction des breakpoints que vous avez définis dans `_variables.scss`.
*   **Exemples d'adaptations responsives :**
    *   **Padding et taille de police :** Augmentez le `padding` et le `font-size` pour les écrans `md` et `lg`.
    *   **Largeur :** Sur les petits écrans (en dessous de `md`), le bouton pourrait prendre `width: 100%` et `display: flex`, puis revenir à `width: auto` et `display: inline-flex` sur les écrans plus grands.
    *   **Alignement :** Si le bouton est `100%` large, il pourrait être centré.

**Étape 4 : Utiliser le Mixin**

*   Dans `src/main.scss` (ou un fichier `_components.scss` si vous en avez un), créez au moins deux classes CSS différentes en utilisant votre mixin.
    *   Exemple : `.btn-primary` et `.btn-secondary`.
    *   Passez des paramètres différents à chaque appel du mixin pour créer des variations de boutons.

    ```scss
    .btn-primary {
        @include button-responsive(
            $bg-color: $primary-color,
            $text-color: $text-light,
            $hover-bg-color: darken($primary-color, 10%),
            $hover-text-color: $text-light,
            $border-radius: 0.5rem,
            $padding-y-base: 0.75rem,
            $padding-x-base: 1.5rem,
            $font-size-base: 1rem
        );
    }

    .btn-secondary {
        @include button-responsive(
            $bg-color: $secondary-color,
            $text-color: $text-dark,
            $hover-bg-color: darken($secondary-color, 10%),
            $hover-text-color: $text-dark,
            $border-radius: 0.25rem,
            $padding-y-base: 0.5rem,
            $padding-x-base: 1rem,
            $font-size-base: 0.875rem
        );
    }
    ```

**Étape 5 : Intégration HTML et Test**

*   Dans `public/index.html`, ajoutez quelques boutons avec les classes que vous avez créées (`.btn-primary`, `.btn-secondary`).
*   Compilez votre Sass et Tailwind.
*   Ouvrez `index.html` dans votre navigateur et testez le comportement responsif en redimensionnant la fenêtre.
*   Observez comment les styles générés par votre mixin Sass s'appliquent et interagissent avec les styles de base de Tailwind (si vous en avez).

---

### Critères de validation :

*   Le mixin `button-responsive` est défini dans `_mixins.scss` et utilise des paramètres pour la personnalisation.
*   Le mixin intègre des media queries Sass pour gérer la responsivité (au moins deux breakpoints différents).
*   Au moins deux classes de boutons différentes sont créées dans `main.scss` en utilisant le mixin avec des paramètres distincts.
*   Les boutons affichent un comportement responsif correct (padding, font-size, largeur, etc.) lorsque la taille de l'écran change.
*   Le code est clair, bien structuré et utilise les variables Sass de manière appropriée.

---

### Conseils pour l'utilisation de l'IA :

L'intelligence artificielle est un excellent assistant pour le développement. N'hésitez pas à l'utiliser pour vous aider dans ce TP, mais rappelez-vous que votre rôle est de comprendre, d'adapter et de valider le code généré.

*   **Pour démarrer :** Vous pouvez demander à l'IA : "Écris un mixin Sass pour un bouton responsif avec des paramètres pour la couleur de fond, la couleur de texte, le padding et la taille de police, et qui s'adapte aux breakpoints `sm`, `md`, `lg`."
*   **Pour explorer des options :** "Comment puis-je ajouter un effet de transition au survol pour mon bouton Sass ?" ou "Comment rendre mon bouton 100% large sur mobile et auto sur desktop avec un mixin Sass ?"
*   **Vérifiez et adaptez :**
    *   **Cohérence :** Le code généré par l'IA utilise-t-il les noms de variables et les conventions de votre projet ? Les breakpoints correspondent-ils à ceux que vous avez définis (ou à ceux de Tailwind si vous les utilisez) ?
    *   **Exactitude :** Les media queries sont-elles correctement écrites ? Les propriétés CSS sont-elles appliquées comme attendu ?
    *   **Optimisation :** Y a-t-il des redondances ? Le code pourrait-il être plus concis ou plus performant ?
    *   **Compréhension :** Avant de copier-coller, assurez-vous de comprendre chaque ligne de code. Si ce n'est pas le cas, demandez à l'IA de vous l'expliquer.

L'objectif est d'apprendre à *diriger* l'IA et à *critiquer* son output pour en faire un outil d'apprentissage et de productivité, et non un simple générateur de code aveugle.

Bon courage et amusez-vous bien avec Sass et Tailwind !