---
title: "Fun Things"
permalink: /fun-things/
---


## Fun Things
Here is where I showcase fun stuff I do.

<ul>
  {% for post in site.categories.fun-things %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
