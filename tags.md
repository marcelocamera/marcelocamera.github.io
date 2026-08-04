---
layout: page
title: Tags
permalink: /tags/
---

{% assign sorted_tags = site.tags | sort %}
{% for tag in sorted_tags %}
  <h2 id="{{ tag[0] | slugify }}" class="year-heading">{{ tag[0] }}</h2>
  <ul class="post-list">
    {% for post in tag[1] %}
      <li class="post-list-item">
        <span class="post-list-date">{{ post.date | date: "%-d %b" }}</span>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
