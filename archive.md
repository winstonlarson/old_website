---
layout: page
title: Archive
---

{% for post in site.posts %}
  * **[ {{ post.title }} ]({{ post.url }})** - {{post.note}}
{% endfor %}
