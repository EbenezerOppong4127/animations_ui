# animations-gallery

Galerie statique de micro-animations UI. Chaque animation est une page HTML
autonome (HTML + CSS + JS, sans dépendance externe) ; la page `index.html` les
présente avec un aperçu live et leur code source, prêt à copier.

## Structure

```
animations-gallery/
├── index.html              # galerie : liste, aperçu (iframe) et code source
├── README.md
└── animations/             # une page autonome par animation
    ├── order-confirm.html
    ├── like-button.html
    ├── toggle-switch.html
    ├── loading-spinner.html
    ├── toast-notification.html
    ├── skeleton-loader.html
    ├── flip-card.html
    ├── ripple-button.html
    ├── progress-bar.html
    └── hamburger-menu.html
```

## Animations

| Fichier | Description |
| --- | --- |
| `order-confirm.html` | Bouton « Complete Order » : un camion traverse le bouton, dépose un colis, puis « Order Placed » s'affiche avec une coche animée (~10 s, relançable via la classe `.animate`). |
| `like-button.html` | Cœur qui se remplit de rouge avec un effet « pop », un anneau et une explosion de particules colorées. |
| `toggle-switch.html` | Interrupteur on/off accessible (checkbox native) : le knob glisse avec un léger rebond et le fond passe au vert. |
| `loading-spinner.html` | Spinner circulaire en rotation continue, 100 % CSS. |
| `toast-notification.html` | Notification qui glisse depuis le bas de l'écran, avec barre de temps restant, et disparaît après 2,5 s. |
| `skeleton-loader.html` | Carte en squelette avec reflet « shimmer » pendant un chargement simulé, puis apparition en fondu du contenu. |
| `flip-card.html` | Carte qui se retourne en 3D au survol (ou au toucher sur mobile) pour révéler son verso. |
| `ripple-button.html` | Boutons avec onde « ripple » façon Material qui part du point de clic. |
| `progress-bar.html` | Barre de progression rayée et animée simulant un envoi de fichier, avec pourcentage et état terminé. |
| `hamburger-menu.html` | Icône hamburger qui se transforme en croix et ouvre un menu déroulant aux liens échelonnés. |

## Ajouter une nouvelle animation

1. Créez un fichier dans `animations/`, par exemple `animations/mon-effet.html`.
   C'est une page HTML complète et autonome : CSS dans `<style>`, JS dans
   `<script>`, une seule micro-animation, centrée dans la page.
2. Ajoutez une entrée au tableau `animations` en haut du script de
   `index.html` :

   ```js
   { name: 'Mon effet', file: 'mon-effet.html', tags: 'mots clés' },
   ```

   Le champ `tags` est facultatif : ce sont des mots-clés supplémentaires
   utilisés par la recherche (par exemple `tags: 'bouton clic onde'`).
3. Ajoutez une ligne dans le tableau ci-dessus du README.

L'animation apparaît alors dans la barre latérale ; elle est aussi accessible
directement via `index.html#mon-effet.html`.

## Recherche et pagination

- Le champ **Rechercher** filtre la liste par nom, nom de fichier et mots-clés
  (`tags`). Il ignore les majuscules et les accents (« coeur » trouve « cœur »).
- Raccourcis clavier : `/` pour aller dans la recherche, `Entrée` pour ouvrir le
  premier résultat, `Échap` pour effacer.
- La liste est paginée (`PAGE_SIZE`, 6 par défaut, en haut du script de
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
