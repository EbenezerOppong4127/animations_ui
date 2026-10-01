# animations-gallery

Galerie statique d'animations UI : des écrans animés pour une application de
rapport journalier de chantier, des micro-interactions (boutons, loaders,
notifications…) et des pages complètes animées (landing page, parallaxe,
transitions…). Chaque animation est une page HTML autonome (HTML + CSS + JS,
sans dépendance externe). La page `index.html` les présente, regroupées par
catégorie, avec un aperçu live et leur code source prêt à copier.

## Structure

```
animations-gallery/
├── index.html              # galerie : catégories, recherche, pagination, aperçu et code
├── README.md
└── animations/             # une page autonome par animation
    ├── chantier-kpi-cards.html
    ├── engins-chantier.html
    ├── equipe-pointage.html
    ├── sous-traitants.html
    ├── rapport-journalier.html
    ├── order-confirm.html
    ├── like-button.html
    ├── ripple-button.html
    ├── toggle-switch.html
    ├── loading-spinner.html
    ├── skeleton-loader.html
    ├── progress-bar.html
    ├── toast-notification.html
    ├── hamburger-menu.html
    ├── flip-card.html
    ├── landing-hero.html
    ├── scroll-reveal.html
    ├── page-transition.html
    ├── parallax-scene.html
    ├── pricing-page.html
    └── login-page.html
```

## Animations

### Rapport de chantier

Écrans pour une application de rapport journalier (effectif, engins,
sous-traitants). Les données sont en tête de chaque script : remplacez-les par
celles de votre API.

| Fichier | Description |
| --- | --- |
| `chantier-kpi-cards.html` | Cartes « Effectif total du jour », « Engins mobilisés », « Sous-traitants » : bordure qui se dessine, compteurs, icônes vivantes (ouvrier qui travaille, engin qui roule avec poussière, poignée de main), barres d'objectif et mise à jour en direct (chiffre qui défile + badge « +1 »). |
| `engins-chantier.html` | Liste des engins dessinés en SVG et animés : pelleteuse qui creuse, bulldozer qui pousse la terre, camion benne qui roule puis vide sa benne, rouleau compacteur qui vibre. Compteur horaire en temps réel, jauge de carburant, états « En marche / En pause / En panne » (animation figée, fumée, alerte). |
| `equipe-pointage.html` | Équipe du jour : anneau de présence, onglets filtrants à pastille glissante, bouton « Pointer » avec coche animée, détection du retard et réorganisation fluide de la liste (animation FLIP). |
| `sous-traitants.html` | Cartes des entreprises sous-traitantes : pile d'avatars des intervenants, anneau d'avancement, accordéon des tâches du jour à cocher (l'anneau se met à jour). |
| `rapport-journalier.html` | Rapport complet : météo animée, chiffres clés, histogramme des heures, avancement des tâches, journal de la journée (ajout d'événements) et validation avec tampon « VALIDÉ » et signature qui se dessine. |

### Boutons & contrôles

| Fichier | Description |
| --- | --- |
| `order-confirm.html` | Bouton « Complete Order » : un camion traverse le bouton, dépose un colis, puis « Order Placed » s'affiche avec une coche animée (~10 s, relançable via la classe `.animate`). |
| `like-button.html` | Cœur qui se remplit de rouge avec un effet « pop », un anneau et une explosion de particules colorées. |
| `ripple-button.html` | Boutons avec onde « ripple » façon Material qui part du point de clic. |
| `toggle-switch.html` | Interrupteur on/off accessible (checkbox native) : le knob glisse avec un léger rebond et le fond passe au vert. |

### Chargement & feedback

| Fichier | Description |
| --- | --- |
| `loading-spinner.html` | Spinner circulaire en rotation continue, 100 % CSS. |
| `skeleton-loader.html` | Carte en squelette avec reflet « shimmer » pendant un chargement simulé, puis apparition en fondu du contenu. |
| `progress-bar.html` | Barre de progression rayée et animée simulant un envoi de fichier, avec pourcentage et état terminé. |
| `toast-notification.html` | Notification qui glisse depuis le bas de l'écran, avec barre de temps restant, et disparaît après 2,5 s. |

### Navigation & cartes

| Fichier | Description |
| --- | --- |
| `hamburger-menu.html` | Icône hamburger qui se transforme en croix et ouvre un menu déroulant aux liens échelonnés. |
| `flip-card.html` | Carte qui se retourne en 3D au survol (ou au toucher sur mobile) pour révéler son verso. |

### Pages complètes

| Fichier | Description |
| --- | --- |
| `landing-hero.html` | Page d'accueil : fond de blobs colorés flottants, titre qui apparaît mot par mot, mot en dégradé animé, halo qui suit la souris et compteurs. |
| `scroll-reveal.html` | Article long : les blocs apparaissent au défilement (fondu, glissement, zoom, balayage), compteurs animés et barre de progression de lecture. |
| `page-transition.html` | Mini-site de 3 pages : un rideau en bandes recouvre l'écran entre deux pages, la pastille du menu glisse et le contenu entre en cascade. |
| `parallax-scene.html` | Paysage de montagnes en couches qui bougent selon leur profondeur avec la souris et le défilement, étoiles scintillantes et nuages. |
| `pricing-page.html` | Page de tarifs : interrupteur mensuel/annuel avec prix qui défilent, cartes en cascade et bordure en dégradé tournante sur l'offre phare. |
| `login-page.html` | Page de connexion : vagues et bulles animées, labels flottants, secousse en cas d'erreur, bouton qui devient spinner puis coche. |

## Ajouter une nouvelle animation

1. Créez un fichier dans `animations/`, par exemple `animations/mon-effet.html`.
   C'est une page HTML complète et autonome : CSS dans `<style>`, JS dans
   `<script>`. Elle contient soit une seule micro-animation, soit une page
   complète animée.
2. Ajoutez une entrée au tableau `animations` en haut du script de
   `index.html` :

   ```js
   { name: 'Mon effet', file: 'mon-effet.html', category: 'Boutons & contrôles', tags: 'mots clés' },
   ```

   `category` doit être l'une des valeurs du tableau `categories` (juste
   au-dessus) ; pour créer une nouvelle catégorie, ajoutez-la simplement à ce
   tableau. Le champ `tags` est facultatif : ce sont des mots-clés supplémentaires
   utilisés par la recherche (par exemple `tags: 'bouton clic onde'`).
3. Ajoutez une ligne dans la bonne catégorie de la liste ci-dessus du README.

L'animation apparaît alors dans la barre latérale ; elle est aussi accessible
directement via `index.html#mon-effet.html`.

## Catégories, recherche et pagination

- Les animations sont regroupées par catégorie dans la barre latérale ; les
  boutons de filtre (Toutes, Rapport de chantier, Boutons & contrôles, …) limitent
  la liste à une catégorie.
- Le champ **Rechercher** filtre la liste par nom, nom de fichier, catégorie et mots-clés
  (`tags`). Il ignore les majuscules et les accents (« coeur » trouve « cœur »).
- Raccourcis clavier : `/` pour aller dans la recherche, `Entrée` pour ouvrir le
  premier résultat, `Échap` pour effacer.
- La liste est paginée (`PAGE_SIZE`, 8 par défaut, en haut du script de
  `index.html`). La page qui contient l'animation affichée est ouverte
  automatiquement.

## Lancer en local

Le code source est chargé avec `fetch()`, qui ne fonctionne pas lorsque la page
est ouverte directement depuis le disque (`file://`). Lancez un petit serveur
HTTP à la racine du projet :

```bash
python3 -m http.server 8000
```

puis ouvrez <http://localhost:8000>.

## Déploiement sur GitHub Pages

Le projet est 100 % statique et déployable tel quel sur GitHub Pages :

**Settings › Pages › Build and deployment › Source : _Deploy from a branch_ ›
Branch : `main` › dossier `/ (root)` › Save.**

Après quelques instants, la galerie est disponible à l'adresse
`https://<utilisateur>.github.io/<nom-du-repo>/`.
