Absolument ! Voici une proposition de sujet de TP, pragmatique et orientée vers l'apprentissage actif, même avec l'aide de l'IA.

---

## TP : Génération de Classes de Couleurs Dynamiques avec Sass et Tailwind

### Objectif du TP

Utiliser les directives de contrôle Sass (notamment les boucles) pour générer des classes utilitaires Tailwind-like, permettant de créer des variantes de couleurs personnalisées de manière automatisée.

### Contexte

Dans un projet web, il est courant d'avoir une palette de couleurs spécifique qui doit être appliquée de manière cohérente à différents éléments (arrière-plans, textes, bordures, etc.). Plutôt que d'écrire manuellement des dizaines de classes CSS répétitives, nous allons automatiser ce processus en exploitant la puissance de Sass pour générer ces classes dynamiquement. Cela améliore la maintenabilité et la cohérence de votre code.

### Prérequis

*   Connaissances de base en Sass (variables, mixins, fonctions).
*   Connaissances de base en Tailwind CSS (classes utilitaires, configuration).
*   Maîtrise des bases du CSS et du HTML.
*   Un environnement de développement avec Node.js et npm/yarn.

### Énoncé du TP

Votre mission est de créer un fichier Sass qui, à l'aide d'une boucle, générera des classes CSS pour une palette de couleurs définie. Ces classes devront imiter le comportement des utilitaires Tailwind pour les arrière-plans et les textes.

### Étapes du TP

#### 1. Initialisation du Projet

*   Créez un nouveau dossier pour votre projet.
*   Initialisez un projet Node.js (`npm init -y` ou `yarn init -y`).
*   Installez Tailwind CSS et PostCSS :
    ```bash
    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init -p
    ```
*   Configurez votre fichier `tailwind.config.js` pour purger les fichiers HTML et JS (si vous en utilisez).
*   Créez un fichier `src/input.css` et importez les directives de base de Tailwind :
    ```css
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```
*   Créez un script de build dans votre `package.json` pour compiler votre CSS :
    ```json
    "scripts": {
      "build:css": "tailwindcss -i ./src/input.css -o ./dist/output.css --watch"
    }
    ```
*   Lancez le script de build : `npm run build:css`.

#### 2. Définition de la Palette de Couleurs

*   Créez un nouveau fichier Sass, par exemple `src/_custom-colors.scss`.
*   Dans ce fichier, définissez une carte Sass (`$custom-colors`) contenant au moins 5 couleurs personnalisées. Chaque entrée de la carte devra associer un nom de couleur (ex: `primary`, `secondary`, `info`, `success`, `warning`) à sa valeur hexadécimale ou RGB.

    ```sass
    // Exemple :
    $custom-colors: (
      "primary": #3490dc,
      "secondary": #6574cd,
      "success": #38c172,
      "danger": #e3342f,
      "warning": #ffed4a,
    );
    ```

#### 3. Génération des Classes de Base

*   Dans le même fichier `src/_custom-colors.scss` (ou un nouveau fichier Sass importé dans `input.css`), écrivez une boucle `@each` qui itérera sur votre carte `$custom-colors`.
*   À l'intérieur de cette boucle, générez deux types de classes pour chaque couleur :
    *   `bg-[nom-de-couleur]` (ex: `bg-primary`) qui applique la couleur en arrière-plan.
    *   `text-[nom-de-couleur]` (ex: `text-secondary`) qui applique la couleur au texte.

    *Exemple de structure de classe attendue :*
    ```css
    .bg-primary {
      background-color: #3490dc;
    }
    .text-primary {
      color: #3490dc;
    }
    /* ... pour toutes les autres couleurs ... */
    ```

#### 4. Intégration et Test

*   Importez votre fichier Sass `_custom-colors.scss` dans votre fichier `src/input.css` (avant les directives Tailwind si vous voulez que vos classes puissent être surchargées par Tailwind, ou après si vous voulez qu'elles surchargent Tailwind).
    ```css
    @import './_custom-colors.scss'; // Assurez-vous que le chemin est correct

    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```
*   Créez un fichier `index.html` simple dans votre dossier `dist/`.
*   Liez votre fichier `output.css` dans `index.html`.
*   Créez plusieurs éléments HTML (`div`, `p`, `span`) et appliquez-y vos nouvelles classes générées (par exemple, `<div class="bg-primary text-warning p-4">Mon texte</div>`).
*   Ouvrez `index.html` dans votre navigateur et vérifiez que les couleurs s'appliquent correctement.

#### 5. Extension (Défis Supplémentaires)

Une fois les étapes précédentes validées, vous pouvez explorer les extensions suivantes :

**A. Variantes au survol (Hover States) :**
*   Modifiez votre boucle Sass pour générer également des classes pour les états de survol. Par exemple, `hover:bg-[nom-de-couleur]-darker` ou `hover:text-[nom-de-couleur]-lighter`.
*   Vous devrez utiliser une fonction Sass (comme `darken()` ou `lighten()`) pour modifier la couleur de base au survol.

**B. Classes de Bordure :**
*   Ajoutez la génération de classes pour les bordures : `border-[nom-de-couleur]` et `border-[nom-de-couleur]-hover` (avec une épaisseur de bordure par défaut, par exemple `1px`).

**C. Intégration à `tailwind.config.js` (Avancé) :**
*   Pour une intégration plus propre et pour que Tailwind reconnaisse ces couleurs dans ses utilitaires JIT (Just-In-Time), explorez comment étendre la configuration de Tailwind (`tailwind.config.js`) avec vos couleurs personnalisées.
*   Cela pourrait impliquer de générer un objet JavaScript depuis Sass (via un script Node.js par exemple) ou de définir les couleurs directement dans le fichier de configuration de Tailwind, en utilisant les mêmes noms que ceux de votre carte Sass. L'objectif est de pouvoir écrire `bg-primary` et que Tailwind le reconnaisse *nativement* sans avoir à générer manuellement le CSS via Sass.

### Conseils pour l'utilisation de l'IA

N'hésitez pas à utiliser des outils d'IA pour vous aider à générer le code Sass ou à comprendre les fonctions spécifiques (comme `darken()` ou `lighten()`). Cependant, assurez-vous de bien comprendre chaque ligne de code générée. L'objectif est d'apprendre, pas seulement de copier-coller.

Voici quelques exemples de prompts que vous pourriez utiliser :
*   "Comment créer une carte Sass avec des noms de couleurs et leurs valeurs hexadécimales ?"
*   "Comment utiliser la directive `@each` en Sass pour itérer sur une carte et générer des classes CSS ?"
*   "Quelle fonction Sass permet d'assombrir une couleur de 10% ?"
*   "Comment étendre la palette de couleurs de Tailwind CSS dans `tailwind.config.js` ?"

Bon courage pour ce TP ! C'est une excellente occasion de maîtriser l'automatisation CSS.

---