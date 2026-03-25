Bonjour !

Ce TP vous guidera à travers les étapes essentielles pour démarrer un projet web avec Tailwind CSS, en mettant l'accent sur une configuration propre et optimisée.

---

### **TP : Configuration de Projet Tailwind CSS de Zéro avec Optimisation (Purge/Content)**

**Objectif du TP :**
Configurer un projet Tailwind CSS de zéro, en intégrant les outils nécessaires et en activant l'optimisation du CSS généré.

**Contexte :**
La configuration initiale de Tailwind CSS est une étape clé pour tout projet web moderne. Maîtriser cette étape garantit un environnement de développement efficace et des performances optimales en production grâce à la suppression du CSS inutilisé.

**Prérequis :**
*   Node.js et npm (ou Yarn) installés sur votre machine.
*   Un éditeur de code (VS Code est recommandé).
*   Des connaissances de base en HTML et CSS.
*   Une compréhension des concepts de ligne de commande.

**Consignes Générales :**
L'utilisation d'outils d'IA générative (ChatGPT, Copilot, etc.) est encouragée pour vous aider à comprendre les concepts, générer des extraits de code ou déboguer. Cependant, l'objectif principal est votre *compréhension* et votre *capacité à vérifier* le code produit. Ne vous contentez pas de copier-coller. Posez des questions à l'IA, demandez des explications, et testez chaque étape. Soyez critique : l'IA peut parfois générer des informations obsolètes ou incorrectes, surtout avec les évolutions rapides des outils front-end.

---

**Étapes du TP :**

**1. Initialisation du projet**
*   Créez un nouveau dossier pour votre projet (ex: `mon-projet-tailwind`).
*   Ouvrez ce dossier dans votre terminal.
*   Initialisez un nouveau projet Node.js :
    ```bash
    npm init -y
    ```
    *(Cette commande crée un fichier `package.json` par défaut.)*

**2. Installation des dépendances**
*   Installez Tailwind CSS ainsi que ses dépendances PostCSS et Autoprefixer :
    ```bash
    npm install -D tailwindcss postcss autoprefixer
    ```
    *   **Question :** À quoi servent `postcss` et `autoprefixer` dans ce contexte ? (Utilisez l'IA si besoin pour une explication concise).

**3. Génération des fichiers de configuration**
*   Générez les fichiers de configuration de Tailwind CSS et PostCSS :
    ```bash
    npx tailwindcss init -p
    ```
    *   Vérifiez que deux nouveaux fichiers ont été créés à la racine de votre projet : `tailwind.config.js` et `postcss.config.js`.
    *   **Question :** Que signifie l'option `-p` dans cette commande ?

**4. Configuration de l'entrée CSS**
*   Créez un dossier `src` à la racine de votre projet.
*   À l'intérieur de `src`, créez un fichier `input.css`.
*   Ajoutez les directives Tailwind CSS de base dans `src/input.css` :
    ```css
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```

**5. Création d'un fichier HTML de test**
*   Créez un fichier `index.html` à la racine de votre projet.
*   Ajoutez une structure HTML simple et liez votre futur fichier CSS compilé (`dist/output.css`) :
    ```html
    <!DOCTYPE html>
    <html lang="fr">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Mon Projet Tailwind</title>
        <link href="./dist/output.css" rel="stylesheet">
    </head>
    <body>
        <h1 class="text-3xl font-bold text-blue-600 p-4">Bienvenue avec Tailwind CSS !</h1>
        <p class="mt-2 text-lg text-gray-700 mx-4">Ceci est un paragraphe stylisé avec Tailwind.</p>
    </body>
    </html>
    ```

**6. Script de compilation**
*   Dans votre fichier `package.json`, ajoutez un script `build` pour compiler votre CSS Tailwind. Il est utile d'ajouter un mode `watch` pour le développement.
    ```json
    "scripts": {
        "build": "tailwindcss -i ./src/input.css -o ./dist/output.css",
        "watch": "tailwindcss -i ./src/input.css -o ./dist/output.css --watch"
    },
    ```
    *   **Note :** Le dossier `dist` sera créé automatiquement lors de la première compilation.

**7. Test initial**
*   Lancez la compilation de votre CSS :
    ```bash
    npm run build
    ```
*   Ouvrez le fichier `index.html` dans votre navigateur.
*   Vérifiez que le titre et le paragraphe sont stylisés avec les classes Tailwind que vous avez ajoutées.

**8. Configuration de l'optimisation (Purge/Content)**
*   Dans votre fichier `tailwind.config.js`, configurez l'option `content` (ou `purge` si vous utilisez une version très ancienne de Tailwind CSS, mais `content` est la norme actuelle) pour qu'elle scanne votre fichier `index.html`.
    *   **Tâche :** Utilisez l'IA pour vous aider à trouver la syntaxe correcte pour `content` afin de scanner tous les fichiers `.html` de votre projet (ou spécifiquement `index.html` pour ce TP).
    *   **Question :** Expliquez en quelques mots pourquoi cette configuration est essentielle pour la performance de votre site web.

**9. Vérification de l'optimisation**
*   **Avant de configurer `content` :**
    *   Exécutez `npm run build`.
    *   Notez la taille du fichier `dist/output.css` (vous pouvez le voir dans votre explorateur de fichiers ou via `ls -lh dist/output.css` dans le terminal).
*   **Après avoir configuré `content` :**
    *   Assurez-vous que votre configuration `content` est active dans `tailwind.config.js`.
    *   Exécutez à nouveau `npm run build`.
    *   Notez la nouvelle taille du fichier `dist/output.css`.
    *   **Observation :** Comparez les deux tailles. Que constatez-vous ?
*   **Test de suppression :**
    *   Dans `index.html`, ajoutez une classe Tailwind très spécifique que vous n'avez pas encore utilisée, par exemple `bg-purple-500`.
    *   Exécutez `npm run build`.
    *   Vérifiez que `bg-purple-500` est bien présent dans `dist/output.css`.
    *   Supprimez la classe `bg-purple-500` de `index.html`.
    *   Exécutez `npm run build` à nouveau.
    *   Vérifiez que `bg-purple-500` a disparu de `dist/output.css`.
    *   **Documentez vos observations sur la taille du fichier CSS et le comportement de suppression.**

---

**Rendu :**
*   Un lien vers un dépôt Git (GitHub, GitLab, Bitbucket) contenant votre projet complet.
*   Le fichier `README.md` de votre dépôt devra inclure :
    *   Les réponses aux questions posées dans le TP.
    *   Vos observations sur la taille du fichier CSS avant et après l'activation de `content`, ainsi que le test de suppression.

**Critères d'évaluation :**
*   Le projet est fonctionnel et compile correctement le CSS Tailwind.
*   Les fichiers `tailwind.config.js` et `postcss.config.js` sont correctement configurés.
*   L'option `content` (ou `purge`) est correctement configurée et démontre son efficacité.
*   Les réponses aux questions sont claires et pertinentes.
*   Les observations sont précises et justifiées.

**Conseils Utiles :**
*   N'hésitez pas à consulter la documentation officielle de Tailwind CSS (tailwindcss.com) qui est une ressource précieuse.
*   En cas de blocage, reformulez votre question à l'IA ou cherchez des solutions sur des plateformes comme Stack Overflow.
*   Pensez à la structure de vos fichiers pour des projets plus grands : où placeriez-vous d'autres fichiers HTML ou des composants JavaScript qui utilisent des classes Tailwind ? Comment adapteriez-vous la configuration `content` ?

Bon courage !