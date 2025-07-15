---
layout: single
title: "Créer une collection « dossiers » pour vos cas d’étude citoyens"
date: 2025-07-15
last_modified_at: 2025-07-15
permalink: /creer-collection-dossiers/
categories: ["Tutoriels"]
tags: ["jekyll", "collections", "citoyenneté", "données-structurées"]
author_profile: true
toc: true
excerpt: "Étape par étape : ajoutez une collection personnalisée « dossiers » dans votre site Minimal Mistakes pour publier des cas d’étude structurés en YAML + Markdown."

header:
  show_overlay_excerpt: false
  overlay_image: /assets/images/og.jpg
  overlay_filter: 0.25
  caption: "Espace citoyen"
  actions:
    - label: "Documentation officielle"
      url: "https://mmistakes.github.io/minimal-mistakes/"

---

> **But :** transformer vos analyses citoyennes en fiches structurées, faciles à parcourir, exporter et réutiliser.

## 1. Pourquoi une collection ?

- **Organisation claire** : séparer les « dossiers » des articles de blog.  
- **Front‑matter adapté** : champs spécifiques (`theme`, `source_data`, `license`) sans polluer les posts.  
- **Endpoints JSON** : chaque dossier devient un nœud réutilisable (API légère).

---

## 2. Déclarer la collection dans `_config.yml`

```yaml
collections:
  dossiers:
    output: true          # génère des pages HTML
    permalink: /dossiers/:path/
```

> ✔️ `output: true` crée la page, `permalink` définit une URL stable `/dossiers/slug/`.

---

## 3. Créer le dossier physique

```
|_ dossiers/
   |_ _posts/      # (optionnel) si vous voulez la date
   |_ infrastructure-eau.md
   |_ open-data-stib.md
```

Minimal Mistakes détecte automatiquement `dossiers/`.

---

## 4. Modèle de front‑matter pour un dossier

```yaml
---
layout: single
collection: dossiers      # obligatoire
title: "Open Data STIB : potentiel citoyen"
permalink: /dossiers/stib-open-data/
theme: "Mobilité & Open Data"
source_data: "API STIB v1"
license: "CC BY 4.0"
toc: true
---
```

**Nouveaux champs** (`theme`, `source_data`, `license`) : libres ou imposés par ton besoin.

---

## 5. Navigation automatique

Ajoute un lien dans `_data/navigation.yml` :

```yaml
- title: "Dossiers"
  url: /dossiers/
```

La page index de la collection se crée toute seule si tu places un fichier `dossiers/index.md` minimal :

```markdown
---
layout: collection
title: "Dossiers citoyens"
permalink: /dossiers/
---
```

Le layout `collection` intégré à Minimal Mistakes liste les items.

---

## 6. Afficher des métadonnées supplémentaires

Crée un include Liquid `_includes/dossier-meta.html` :

```html
<ul class="dossier-meta">
  <li><strong>Thème :</strong> {{ page.theme }}</li>
  <li><strong>Donnée source :</strong> {{ page.source_data }}</li>
  <li><strong>Licence :</strong> {{ page.license }}</li>
</ul>
```

Puis, dans chaque dossier, insère où tu veux :

```liquid
{% include dossier-meta.html %}
```

---

## 7. Générer un endpoint JSON (optionnel)

Dans `dossiers/index.json` :

```liquid
---
layout: null
permalink: /dossiers.json
---
[
{% for dossier in site.dossiers %}
  {{ dossier | jsonify }}{% unless forloop.last %},{% endunless %}
{% endfor %}
]
```

> 🎯 Utilisable comme API simplifiée pour un widget externe (Appsmith, Dash, etc.).

---

## 8. Checklist avant de pousser

- [ ] `collections:` ajouté dans `_config.yml`  
- [ ] Dossier `dossiers/` créé et peuplé  
- [ ] Fichier `dossiers/index.md` (layout `collection`)  
- [ ] Liens navigation mis à jour  
- [ ] Build local (`bundle exec jekyll serve`) OK

---

## 9. Et après ?

- **Recherche dédiée** : activer Lunr.js sur `/dossiers/`.  
- **Filtres par thème** : paramètre URL `?theme=Mobilite`.  
- **Export CSV** : page Liquid qui parcourt `site.dossiers` et crache un fichier CSV.

Tu tiens désormais un mini‑réseau de connaissances prêt à l’open data !

