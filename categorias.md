---
layout: page
title: Categorías
permalink: /categorias/
---

<div class="category-buttons">
  {% for category in site.data.categorias %}
  <a class="category-button" href="#{{ category.name }}">{{ category.name }}</a>
  {% endfor %}
</div>

{% for category in site.data.categorias %}
<h2 id="{{ category.name }}">{{ category.name }}</h2>
<table class="category-table">
  <tbody>
    {% for post in category.posts %}
    <tr>
      <td><a href="{{ post.link }}">{{ post.title }}</a></td>
    </tr>
    {% endfor %}
  </tbody>
</table>
{% endfor %}
