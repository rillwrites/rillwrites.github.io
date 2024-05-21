---
layout: default
---

## A List of Posts

<ul>
{% for post in site.posts reversed %}
	{{ article.date | date_to_string: "%B %d, %Y" }}

  <li>    <a href="{{ post.url }}">{{ post.title }}</a> ({{ article.date }})
</li>
{% endfor %}
</ul>
