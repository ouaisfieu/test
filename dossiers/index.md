---
layout: collection
title: "Dossiers citoyens"
permalink: /dossiers/
toc: false
---

<p class="notice--primary">Filtrer les dossiers par thème :</p>

{::nomarkdown}
{% comment %} Liste unique des thèmes (acceptant theme: ou themes: []) {% endcomment %}
{% capture theme_list %}{% endcapture %}
{% for dossier in site.dossiers %}
  {% if dossier.themes %}
    {% for t in dossier.themes %}
      {% assign theme_list = theme_list | append: t | append: "|" %}
    {% endfor %}
  {% elsif dossier.theme %}
    {% assign theme_list = theme_list | append: dossier.theme | append: "|" %}
  {% endif %}
{% endfor %}
{% assign themes = theme_list | split: "|" | uniq | sort %}

<select id="theme-filter">
  <option value="all">Tous les thèmes</option>
  {% for th in themes %}
    {% if th != "" %}
      <option value="{{ th | slugify }}">{{ th }}</option>
    {% endif %}
  {% endfor %}
</select>
{:/nomarkdown}

<div id="dossier-list">
  {% for dossier in site.dossiers %}
    {% capture sluglist %}{% endcapture %}
    {% if dossier.themes %}
      {% for t in dossier.themes %}
        {% capture sluglist %}{{ sluglist }}{{ t | slugify }} {% endcapture %}
      {% endfor %}
    {% elsif dossier.theme %}
      {% capture sluglist %}{{ dossier.theme | slugify }}{% endcapture %}
    {% endif %}

    <article class="dossier-item" data-theme="{{ sluglist | strip }}">
      <h2><a href="{{ dossier.url | relative_url }}">{{ dossier.title }}</a></h2>
      {% if dossier.themes %}
        <p><em>{{ dossier.themes | join: ", " }}</em></p>
      {% elsif dossier.theme %}
        <p><em>{{ dossier.theme }}</em></p>
      {% endif %}
      {{ dossier.excerpt }}
    </article>
  {% endfor %}
</div>

<script>
(function() {
  const select = document.getElementById('theme-filter');
  const items  = document.querySelectorAll('.dossier-item');

  function filter() {
    const val = select.value;
    items.forEach(it => {
      const themes = it.dataset.theme.split(' ');
      if (val === 'all' || themes.includes(val)) {
        it.style.display = '';
      } else {
        it.style.display = 'none';
      }
    });
  }
  filter(); // initial call in case default not 'all'
  select.addEventListener('change', filter);
})();
</script>
