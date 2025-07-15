---
layout: collection
title: "Dossiers citoyens"
permalink: /dossiers/
toc: false
---

<p class="notice--primary">Filtrer les dossiers par thème :</p>

<select id="theme-filter">
  <option value="all">Tous les thèmes</option>
  {% assign themes = site.dossiers | map: "theme" | uniq | sort %}
  {% for th in themes %}
    {% if th %}
      <option value="{{ th | slugify }}">{{ th }}</option>
    {% endif %}
  {% endfor %}
</select>

<div id="dossier-list">
  {% for dossier in site.dossiers %}
    <article class="dossier-item" data-theme="{{ dossier.theme | slugify }}">
      <h2><a href="{{ dossier.url | relative_url }}">{{ dossier.title }}</a></h2>
      {% if dossier.theme %}<p><em>{{ dossier.theme }}</em></p>{% endif %}
      {{ dossier.excerpt }}
    </article>
  {% endfor %}
</div>

<script>
(function() {
  const select = document.getElementById('theme-filter');
  const items = document.querySelectorAll('.dossier-item');

  function filter() {
    const val = select.value;
    items.forEach(it => {
      if (val === 'all' || it.dataset.theme === val) {
        it.style.display = '';
      } else {
        it.style.display = 'none';
      }
    });
  }
  select.addEventListener('change', filter);
})();
</script>
