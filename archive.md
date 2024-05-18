---
layout: default
---

## A List of Posts

<ul>
{% for post in site.posts reversed %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a> ({{ post.date }})
  </li>
{% endfor %}
</ul>
