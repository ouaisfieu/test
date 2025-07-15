---
layout: single
title: "Personnaliser l’apparence : couleurs, typo et mises en page sous Minimal Mistakes"
date: 2025-07-15
last_modified_at: 2025-07-15
permalink: /personnalisation-apparence-mm/
categories: ["Tutoriels", "Design"]
tags: ["design", "scss", "minimal-mistakes", "palette", "typography"]
author_profile: true
toc: true
excerpt: "Un guide étape par étape pour donner à votre site Minimal Mistakes une identité visuelle unique : palette vert/lilas, police personnalisée, tuiles colorées et mises en page étendues."
header:
  show_overlay_excerpt: false
  overlay_image: /assets/images/og.jpg
  overlay_filter: 0.25
  caption: "Espace citoyen"
  actions:
    - label: "Documentation officielle"
      url: "https://mmistakes.github.io/minimal-mistakes/"

---

> **Objectif :** transformer l’apparence par défaut de Minimal Mistakes en une identité cohérente avec vos couleurs, votre typo et quelques touches CSS.

---

## 1. Principe général

1. **Surcharger SCSS** via `assets/css/_custom.scss` (ou `custom.scss` en racine `assets/css/`)  
2. Ajouter, au besoin, un `head/custom.html` pour importer des polices externes  
3. Ajuster le layout avec les classes utilitaires déjà fournies (`classes: wide`, `image-feature`)  
4. Garder la compatibilité GitHub Pages (pas de plugins Ruby additionnels)

---

## 2. Créer ou activer le fichier SCSS  
Dans `assets/css/` ajoute :

```scss
/* _custom.scss */
// Palette vert & lilas
$body-link-color: #6b5b95;
$primary-color:    #88b04b;
$masthead-background: #ffffff;

// Titres en Police Google 'Inter'
$global-font-family: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI",
                     Roboto, "Helvetica Neue", Arial, sans-serif;

// Accent infos (ex. notice)
.notice--primary {
  background: mix($primary-color, #fff, 15%);
  border-left: 4px solid $primary-color;
}
```

Minimal Mistakes compile automatiquement ce fichier pendant le build GitHub Pages car il l’inclut dans `main.scss`.

---

## 3. Importer une police Google (optionnel)

1. Crée `_includes/head/custom.html`  
2. Colle :

```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
```

3. `git add _includes/head/custom.html`

Votre `$global-font-family` pointera vers *Inter* (déjà défini dans SCSS).

---

## 4. Étendre la largeur de certaines pages

Dans un front‑matter :

```yaml
classes: wide
```

ou full‑width (aucune marge) :

```yaml
classes: full
```

Idéal pour des dashboards ou images larges.

---

## 5. Boutons personnalisés

```scss
.btn--citoyen {
  @extend .btn;
  background: $primary-color;
  &:hover { background: darken($primary-color, 7%); }
}
```

Puis dans un article :

```html
<a href="/dossiers/" class="btn btn--citoyen">Voir les dossiers</a>
```

---

## 6. Exemple complet

> Demo : `/assets/images/og.jpg` comme hero verdâtre + classes `wide`.  
> Essayez sur la page “Découvrabilité & Citoyenneté”.

```yaml
header:
  overlay_image: /assets/images/hero-demo.jpg
  overlay_filter: 0.2
classes: wide
```

---

## 7. Checklist avant push

- [ ] `assets/css/_custom.scss` présent  
- [ ] Pas d’erreur de compil Sass (`bundle exec jekyll build` local)  
- [ ] `_includes/head/custom.html` si police externe  
- [ ] `og_image` rafraîchi pour vos réseaux

Tout prêt ? **Commit + push** puis admirez votre nouveau style !

---

## 8. Aller plus loin

* Icônes : `@lucide-icons` en SVG inline  
* Mode sombre : surcharge `$body-background-color--dark`  
* Micro‑animations : ajouter `@keyframes` dans `_custom.scss`.

_Faites‑vous plaisir, l’esthétique aussi est un acte citoyen._ 
