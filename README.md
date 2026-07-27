# Adel Malik Annabi — academic website

A small, dependency-free [Jekyll](https://jekyllrb.com) site (custom theme,
"Warm Amber") designed to be hosted for free on **GitHub Pages**. No build tools
required: GitHub compiles the Jekyll site automatically on every push.

## Pages

- **Home** (`index.md`) — name, title, research interests, short bio, and a card
  pointing to GitHub for code & numerical simulations.
- **Publications** (`publications.md`) — generated from `_data/publications.yml`.
- **CV** (`cv.md`) — education, teaching, skills + a "Download CV (PDF)" button.

## Deploy to GitHub Pages

You have two options.

### Option A — user site (nicest URL: `https://<username>.github.io`)
1. Create a GitHub repository named **exactly** `<username>.github.io`.
2. Copy the contents of this `website/` folder to the repository root.
3. Commit and push to the `main` branch.
4. Repo **Settings → Pages → Build and deployment → Deploy from a branch →
   `main` / `/ (root)`**. Your site is live in ~1–2 minutes.

### Option B — project site (URL: `https://<username>.github.io/<repo>`)
1. Create any repository (e.g. `annabi-website`) and push this folder to it.
2. In `_config.yml`, set `baseurl: "/<repo>"` (e.g. `baseurl: "/annabi-website"`).
3. Enable Pages as in step 4 above.

## Fill in your links later

Open `_config.yml` and paste your URLs. Empty values stay hidden automatically,
so links appear only once you add them:

```yaml
scholar: "https://scholar.google.com/citations?user=XXXXXXXX"
github: "https://github.com/your-username"
researchgate: "https://www.researchgate.net/profile/Your-Name"
```

`email` is already filled in.

## Add a publication

Append a block to `_data/publications.yml` (newest is sorted to the top by
`year`). Leave `links: []` if you have no URL yet.

## Update the CV PDF

Replace `assets/cv.pdf` with a new export of your CV (keep the same file name).

## Optional: preview locally

Requires Ruby + Bundler (on Windows, [RubyInstaller](https://rubyinstaller.org)):

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000
```
