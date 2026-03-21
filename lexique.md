**CSS scalable** : Approche de structuration du CSS visant à le rendre facilement gérable, maintenable et extensible à mesure que le projet grandit.

**Sass** : Préprocesseur CSS qui étend les fonctionnalités du CSS natif avec des capacités telles que les variables, le nesting, les mixins et les fonctions, permettant de structurer un CSS scalable.

**Limites du CSS traditionnel** : Problèmes rencontrés avec le CSS natif tels que les difficultés liées à la spécificité, la cascade, les soucis de maintenance, la redondance et la duplication des styles, ainsi que les défis de modularité et de réutilisabilité.

**Architecture CSS** : Organisation et structuration du code CSS et des fichiers dans un projet, visant la maintenabilité et la scalabilité (par exemple, le 7-1 pattern).

**7-1 pattern** : Architecture de fichiers Sass qui organise le code en sept dossiers (base, layout, components, utilities, vendors, themes, abstracts) et un fichier d'import principal, favorisant la maintenabilité et la scalabilité.

**Modularité (CSS/Sass)** : Capacité à diviser le code CSS ou Sass en blocs indépendants et réutilisables, facilitant la gestion et la réutilisation des styles.

**Tailwind CSS** : Framework CSS utility-first qui fournit un ensemble de classes utilitaires composables pour construire rapidement des interfaces utilisateur directement dans le balisage HTML.

**UI moderne, responsive et maintenable** : Interface utilisateur qui est esthétiquement actuelle, s'adapte harmonieusement à différentes tailles d'écran (responsive) et est facile à modifier, à mettre à jour et à faire évoluer.

**Stratégie CSS** : Ensemble des choix méthodologiques et techniques adoptés pour gérer le CSS dans un projet, incluant l'utilisation de Sass, Tailwind ou une combinaison des deux.

**Spécificité (CSS)** : Mécanisme du CSS qui détermine quelle règle de style s'applique lorsqu'un élément est ciblé par plusieurs sélecteurs différents; identifiée comme une source de problèmes de maintenance.

**Cascade (CSS)** : Principe fondamental du CSS où les styles sont appliqués dans un ordre déterminé, pouvant complexifier la gestion des styles en l'absence de bonne architecture.

**Maintenance (CSS)** : La facilité avec laquelle le code CSS peut être modifié, corrigé et étendu au fil du temps.

**Redondance et duplication des styles (CSS)** : La répétition ou la copie inutile de déclarations ou de blocs de styles CSS, augmentant la taille du code et les efforts de maintenance.

**Réutilisabilité (CSS)** : La capacité à employer des morceaux de code CSS à plusieurs endroits d'un projet sans avoir à les réécrire.

**Variables (Sass)** : Fonctionnalité de Sass permettant de déclarer et de stocker des valeurs (comme des couleurs, des tailles de police) pour les réutiliser à travers la feuille de style, réduisant la duplication.

**Nesting (Sass)** : Fonctionnalité de Sass qui permet d'imbriquer des sélecteurs CSS les uns dans les autres, reflétant la structure HTML et améliorant la lisibilité.

**Mixins (Sass)** : Fonctionnalité de Sass permettant de définir des blocs de styles réutilisables qui peuvent être inclus dans n'importe quel sélecteur, avec ou sans arguments.

**Fonctions (Sass)** : Fonctionnalité de Sass qui permet de créer des logiques pour des calculs et de retourner des valeurs, utiles pour générer des styles dynamiquement.

**Philosophie utility-first (Tailwind)** : L'approche de Tailwind CSS qui privilégie l'utilisation de petites classes utilitaires atomiques directement dans le HTML pour construire des interfaces, plutôt que des classes sémantiques.

**Classes (Tailwind)** : Attributs HTML utilisés par Tailwind CSS pour appliquer des styles prédéfinis (ex: `flex`, `pt-4`, `text-center`), composant l'interface utilisateur.

**Configuration (Tailwind)** : Le processus de personnalisation de Tailwind CSS via le fichier `tailwind.config.js` pour adapter ses valeurs par défaut (couleurs, espacements, etc.) aux besoins du projet.

**CSS natif** : Le langage CSS standard tel qu'il est défini par les spécifications du W3C, sans l'utilisation de préprocesseurs ou de frameworks.

**Organisation des fichiers (Sass)** : La structure des répertoires et des fichiers Sass selon une méthodologie spécifique (comme le 7-1 pattern) pour une meilleure gestion du projet.

**Partial files (Sass)** : Fichiers Sass dont le nom commence par un underscore (`_`) et qui sont conçus pour être importés dans d'autres fichiers Sass sans être compilés directement en fichiers CSS autonomes.

**Import (Sass)** : Directive `@import` de Sass utilisée pour inclure le contenu de fichiers partials dans un fichier Sass principal, permettant de combiner le code modularisé.

**Control directives (Sass)** : Instructions de flux de contrôle en Sass telles que `@if`, `@for`, `@each`, `@while` qui permettent d'ajouter de la logique conditionnelle et des boucles au code Sass.

**@extend (Sass)** : Directive Sass permettant à un sélecteur d'hériter de toutes les propriétés et les sélecteurs associés à un autre sélecteur, favorisant la réutilisabilité et réduisant la duplication.

**Placeholders (Sass)** : Sélecteurs spéciaux en Sass, commençant par `%`, qui définissent des styles réutilisables sans générer de CSS seul, tant qu'ils ne sont pas étendus par `@extend`.

**Installation et configuration de Tailwind CSS** : Les étapes nécessaires pour intégrer Tailwind CSS dans un projet, incluant l'installation via npm/yarn et la mise en place du fichier `tailwind.config.js`.

**tailwind.config.js** : Le fichier JavaScript central pour la personnalisation de Tailwind CSS, où l'on définit les thèmes, les palettes de couleurs, les breakpoints et les utilitaires personnalisés.

**Purge des classes inutilisées (Tailwind)** : Processus d'optimisation de Tailwind CSS qui consiste à supprimer toutes les classes utilitaires non détectées dans les fichiers du projet lors de la compilation finale, réduisant la taille du fichier CSS.

**Personnalisation de Tailwind** : La capacité à modifier les paramètres par défaut de Tailwind CSS pour l'adapter spécifiquement aux besoins visuels et fonctionnels d'un projet.

**Thèmes (Tailwind)** : Ensembles cohérents de propriétés visuelles (couleurs, polices, espacements) définis et gérés dans la configuration de Tailwind CSS pour une marque ou un style spécifique.

**Palettes de couleurs (Tailwind)** : Collections de couleurs définies dans le fichier de configuration de Tailwind CSS, offrant une base cohérente pour le design d'une interface.

**Fonts (Tailwind)** : Polices de caractères configurées et utilisées dans le cadre d'un projet Tailwind CSS.

**Custom utilities (Tailwind)** : Classes utilitaires personnalisées que l'on peut ajouter à la configuration de Tailwind CSS pour étendre ses fonctionnalités de base.

**Breakpoints (Tailwind)** : Points de rupture définis dans la configuration de Tailwind CSS pour le design responsive, permettant d'appliquer des styles différents en fonction de la taille de l'écran.

**Plugins Tailwind** : Extensions qui ajoutent des fonctionnalités supplémentaires ou des groupes de classes utilitaires à Tailwind CSS, ou qui permettent de modifier son comportement.

**Création de plugins personnalisés (Tailwind)** : Le processus de développement de ses propres extensions pour ajouter des fonctionnalités spécifiques ou des utilitaires personnalisés à Tailwind CSS.

**UI responsive (Tailwind)** : L'implémentation d'une interface utilisateur qui s'adapte dynamiquement à différentes tailles d'écran et appareils en utilisant les fonctionnalités responsives de Tailwind CSS.

**Variants responsive et hover (Tailwind)** : Préfixes de classes Tailwind (ex: `md:`, `hover:`) qui appliquent des styles conditionnellement, comme pour les tailles d'écran spécifiques ou les états d'interaction (survol de la souris).

**Gestion des états et animations (Tailwind)** : L'utilisation des classes et variants de Tailwind CSS pour styliser les différents états des éléments (ex: `focus:`, `active:`) et pour créer des animations.

**Méthodologie (Sass, Tailwind, mixte)** : L'approche choisie pour le développement CSS d'un projet, qui peut être purement Sass, purement Tailwind, ou une combinaison des deux.

**Contexte du projet** : Les caractéristiques spécifiques d'un projet (taille, équipe, exigences, etc.) qui influencent le choix des outils et des stratégies CSS.

**Perspectives d'évolution (CSS)** : La réflexion sur les tendances futures du CSS et des bonnes pratiques pour maintenir le code à jour et performant.

**Bonnes pratiques (CSS)** : Ensemble de recommandations et de conventions pour écrire du code CSS efficace, propre, maintenable et performant.

