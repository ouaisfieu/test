---
layout: collection
title: "Dossiers citoyens"
permalink: /dossiers/
toc: false
---

<p class="notice--primary">Filtrer les dossiers par&nbsp;thème :</p>

{::nomarkdown}
{% comment %}Construire la liste unique des thèmes, qu’ils soient dans `theme:` ou `themes:`{% endcomment %}
{% capture raw_themes %}{% endcapture %}
{% for d in site.dossiers %}
  {% if d.themes %}
    {% for t in d.themes %}
      {% assign raw_themes = raw_themes | append: t | append: "|" %}
    {% endfor %}
  {% elsif d.theme %}
    {% assign raw_themes = raw_themes | append: d.theme | append: "|" %}
  {% endif %}
{% endfor %}
{% assign theme_array = raw_themes | split: "|" | uniq | sort %}

<select id="theme-filter">
  <option value="all">Tous les thèmes</option>
  {% for th in theme_array %}
    {% if th != "" %}
      <option value="{{ th | slugify }}">{{ th }}</option>
    {% endif %}
  {% endfor %}
</select>
{:/nomarkdown}

<div id="dossier-list">
  {% for d in site.dossiers %}
    {% comment %}Construire l'attribut data-theme en concaténant les slugs séparés par espace{% endcomment %}
    {% capture slugs %}{% endcapture %}
    {% if d.themes %}
      {% for t in d.themes %}
        {% capture slugs %}{{ slugs }}{{ t | slugify }} {% endcapture %}
      {% endfor %}
    {% elsif d.theme %}
      {% capture slugs %}{{ d.theme | slugify }}{% endcapture %}
    {% endif %}
    <article class="dossier-item" data-theme="{{ slugs | strip }}">
      <h2><a href="{{ d.url | relative_url }}">{{ d.title }}</a></h2>
      {% if d.themes %}
        <p><em>{{ d.themes | join: ", " }}</em></p>
      {% elsif d.theme %}
        <p><em>{{ d.theme }}</em></p>
      {% endif %}
      {{ d.excerpt }}
    </article>
  {% endfor %}
</div>

<script>
(function () {
  const select = document.getElementById('theme-filter');
  const items  = document.querySelectorAll('.dossier-item');

  function applyFilter() {
    const val = select.value;
    items.forEach(it => {
      const arr = it.dataset.theme.split(' ');
      it.style.display = (val === 'all' || arr.includes(val)) ? '' : 'none';
    });
  }
  select.addEventListener('change', applyFilter);
  applyFilter(); // initial load
})();
</script>
