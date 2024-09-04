---
layout: blog
title: "Hacking"
permalink: /hacking/
category: hacking
---

# Hacking Blog
<div class="article-list">
  {% for post in site.categories.hacking %}
  <div class="article-item">
    <a href="{{ post.url | relative_url }}">
      <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
      <h2 class="article-title">{{ post.title }}</h2>
    </a>
    <div class="article-content">
      {{ post.excerpt }}
    </div>
  </div>
  {% endfor %}
</div>