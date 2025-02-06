---
title: "Publications"
permalink: /publications/
---

## Publications
Here is my research that I have published. Not comprehensive, Just the stuff I really liked.


<ul>
  {% for post in site.categories.publications %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%B %-d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
