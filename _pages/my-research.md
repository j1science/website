---
title: "My Research"
permalink: /my-research/
---

## My Research
This section covers my scientific research.

<ul>
  {% for post in site.categories.my-research %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
