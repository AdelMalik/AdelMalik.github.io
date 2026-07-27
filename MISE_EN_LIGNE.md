# Mettre le site en ligne — guide pas à pas

Deux temps, dans l'ordre :

- **Partie A — Voir le site EN PRIVÉ** (sur ton ordinateur, personne d'autre) → pour tester tranquillement.
- **Partie B — PUBLIER** (une adresse publique que tu partages sur tes articles, LinkedIn…).

> ⚠️ Point honnête à connaître : un site **« en ligne mais privé »** n'existe pas
> gratuitement sur GitHub Pages. « En privé » = **sur ta machine** (Partie A). Dès
> que tu publies (Partie B), le site est **public**. C'est le fonctionnement normal
> d'un site académique — l'adresse est publique mais personne ne la trouve tant que
> tu ne la partages pas.

> 🛑 Rappel essentiel : **ouvrir `index.md` ou un `.html` directement dans le
> navigateur ne montre RIEN de correct** (ni photo, ni mise en page). C'est Jekyll
> qui assemble le site. Pour voir le vrai rendu, il FAUT la Partie A ou la Partie B.

---

# PARTIE A — Voir le site en privé (sur ton ordinateur)

Le vrai test : tu construis le site chez toi et tu l'ouvres sur une adresse locale
`http://localhost:4000`. **Toi seul** le vois.

> ✅ **Déjà fait (24/07/2026) :** Ruby 3.3 + DevKit est **déjà installé** sur ta
> machine (`C:\Ruby33-x64`), et les outils (`bundle install`) sont déjà en place.
> **Tu peux sauter les étapes A.1, A.2 et A.3** et aller directement à **A.4**.
>
> ⚠️ Un seul détail : dans un terminal VS Code, si taper `ruby` répond « commande
> introuvable », **ferme et rouvre VS Code une fois** (le temps que Windows prenne
> en compte Ruby dans le PATH), puis réessaie. C'est à faire une seule fois.

## A.1 — Installer Ruby (une seule fois)

1. Va sur **https://rubyinstaller.org**.
2. Télécharge la version recommandée en gras : **« Ruby+Devkit »** (la plus récente,
   en x64).
3. Lance le fichier téléchargé, clique **Suivant / Next** partout, **Installer**.
4. À la toute fin, une case propose de lancer **`ridk install`** — laisse-la cochée,
   **Terminer**. Une fenêtre noire s'ouvre : appuie simplement sur **Entrée** (elle
   installe des composants). Attends que ça revienne à la ligne, puis ferme-la.

## A.2 — Ouvrir un terminal dans le dossier du site

Dans VS Code : menu **Terminal → Nouveau terminal**. Puis tape (copie-colle) :

```powershell
cd "c:\Perso\VSCODE WORKSPACE\website"
```

## A.3 — Préparer les outils (une seule fois)

```powershell
gem install bundler
bundle install
```

(Ça télécharge Jekyll. La première fois peut prendre 1–2 minutes.)

## A.4 — Lancer le site

```powershell
bundle exec jekyll serve
```

Laisse cette commande tourner. Ouvre ton navigateur sur :

**http://localhost:4000**

- Tant que la commande tourne, le site est visible **uniquement par toi**.
- Tu modifies un fichier, tu enregistres (**Ctrl+S**), tu **recharges la page** du
  navigateur → tu vois le changement.
- Pour **arrêter** : reviens dans le terminal et fais **Ctrl+C**.

> C'est ICI que tu vérifies que la photo s'affiche, que le nom est à la bonne
> taille, etc. — pas en ouvrant les fichiers à la main.

---

# PARTIE B — Publier (mettre en ligne, adresse publique)

Résultat : une adresse **`https://<ton-pseudo>.github.io`**, gratuite, qui se
reconstruit toute seule à chaque modification. On fait tout **sans ligne de
commande** grâce à **GitHub Desktop**.

## B.1 — Créer un compte GitHub (si tu n'en as pas)

1. Va sur **https://github.com** → **Sign up**.
2. Choisis un **pseudo (username)** avec soin : **il deviendra ton adresse web**
   (ex. pseudo `amannabi` → site `https://amannabi.github.io`).

## B.2 — Installer GitHub Desktop

1. Télécharge **https://desktop.github.com** → installe.
2. Ouvre-le → **Sign in to GitHub.com** → connecte-toi avec ton compte.

## B.3 — Transformer ton dossier en dépôt et le publier

Le plus simple : on publie **directement ton dossier actuel**, sans rien recopier.

1. Dans GitHub Desktop : menu **File → Add local repository…**
2. **Choose…** → sélectionne le dossier `c:\Perso\VSCODE WORKSPACE\website` → **Add**.
3. Il dira que ce n'est pas encore un dépôt Git et proposera **« create a
   repository »** → clique dessus → **Create repository**.
4. En haut, clique **Publish repository**. Une fenêtre s'ouvre :
   - **Name** : tape **exactement** `<ton-pseudo>.github.io`
     (ex. `amannabi.github.io`). ⚠️ C'est ce nom précis qui donne la belle adresse.
   - **Décoche** « Keep this code private » (Pages gratuit = public).
   - **Publish repository**.

## B.4 — Activer la publication (GitHub Pages)

1. Va sur **https://github.com**, ouvre ton dépôt `<pseudo>.github.io`.
2. Onglet **Settings** (en haut) → dans le menu de gauche, **Pages**.
3. Sous **Build and deployment → Source** : choisis **Deploy from a branch**.
4. **Branch** : `main`, dossier **/ (root)** → **Save**.
5. Attends **1 à 2 minutes**, recharge la page. Elle affiche :
   *« Your site is live at https://<pseudo></pseudo>.github.io »*. Clique — c'est en ligne ! ✅

## B.5 — Mettre à jour le site plus tard

À chaque fois que tu changes quelque chose (bio, CV, publication, photo…) :

1. Édite et enregistre tes fichiers (comme d'habitude).
2. Dans **GitHub Desktop** : en bas à gauche, écris un petit message (ex.
   « maj bio ») → **Commit to main** → en haut, **Push origin**.
3. Le site public se reconstruit tout seul en **1–2 minutes**.

C'est tout. Plus jamais de ligne de commande pour publier.

---

## Récapitulatif express

| Je veux…                       | Je fais…                                                             |
| ------------------------------- | --------------------------------------------------------------------- |
| Voir le site en privé (test)   | Terminal →`bundle exec jekyll serve` → `http://localhost:4000`  |
| Publier la 1re fois             | GitHub Desktop : Add local repository → Publish → Settings → Pages |
| Mettre à jour après une modif | GitHub Desktop :**Commit to main** puis **Push origin**   |

> Astuce photo : `profile.jpg` fait ~0,9 Mo, c'est bon pour le web. Si un jour tu
> veux qu'elle charge encore plus vite, réduis-la à ~800 px de large avant de la
> déposer dans `assets/img/`.
