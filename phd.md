---
layout: default
title: PhD Journey
permalink: /phd.html
---

# PhD Journey

Posts sobre o doutorado:

<ul>
  {% assign sorted_phd = site.phd | sort: 'date' | reverse %}
  {% for post in sorted_phd %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small>— {{ post.date | date: "%d/%m/%Y" }}</small>
    </li>
  {% endfor %}
</ul>
