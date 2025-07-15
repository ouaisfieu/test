---
layout: single
title: "Front‑matter en profondeur : le cœur invisible d’un bon référencement"
date: 2025-07-15
last_modified_at: 2025-07-15
permalink: /front-matter-referencement/
categories: ["Tutoriels", "SEO"]
tags: ["front-matter", "jekyll", "seo", "metadata"]
author_profile: true
toc: true
excerpt: "Découvre comment quelques lignes de front‑matter optimisent la visibilité, la lisibilité et le partage de tes articles Minimal Mistakes."
header:
  show_overlay_excerpt: false
  overlay_image: /assets/images/og.jpg
  overlay_filter: 0.25
  caption: "Espace citoyen"
  actions:
    - label: "Documentation officielle"
      url: "https://mmistakes.github.io/minimal-mistakes/"

---

> Un bon front‑matter, c’est l’ADN de ta page : moteurs de recherche, réseaux sociaux et lecteurs humains s’y retrouvent… ou pas.

## 1. Pourquoi s’en préoccuper ?

- **SEO** : Google lit d’abord tes balises `title` et `description`.  
- **Partage social** : Open Graph/Twitter Cards utilisent `image`, `excerpt`.  
- **Ergonomie** : Minimal Mistakes gère le temps de lecture (`read_time`), le héros (`header:`), la sidebar, etc.

**Moralité :** Pas de front‑matter → pas de stratégie de découvrabilité.

---

## 2. Clés obligatoires

| Clé | Longueur conseillée | Rôle |
|-----|--------------------|------|
| `title` | ≤ 60 car. | Titre SEO & barre du navigateur |
| `description` | 120‑160 car. | Snippet SERP & réseaux |
| `permalink` | slug clair | URL stable (évite /categories/….) |
| `date` | ISO 8601 | Chronologie, RSS, JSON‑Feed |
| `last_modified_at` | ISO 8601 | Signale les mises à jour à Google |

```yaml
title: "Carte blanche : la STIB en Open Data"
description: "Analyse des données temps réel STIB pour une mobilité citoyenne."
permalink: /stib-open-data/
date: 2025-08-01
last_modified_at: 2025-08-03
```

---

## 3. Métadonnées sociales

```yaml
image: /assets/images/stib-dashboard.jpg   # miniature OG
excerpt: "Une plongée dans les API STIB pour démocratiser l'info transport."
share: true       # Active les icônes de partage MM
```

| Champs clés | Pour quoi ? |
|-------------|------------|
| `image` | Facebook, LinkedIn, Twitter (1200 × 630 px) |
| `excerpt` | Résumé court sous le titre / dans les cartes |
| `share` | Boutons de partage en fin d’article |

---

## 4. Options Minimal Mistakes utiles

| Clé | Effet |
|-----|-------|
| `header:` | Hero par‑page (`overlay_image`, `overlay_filter`, `actions:`) |
| `read_time: false` | Masque l’estimation de lecture |
| `related: false` | Désactive les billets similaires |
| `classes: wide` | Largeur pleine page |

```yaml
header:
  overlay_image: /assets/images/hero-stib.jpg
  overlay_filter: 0.3
classes: wide
read_time: false
```

---

## 5. Modèles prêts à copier

### 5.1 Article d’analyse longue

```yaml
layout: single
title: "Analyse longue"
permalink: /analyse-longue/
categories: ["Analyse"]
tags: ["longread", "belgique"]
toc: true
related: true
```

### 5.2 Fiche outil

```yaml
layout: single
title: "Outil — GeoJSONLint"
permalink: /outils/geojsonlint/
categories: ["Outils"]
tags: ["geojson", "validation"]
description: "Valide vos fichiers GeoJSON en un clic."
header:
  overlay_filter: 0.15
```

---

## 6. Tester son front‑matter

1. **Local** : `bundle exec jekyll build` → avertissements.  
2. **GitHub Actions** : l’étape `pages/build` échoue si front‑matter mal formé.  
3. **Lighthouse SEO** : vérifie balises manquantes.  
4. **`jekyll doctor`** : repère dates invalides, titres vides.

---

## 7. Checklist rapide avant `git push`

- [ ] Titre & description uniques  
- [ ] `permalink` sans majuscules ni espaces  
- [ ] `last_modified_at` mis à jour  
- [ ] Image OG compressée (< 500 Ko)  
- [ ] Aucune balise YAML vide ou en double

---

## 8. Vers la suite

Prochain niveau : **créer ta collection `dossiers`** pour publier des cas d’étude citoyens structurés (YAML + Markdown). Reste branché !
