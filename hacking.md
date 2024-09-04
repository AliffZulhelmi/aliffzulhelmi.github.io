---
layout: blog
title: "Hacking"
permalink: /hacking/
category: hacking
---

# Hacking Blog
<ul>
  {% for post in site.categories.hacking %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span>{{ post.date | date: "%B %-d, %Y" }}</span>
  </li>
  {% endfor %}
</ul>
