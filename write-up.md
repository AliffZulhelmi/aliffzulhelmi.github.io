---
layout: blog
title: "Write-Up"
permalink: /write-up/
category: write-up
---

# Write-Up Blog
<ul>
  {% for post in site.categories.write-up %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    <span>{{ post.date | date: "%B %-d, %Y" }}</span>
  </li>
  {% endfor %}
</ul>
