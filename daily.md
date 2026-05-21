---
layout: default
title: Daily Digest
permalink: /daily.html
---

# Daily Digest

Posts do dia a dia:

<ul>
  {% assign sorted_daily = site.daily | sort: 'date' | reverse %}
  {% for post in sorted_daily %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small>— {{ post.date | date: "%d/%m/%Y" }}</small>
    </li>
  {% endfor %}
</ul>
