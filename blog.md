---
layout: blog
title: "All Blog Posts"
permalink: /blog/
---

# All Blog Posts
<ul>
  {% for post in site.posts %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a> - 
    <span>{{ post.date | date: "%B %-d, %Y" }}</span> in 
    <strong>{{ post.categories | join: ", " }}</strong>
  </li>
  {% endfor %}
</ul>
