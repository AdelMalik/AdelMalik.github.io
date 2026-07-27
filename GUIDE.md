# Guide d'édition du site

Le site est un site **Jekyll**. Vous modifiez des fichiers texte, vous poussez sur
GitHub, et le site se met à jour tout seul. Aucun logiciel à installer pour éditer.

Dossier du site : `c:\Perso\VSCODE WORKSPACE\website\`

---

## 1. Quel fichier contrôle quoi ?

| Ce que vous voulez changer            | Fichier à ouvrir                         |
|---------------------------------------|------------------------------------------|
| Nom (accueil)                         | `_layouts/home.html`                     |
| Présentation / bio sous le nom        | `index.md`                               |
| Adresse email affichée                | `_config.yml` → `email`                  |
| Centres d'intérêt (les pastilles)     | `_config.yml` → `research_interests`     |
| Photo (quelle image)                  | `_config.yml` → `photo`                  |
| **Taille / forme de la photo**        | `_sass/_theme.scss` → `.hero-photo`      |
| Liens Scholar / GitHub…               | `_config.yml`                            |
| Publications (ajouter / modifier)     | `_data/publications.yml`                 |
| Texte de la page « Code »             | `code.md`                                |
| Texte du CV (formations, TD, skills)  | `cv.md`                                  |
| Fichier CV téléchargeable (PDF)       | `assets/cv.pdf` (remplacez le fichier)   |
| Couleurs                              | `_sass/_theme.scss` → bloc `:root`       |
| Taille du texte                       | `_sass/_theme.scss` → `body { font-size }` |
| Barre de navigation (Home, Publications…) | `_includes/sidebar.html`             |

---

## 2. Modifier, supprimer ou ajouter du texte (le principe de base)

Tout le site est fait de **fichiers texte**. Pour changer un mot, une phrase ou
tout un paragraphe, le geste est **toujours le même** :

1. Ouvrir le bon fichier (tableau de la section 1).
2. Trouver le texte à l'écran (**Ctrl+F** dans l'éditeur pour le chercher).
3. Le modifier, le supprimer ou en ajouter.
4. Enregistrer (**Ctrl+S**), puis pousser sur GitHub (section 12).

### Deux sortes de fichiers

- Les fichiers **`.md`** (comme `index.md`) : du texte presque normal, vous écrivez
  directement. `*mot*` = *italique*, `**mot**` = **gras**.
- Les fichiers **`.html`** et **`.yml`** (comme `cv.md`, `code.md`, `_config.yml`) : le
  texte est entouré de **balises** `<...>` ou de lignes `{% ... %}`. **Ne touchez
  qu'au texte lisible**, laissez les balises telles quelles.

> Règle d'or : quand vous voyez une paire comme `<p>` … `</p>` ou `<h3>` … `</h3>`,
> ce sont une balise **ouvrante** et sa **fermante**. Gardez toujours les deux, et
> ne modifiez que le texte **au milieu**.

### Supprimer une ligne / une phrase

Effacez la **ligne entière**. Exemple sur la page CV (`cv.md`), pour retirer le
bloc « Teaching Assistant… », on supprime tout, de `<p>` jusqu'à `</p>` :

```html
<p>Teaching Assistant — Mathematics (96 hours), Laboratoire Jean Alexandre
Dieudonné, Université Côte d'Azur.</p>
```

### Modifier un mot ou un chiffre

Cherchez le texte (Ctrl+F) et remplacez-le. Exemple : dans `cv.md`, changer le
volume de TD → remplacez `96 hours` par `120 hours`. On ne touche pas aux `<p>`
autour, seulement au texte.

### Ajouter du texte

Copiez une ligne voisine et adaptez-la. Exemple, ajouter une précision sous une
expérience du CV : à l'intérieur du bloc `<div class="tl-body"> … </div>`, ajoutez
une ligne sous les autres :

```html
<p>Une phrase supplémentaire à afficher.</p>
```

### Où se trouve le texte de chaque page

| Page                              | Fichier                                    |
|-----------------------------------|--------------------------------------------|
| Accueil (bio sous le nom)         | `index.md` (voir section 5)                |
| CV (formations, TD, compétences)  | `cv.md`                                    |
| Code                              | `code.md`                                  |
| Publications                      | `_data/publications.yml` (voir section 6)  |

---

## 3. Changer la photo

**a) Mettre votre image :** déposez votre fichier dans `assets/img/`
(ex. `profile.jpg`), puis dans `_config.yml` :

```yaml
photo: "/assets/img/profile.jpg"
```

Pour **enlever** la photo : `photo: ""` (l'emplacement disparaît).

**b) Changer la taille :** ouvrez `_sass/_theme.scss`, cherchez `.hero-photo` :

```css
.hero-photo {
  width: 220px;    /* largeur — augmentez/diminuez */
  height: 260px;   /* hauteur */
  ...
}
```

- Plus grande : `width: 260px; height: 310px;`
- Plus petite : `width: 180px; height: 215px;`

**c) Photo ronde** au lieu d'un carré arrondi : mettez la **même** largeur et
hauteur, et un rayon de 50 % :

```css
.hero-photo { width: 220px; height: 220px; border-radius: 50%; ... }
```

> Il y a aussi une version pour mobile un peu plus bas dans le fichier
> (`@media (max-width: 620px) { .hero-photo { width: 168px; height: 198px; } }`) —
> ajustez-la de la même manière si besoin.

---

## 4. Changer le nom (accueil)

Ouvrez `_layouts/home.html`, cette ligne :

```html
<h1 class="hero-name">Adel Malik Annabi</h1>
```

(Le nom apparaît aussi en haut de la barre de navigation à gauche
`_includes/sidebar.html` — pensez à le changer là aussi si vous modifiez votre nom.)

---

## 5. Changer la présentation sous le nom (bio)

Le petit paragraphe affiché **directement sous votre nom** se trouve dans
`index.md`. Ouvrez le fichier et modifiez le texte sous la ligne `---`. C'est du
Markdown simple : `*mot*` = italique, `**mot**` = gras. C'est là qu'on écrit le
titre de thèse, la date de soutenance, le laboratoire et les encadrants.

---

## 6. Ajouter / modifier une publication

Ouvrez `_data/publications.yml`. Copiez un bloc et adaptez-le (le plus récent
remonte automatiquement en haut, tri par `year`) :

```yaml
- title: "Titre de l'article"
  authors: "Adel Malik Annabi, Co-auteur 1, Co-auteur 2"
  venue: "Nom de la conférence ou du journal"
  year: 2027
  type: "Publication"       # ou "Preprint"
  links:
    - name: "arXiv"
      url: "https://arxiv.org/abs/…"
    # laissez « links: [] » s'il n'y a pas de lien
```

Votre nom se met automatiquement en gras dans la liste.

---

## 7. Afficher les liens Scholar / GitHub / ResearchGate

Dans `_config.yml`, remplissez les URLs (un champ vide reste caché) :

```yaml
scholar: "https://scholar.google.com/citations?user=XXXX"
github: "https://github.com/votre-user"
researchgate: "https://www.researchgate.net/profile/Votre-Nom"
```

Dès qu'un lien est rempli, il apparaît. Le champ `github` active aussi le bouton
de la page **Code**.

---

## 8. Changer les couleurs

Ouvrez `_sass/_theme.scss`, bloc `:root` tout en haut. La couleur principale :

```css
--accent:        #E07B39;   /* orange principal (pastilles, menu actif, focus) */
--accent-deep:   #A9501E;   /* orange foncé (liens, boutons) */
--accent-darker: #8A3F16;   /* survol des boutons */
--bg:            #FAF6EF;   /* fond de page */
--ink:           #221E1A;   /* couleur du texte */
```

Changez le code hexadécimal (`#......`) pour une autre teinte.

---

## 9. Changer la taille générale du texte

Dans `_sass/_theme.scss`, cherchez `body { … font-size: 16.5px; … }`.
Augmentez (17.5px) ou diminuez (15.5px). Les titres se règlent juste en dessous
(`.hero-name`, `.section h2`, `.page-title`, etc.).

---

## 10. Remplacer le CV PDF

Exportez votre CV en PDF, nommez-le `cv.pdf`, et remplacez le fichier
`assets/cv.pdf`. Le bouton « Download CV (PDF) » pointera vers la nouvelle version.

---

## 11. Simuler / prévisualiser le site

**Le plus simple (sans rien installer)** : poussez sur GitHub et regardez le site
en ligne (il se reconstruit en 1–2 min). Voir la section 12.

**En local, avec Ruby** (si vous voulez tester avant de pousser) :

1. Installez Ruby : https://rubyinstaller.org (choisir « Ruby+Devkit »).
2. Une seule fois, dans le dossier `website/` :
   ```bash
   gem install bundler
   bundle install
   ```
3. À chaque fois que vous voulez prévisualiser :
   ```bash
   bundle exec jekyll serve
   ```
   Puis ouvrez http://localhost:4000 dans votre navigateur. La page se met à jour
   quand vous enregistrez un fichier (rechargez l'onglet).

> Note : ouvrir `index.md` ou les `.html` directement dans le navigateur ne marche
> pas — c'est Jekyll qui assemble les pages. Il faut soit la commande ci-dessus,
> soit GitHub Pages.

## 12. Mettre en ligne (rappel)

Après vos modifications : `git add . && git commit -m "maj" && git push`.
GitHub reconstruit le site en 1–2 minutes. (Voir `README.md` pour la première
mise en place.)
