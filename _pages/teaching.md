---
title: "Teaching"
permalink: /teaching/
---

## Teaching
Here I share my teaching materials and philosophy.


<ul>
  {% for post in site.categories.teaching %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
