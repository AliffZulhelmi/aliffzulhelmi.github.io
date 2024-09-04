---
layout: blog
title: "Secure Coding"
permalink: /secure-coding/
category: secure-coding
---

# Secure Coding Blog
<ul>
  {% for post in site.categories.secure-coding %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span>{{ post.date | date: "%B %-d, %Y" }}</span>
  </li>
  {% endfor %}
</ul>
