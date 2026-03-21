Salut les développeurs !

Ce TP est conçu pour vous familiariser avec l'application pratique de Tailwind CSS. L'objectif est de reproduire un élément d'interface utilisateur courant : la carte.

---

### **TP : Reproduction d'une carte UI avec Tailwind CSS**

**Objectif du TP :** Utiliser des classes Tailwind pour reproduire un design de carte d'interface utilisateur simple et fonctionnel.

**Contexte :**
Les cartes sont des composants fondamentaux dans de nombreuses interfaces web modernes. Elles permettent d'organiser le contenu de manière visuellement agréable et facile à digérer. Tailwind CSS, avec son approche utilitaire, est particulièrement efficace pour construire ce type de composant rapidement et de manière flexible.

**Énoncé du TP :**
Votre mission est de reproduire une carte d'interface utilisateur en utilisant exclusivement les classes utilitaires de Tailwind CSS.

---

#### **Design à Reproduire :**

Imaginez une carte de produit ou d'article simple, présentant les éléments suivants :

*   **Conteneur de la carte :**
    *   Fond blanc.
    *   Coins légèrement arrondis (par exemple, `rounded-lg`).
    *   Une ombre subtile (`shadow-md` ou `shadow-lg`).
    *   Une largeur fixe ou maximale (`max-w-sm` ou `w-80`).
    *   Un espacement interne (`p-4` ou `p-6`).
*   **Image :**
    *   Placée en haut de la carte, occupant toute sa largeur.
    *   Hauteur fixe (`h-48` ou `h-56`).
    *   Les coins supérieurs de l'image doivent être arrondis pour correspondre au conteneur de la carte.
    *   L'image doit couvrir l'espace alloué sans être déformée (`object-cover`).
*   **Contenu textuel :**
    *   Un titre (par exemple, "Nom du Produit" ou "Titre de l'Article") :
        *   Texte en gras (`font-bold`).
        *   Taille de police légèrement plus grande (`text-xl` ou `text-2xl`).
        *   Marge inférieure (`mb-2`).
    *   Une courte description (par exemple, "Une description concise et attrayante du produit ou de l'article, limitée à quelques lignes.") :
        *   Couleur de texte gris clair (`text-gray-700`).
        *   Taille de police standard (`text-base`).
        *   Marge inférieure (`mb-4`).
*   **Bouton d'action :**
    *   Placé en bas de la carte.
    *   Texte : "En savoir plus" ou "Ajouter au panier".
    *   Fond bleu (`bg-blue-500`).
    *   Texte blanc (`text-white`).
    *   Padding horizontal et vertical (`px-4 py-2`).
    *   Coins arrondis (`rounded-md`).
    *   Effet au survol (`hover:bg-blue-600`).

---

#### **Prérequis :**

*   Connaissances de base en HTML.
*   Un environnement de développement avec Node.js installé.
*   Compréhension des principes fondamentaux de Tailwind CSS (classes utilitaires, configuration).

#### **Mise en place du projet :**

1.  Créez un nouveau dossier pour votre projet.
2.  Initialisez un projet Node.js : `npm init -y`
3.  Installez Tailwind CSS et ses dépendances : `npm install -D tailwindcss postcss autoprefixer`
4.  Générez les fichiers de configuration Tailwind : `npx tailwindcss init -p`
5.  Configurez votre fichier `tailwind.config.js` pour qu'il scanne vos fichiers HTML :
    ```javascript
    // tailwind.config.js
    module.exports = {
      content: [
        "./*.html", // Scanne tous les fichiers HTML à la racine
        // Ajoutez d'autres chemins si nécessaire, par exemple "./src/**/*.{html,js,ts,jsx,tsx}"
      ],
      theme: {
        extend: {},
      },
      plugins: [],
    }
    ```
6.  Créez un fichier `input.css` à la racine de votre projet et ajoutez les directives Tailwind :
    ```css
    /* input.css */
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```
7.  Créez un fichier `index.html` à la racine de votre projet.
8.  Ajoutez un script dans votre `package.json` pour compiler Tailwind :
    ```json
    "scripts": {
      "build:css": "tailwindcss -i ./input.css -o ./output.css --watch"
    }
    ```
9.  Lancez la compilation : `npm run build:css`
10. Liez le fichier `output.css` dans votre `index.html` : `<link href="./output.css" rel="stylesheet">`

#### **Étapes du TP :**

1.  **Structure HTML de base :**
    *   Dans votre `index.html`, créez la structure sémantique de la carte : un `div` principal pour le conteneur, une `img`, un autre `div` pour le contenu textuel (avec un `h2`, un `p`), et un `button`.
    *   Utilisez une image de placeholder (par exemple, `https://via.placeholder.com/400x200`) pour l'instant.

2.  **Conteneur de la carte :**
    *   Appliquez les classes Tailwind au `div` principal pour définir le fond, les arrondis, l'ombre et la largeur/espacement interne.

3.  **L'image :**
    *   Appliquez les classes Tailwind à l'élément `img` pour définir sa largeur, sa hauteur, son comportement d'ajustement et les arrondis des coins supérieurs.

4.  **Le bloc de contenu textuel :**
    *   Appliquez les classes Tailwind au `div` qui contient le titre et la description pour gérer l'espacement si nécessaire.
    *   Appliquez les classes au `h2` pour le style du titre (taille, gras, marge).
    *   Appliquez les classes au `p` pour le style de la description (couleur, taille, marge).

5.  **Le bouton d'action :**
    *   Appliquez les classes Tailwind à l'élément `button` pour définir son fond, sa couleur de texte, son padding, ses arrondis et son effet au survol.

6.  **Ajustements finaux (optionnel mais recommandé) :**
    *   Assurez-vous que la carte est centrée sur la page (par exemple, en utilisant Flexbox sur le `body` ou un conteneur parent).
    *   Vérifiez la responsivité de la carte. Comment se comporte-t-elle sur différentes tailles d'écran ?

#### **Conseils pour l'utilisation de l'IA :**

L'utilisation d'outils d'IA pour vous aider à trouver les classes Tailwind appropriées est encouragée. Par exemple, vous pouvez demander :
*   "Comment faire un div avec des coins arrondis et une ombre en Tailwind CSS ?"
*   "Quelles classes Tailwind pour un bouton bleu avec texte blanc et effet hover ?"
*   "Donne-moi le HTML de base pour une carte avec une image, un titre, un paragraphe et un bouton."

L'objectif n'est pas de copier-coller sans comprendre, mais d'utiliser l'IA comme un assistant intelligent pour accélérer votre apprentissage et votre développement. Soyez prêt à expliquer pourquoi vous avez choisi certaines classes.

#### **Critères de validation :**

*   La carte reproduit visuellement le design décrit.
*   Seules les classes utilitaires de Tailwind CSS sont utilisées (pas de CSS personnalisé dans `output.css` en dehors des directives `@tailwind`).
*   Le code HTML est propre et sémantique.
*   Le projet est fonctionnel et peut être compilé avec `npm run build:css`.

#### **Pour aller plus loin (Challenge) :**

*   **Responsivité avancée :** Adaptez la carte pour qu'elle change de disposition ou de taille à des points de rupture spécifiques (par exemple, la carte prend toute la largeur sur mobile, mais une largeur fixe sur desktop).
*   **Variante de carte :** Créez une deuxième carte avec un design légèrement différent (par exemple, l'image à gauche du texte, ou un badge de catégorie).
*   **Interactivité :** Ajoutez un effet de survol plus complexe à la carte entière (par exemple, un léger agrandissement ou un changement d'ombre).
*   **Mode sombre :** Implémentez une version "mode sombre" de votre carte en utilisant les variantes de mode sombre de Tailwind.

Amusez-vous bien avec ce TP ! C'est une excellente occasion de renforcer vos compétences avec Tailwind CSS.