# 👤 avatar.jpg → image de profil auteur
📐 Dimensions recommandées
Taille recommandée : 400 x 400 px

Format carré obligatoire

S’affiche en petit dans la sidebar ou les articles → inutile d’aller au-delà de 500 px

Poids : idéalement < 100 Ko

# 🖼️ og.jpg → image Open Graph (réseaux sociaux, SEO)
📐 Dimensions idéales
Plateforme	Taille recommandée	Ratio
Facebook / LinkedIn	1200 x 630 px	1.91:1
Twitter (carte large)	1200 x 675 px	~16:9

✅ Conseils
1200 px de large minimum, sinon les images seront floues ou mal affichées.

Format : .jpg ou .png, pas de WebP (pas toujours pris en charge).

Poids : max 300–500 Ko pour un bon compromis qualité/vitesse (utilise TinyJPG ou Squoosh).

Pas de texte trop petit : les miniatures réduisent énormément l’image.


Voici un guide clair pour t’expliquer les différences entre header, hero, et comment les intégrer dans Minimal Mistakes, avec dimensions et bonnes pratiques.

🧱 Les différents types d’images
Type d’image	Rôle principal	Affichage dans Minimal Mistakes
og.jpg	Partage sur réseaux sociaux	Invisible sur le site, mais visible sur Facebook etc.
avatar.jpg	Profil auteur (sidebar ou article)	Petit format, image carrée
Hero image	Image d’en-tête d’un article ou d’une page	Visible en haut de l’article (layout single)
Site header	Image fixe visible sur toutes les pages	En haut du site via la config _config.yml

🖼️ 1. Hero image (image par article/page)
Objectif :
Attirer visuellement sur une page ou un article particulier.

Exemple dans un article :

```markdown
---
layout: single
title: "Exemple d’article avec image"
header:
  overlay_image: /assets/images/header-exemple.jpg
  overlay_filter: 0.3 # floute ou assombrit
  caption: "Image par Nom / Source"
  actions:
    - label: "Lire la suite"
      url: "/autre-page/"
---
```

📐 Dimensions recommandées :
1500 x 600 px ou plus

Ratio : ~16:9 ou plus panoramique

Poids : max 400-600 Ko

🧱 2. Image de header global (fixe pour tout le site)
Tu peux définir une image de fond d’en-tête pour tout ton site dans _config.yml :

```yaml
header:
  image: "/assets/images/header-site.jpg"
```

Elle s’affichera sur la home page avec layout: home, et sur les pages si tu ne mets pas de layout: single.

⚠️ Attention :
Ce header global est désactivé par défaut dans Minimal Mistakes.

Pour qu’il s’affiche joliment, il faut personnaliser un peu le layout home.

🖌️ Style : overlay_image + overlay_filter
Le duo magique de Minimal Mistakes.

```yaml

header:
  overlay_image: /assets/images/hero.jpg
  overlay_filter: 0.2


```

overlay_image → image à afficher

overlay_filter → couche semi-transparente noire (0.0 = aucune, 1.0 = tout noir)

Tu peux aussi ajouter un title, subtitle, caption, et des boutons d’action (actions:).

📁 Où mettre les images ?
Toutes tes images peuvent aller dans :


```css
assets/
└── images/
    ├── og.jpg
    ├── avatar.jpg
    ├── header-site.jpg
    └── hero-article-1.jpg


```

Tu y accèdes ensuite dans le front-matter ou config avec :

```yaml
/assets/images/nom-image.jpg

```


