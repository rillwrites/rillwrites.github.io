layout: default
title: List of posts - Newest to Oldest
---
<ul>
  {% for post in site.posts  %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
    </li>
  {% endfor %}
</ul>
