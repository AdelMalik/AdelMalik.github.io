---
layout: default
title: Publications
description: Publications and preprints by Adel Malik Annabi.
---
<h1 class="page-title">Publications</h1>

{% assign preprints = site.data.publications | where: "type", "Preprint" | sort: "year" | reverse %}
{% assign publications = site.data.publications | where: "type", "Publication" | sort: "year" | reverse %}

{% if preprints.size > 0 %}
<section class="pub-group">
  <h2 class="pub-group-title">Preprints</h2>
  <ul class="pub-list">{% for p in preprints %}{% include pub-item.html p=p %}{% endfor %}</ul>
</section>
{% endif %}

{% if publications.size > 0 %}
<section class="pub-group">
  <h2 class="pub-group-title">Publications</h2>
  <ul class="pub-list">{% for p in publications %}{% include pub-item.html p=p %}{% endfor %}</ul>
</section>
{% endif %}
