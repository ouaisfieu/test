---
title: "Comparatif SEO : Just the Docs vs Minimal Mistakes"
permalink: /comparatif-seo-jtd-vs-mm/
date: 2025-07-15
last_modified_at: 2025-07-15
categories: ["Tutoriels", "SEO"]
tags: ["jekyll", "minimal-mistakes", "just-the-docs", "seo"]
author_profile: true
toc: true
excerpt: "Quelle solution Jekyll est la plus performante pour le référencement ? Analyse détaillée entre Just the Docs et Minimal Mistakes."
header:
  show_overlay_excerpt: false
  overlay_image: /assets/images/og.jpg
  overlay_filter: 0.25
  caption: "Photo : Unsplash — CC0"
  actions:
    - label: "Documentation officielle"
      url: "https://mmistakes.github.io/minimal-mistakes/"

---

> **Objectif :** aider les créateurs de sites Jekyll à choisir le thème le plus adapté à la *découvrabilité* : **Just the Docs** (JTD) ou **Minimal Mistakes** (MM).

## 1. Méthodologie

- Analyse des fonctionnalités natives : balises SEO, sitemap, Open Graph…  
- Tests Lighthouse (performance, accessibilité, bonnes pratiques SEO).  
- Facilité d’enrichissement pour un·e débutant·e.

## 2. Tableau comparatif

| Critère | Just the Docs | Minimal Mistakes |
|---------|--------------|------------------|
| Pensé pour le SEO | ❌ Basique | ✅ Oui |
| Métadonnées (`title`, `description`) | Manuelles | Auto + manuel |
| Balises Open Graph / Twitter Cards | ❌ Absent par défaut | ✅ Intégré |
| `jekyll-seo-tag` inclus | ⚠️ À ajouter | ✅ Oui |
| Sitemap & robots.txt | À ajouter | Générés |
| Breadcrumb / Fil d’Ariane | ❌ Non | ✅ Oui |
| Responsive Design | ✅ Oui | ✅ Oui |
| Personnalisation fine | Moyenne | Excellente |
| Performance brute | ⚡ Léger | ⚡⚡ Très optimisé |

## 3. Analyse détaillée

### 3.1 Just the Docs

- Orientation documentation interne.  
- Structure sidebar robuste, mais **pas d’automation SEO**.  
- Nécessite d’ajouter : `jekyll-seo-tag`, `jekyll-sitemap`, fichier `robots.txt`.

### 3.2 Minimal Mistakes

- Pensé pour blogs et sites publics.  
- Meta tags complètes, prise en charge des réseaux sociaux.  
- Plugins SEO déjà whitelisted pour GitHub Pages.

## 4. Recommandations

| Usage envisagé | Thème conseillé | Pourquoi |
|----------------|-----------------|----------|
| Wiki interne / docs privées | Just the Docs | Simplicité & sidebar puissante |
| Blog, portfolio, site associatif | Minimal Mistakes | SEO prêt à l’emploi, design flexible |

## 5. Checklist SEO rapide pour chaque thème

**Just the Docs**

- [ ] Ajouter à `_config.yml` : `jekyll-seo-tag`, `jekyll-sitemap`  
- [ ] Créer `robots.txt`, `sitemap.xml`  
- [ ] Renseigner `title` & `description` dans chaque page

**Minimal Mistakes**

- [x] Vérifier les balises OG (`og_image`)  
- [x] Compléter front‑matter : `last_modified_at`  
- [x] Soumettre `sitemap.xml` à Google Search Console

## 6. Conclusion

Pour un projet destiné au **grand public** (blogs, sites pédagogiques, documentation externe), **Minimal Mistakes** offre une longueur d’avance nette en SEO *out‑of‑the‑box*.  
Si votre priorité est la **légèreté** et la **navigation type wiki**, **Just the Docs** reste une option viable à condition d’ajouter les briques SEO manquantes.

---

*Article publié dans le cadre du site “Découvrabilité & Citoyenneté”.*
