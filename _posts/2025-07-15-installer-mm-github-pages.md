---
title: "Installer Minimal Mistakes et deployer sur GitHub Pages en 10 minutes"
date: 2025-07-15
last_modified_at: 2025-07-15
categories: ["Tutoriels"]
tags: ["jekyll", "minimal-mistakes", "github-pages", "seo", "beginner"]
author_profile: true
toc: true

header:
  show_overlay_excerpt: false
  overlay_image: /assets/images/og.jpg
  overlay_filter: 0.25
  caption: "Photo : Unsplash — CC0"
  actions:
    - label: "Voir le dépôt starter"
      url: "https://github.com/mmistakes/mm-github-pages-starter"
    - label: "Documentation officielle"
      url: "https://mmistakes.github.io/minimal-mistakes/"

---

> Objectif : obtenir un site fonctionnel avec le thème Minimal Mistakes, hébergé gratuitement sur GitHub Pages – sans Ruby local, sans ligne de commande complexe. Comptez environ **10 minutes**, café compris.

## 1. Prérequis ultra-light

| Outil | Pourquoi | Lien |
|-------|----------|------|
| Compte GitHub | Hébergement + actions intégrées | https://github.com |
| Navigateur | Tout se fait en ligne | – |
| (Optionnel) VS Code + extension GitHub | Retouches locales confort | – |

## 2. Créer le dépôt en un clic

1. Ouvre le repo starter : https://github.com/mmistakes/mm-github-pages-starter  
2. Clique sur **Use this template → Create a new repository**  
3. Nomme ton dépôt (par exemple `citoyennete-mm-site`)  
4. Choisis **Public** pour GitHub Pages gratuit  
5. Clique **Create repository**

GitHub clone alors le thème avec la config et un contenu de démonstration.

## 3. Modifier `_config.yml`

```yaml
url: "https://ton-pseudo.github.io"
baseurl: "/citoyennete-mm-site"  # mettre "" si le site est à la racine
title: "Découvrabilité & Citoyenneté"
description: "Tutoriel et articles pédagogiques construits avec Minimal Mistakes"
remote_theme: "mmistakes/minimal-mistakes@4.27.1"
```

## 4. Activer GitHub Pages

1. Va dans **Settings → Pages** de ton dépôt  
2. Source : **Deploy from a branch** et sélectionne `main`  
3. Patiente une minute : ton site apparaît à `https://ton-pseudo.github.io/citoyennete-mm-site/`

🎉 C’est en ligne !

## 5. Personnaliser la page d’accueil

- Édite `index.md`  
- Mets le menu à jour dans `_data/navigation.yml`  
- Ajoute ta bio dans `_data/authors.yml`

## 6. Bonnes pratiques SEO immédiates

1. Vérifie la présence de `jekyll-seo-tag` dans `_config.yml`  
2. Ajoute `title`, `description` et `last_modified_at` dans chaque front‑matter  
3. Laisse GitHub générer `sitemap.xml` et `feed.xml`  
4. Place `/assets/images/og.jpg` (1200 × 630 px, ≤ 500 Ko) et référence‑le :

```yaml
seo:
  og_image: /assets/images/og.jpg
```

## 7. (Facultatif) Développer localement

```bash
gem install bundler
git clone https://github.com/ton-pseudo/citoyennete-mm-site.git
cd citoyennete-mm-site
bundle install
bundle exec jekyll serve
```

Puis visite http://localhost:4000.

## 8. FAQ express

| Question | Réponse |
|----------|---------|
| Nom de domaine personnalisé ? | Oui, via Settings → Pages → Custom domain |
| `Gemfile.lock` obligatoire ? | Oui pour un développement local ; ignoré en production |
| Mettre à jour le thème ? | Change la version dans `remote_theme:` puis `git push` |

## 9. Aller plus loin

Passe au tutoriel suivant pour créer une collection dédiée, styliser ta palette, et activer la recherche interne.
