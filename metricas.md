---
layout: page
title: Métricas
permalink: /metricas/
---

{% assign total_posts = site.posts.size %}
{% assign total_tags = site.tags.size %}

{% assign total_words = 0 %}
{% for post in site.posts %}
  {% assign words = post.content | number_of_words %}
  {% assign total_words = total_words | plus: words %}
{% endfor %}
{% if total_posts > 0 %}
  {% assign avg_words = total_words | divided_by: total_posts %}
{% else %}
  {% assign avg_words = 0 %}
{% endif %}

{% assign newest = site.posts.first %}
{% assign oldest = site.posts.last %}

<div class="metrics-grid">
  <div class="metric-card">
    <span class="metric-number">{{ total_posts }}</span>
    <span class="metric-label">posts publicados</span>
  </div>
  <div class="metric-card">
    <span class="metric-number">{{ total_tags }}</span>
    <span class="metric-label">tags diferentes</span>
  </div>
  <div class="metric-card">
    <span class="metric-number">{{ total_words }}</span>
    <span class="metric-label">palavras escritas</span>
  </div>
  <div class="metric-card">
    <span class="metric-number">{{ avg_words }}</span>
    <span class="metric-label">palavras por post (média)</span>
  </div>
</div>

{% if oldest %}
<p class="metrics-note">
  Primeiro post em <strong>{{ oldest.date | date: "%-d de %B de %Y" }}</strong>
  ({{ oldest.title }}), o mais recente em
  <strong>{{ newest.date | date: "%-d de %B de %Y" }}</strong>
  ({{ newest.title }}).
</p>
{% endif %}

{% if site.tags.size > 0 %}
  <h2 class="year-heading">Tags usadas</h2>
  <ul class="post-list">
    {% assign sorted_tags = site.tags | sort %}
    {% for tag in sorted_tags %}
      <li class="post-list-item">
        <span class="post-list-date">{{ tag[1].size }}</span>
        <a href="{{ '/tags/' | relative_url }}#{{ tag[0] | slugify }}">{{ tag[0] }}</a>
      </li>
    {% endfor %}
  </ul>
{% endif %}

<h2 class="year-heading">Visitas e tráfego</h2>
<p>
  Como este é um site estático, o número de visitantes, páginas mais lidas e
  origem do tráfego ficam disponíveis no
  <a href="https://analytics.google.com" target="_blank" rel="noopener">painel do Google Analytics</a>,
  fora do próprio blog.
</p>
