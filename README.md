# Portfolio — Nelson Camara

Site portfolio professionnel déployé sur **GitHub Pages** pour présenter mes projets de développement dans le cadre de ma recherche d'alternance. Le site récupère dynamiquement les dépôts GitHub via l'**API GitHub**, affiche les README de chaque projet avec rendu Markdown, et propose une navigation fluide avec filtrage par langage et table des matières interactive.

  **Accès direct** : [nelsoncamara.github.io](https://nelsoncamara.github.io)

---

## Fonctionnalités

- **Chargement dynamique des projets** — Les dépôts GitHub sont récupérés automatiquement via l'API REST GitHub, aucune mise à jour manuelle nécessaire
- **Filtrage par langage** — Boutons de filtre générés dynamiquement (Java, Python, C, PHP...) pour naviguer entre les projets
- **Pages de projet dédiées** — Chaque carte redirige vers une page détaillée qui récupère et affiche le README du dépôt avec rendu Markdown complet
- **Rendu Markdown avancé** — Parsing via Marked.js avec coloration syntaxique du code via Highlight.js, support des tableaux, listes, blocs de citation, images
- **Table des matières interactive** — Générée automatiquement depuis les titres du README avec suivi de la section active au scroll (IntersectionObserver)
- **Design responsive** — Adaptation mobile avec navigation simplifiée et grille adaptative
- **Section "Bientôt disponibles"** — Projets en cours de développement affichés avec badge d'état
- **Téléchargement du CV** — Lien direct vers le CV au format PDF

---

## Architecture

```
nelsoncamara.github.io/
├── index.html                → Page d'accueil (hero, grille de projets, filtres)
├── Nelson_Camara_CV_2026.pdf → CV téléchargeable
└── project/
    └── project.html          → Page détaillée d'un projet (README, TOC, métadonnées)
```

**100% front-end** | **Aucun framework** | **Hébergé sur GitHub Pages**

---

## Compétences techniques démontrées

### Intégration API GitHub

- **Fetch asynchrone** — `fetch()` avec `async/await` vers `api.github.com/users/{username}/repos` pour récupérer la liste des dépôts et `raw.githubusercontent.com` pour les README
- **Gestion d'erreurs** — Fallback `main` → `master` pour la branche du README, messages d'erreur en cas d'échec réseau
- **Construction dynamique du DOM** — Génération des cartes projet avec `document.createElement()`, injection via `innerHTML` avec template literals

### Rendu Markdown & Coloration syntaxique

- **Marked.js** — Parsing du Markdown brut (GFM) en HTML avec support des tables, code fencé, listes, blockquotes
- **Highlight.js** — Coloration syntaxique automatique des blocs de code (`pre code`) après rendu

### Table des matières dynamique

- **Extraction des headings** — Parcours des `h1` à `h4` du README rendu pour construire la TOC
- **Slugs uniques** — Génération d'IDs à partir du texte des titres avec gestion des doublons
- **Scroll spy** — `IntersectionObserver` avec `rootMargin` pour suivre la section visible et mettre à jour le lien actif dans la sidebar
- **Smooth scroll** — Navigation au clic avec `scrollIntoView({ behavior: 'smooth' })`

### Design & CSS

- **Design system cohérent** — Variables CSS (`--blue`, `--text`, `--border`, `--surface`) pour une charte graphique uniforme
- **Typographie** — Combinaison Inter (texte) + Montserrat (titres) via Google Fonts
- **Composants réutilisables** — Cards, badges, boutons primaires/secondaires, filtres
- **Sticky nav** — Navigation fixe avec `backdrop-filter: blur(8px)` et fond semi-transparent
- **Responsive design** — Media queries à 768px et 900px, grille CSS `auto-fill` avec `minmax()`
- **Animations** — Transitions CSS sur les cards (`transform`, `box-shadow`), boutons et liens

---

## Déploiement

Le site est automatiquement déployé via **GitHub Pages** depuis la branche `main`. Toute modification poussée sur le dépôt est immédiatement reflétée sur le site en ligne.

Pour un développement local :
```bash
git clone https://github.com/NelsonCamara/nelsoncamara.github.io.git
cd nelsoncamara.github.io
# Ouvrir index.html dans un navigateur
# (ou utiliser un serveur local pour éviter les restrictions CORS)
python -m http.server 8000
```

---

## Technologies

| Technologie | Usage |
|-------------|-------|
| HTML5 / CSS3 | Structure et mise en forme |
| JavaScript (ES6+) | Logique, appels API, manipulation DOM |
| API GitHub REST | Récupération dynamique des dépôts et README |
| Marked.js | Parsing Markdown → HTML |
| Highlight.js | Coloration syntaxique du code |
| Google Fonts | Typographies Inter et Montserrat |
| GitHub Pages | Hébergement et déploiement |

---

## Auteur

**Nelson Camara** — Étudiant en Master Informatique

---

*Portfolio professionnel — Site vitrine dynamique avec intégration API GitHub et rendu Markdown.*
