---
layout: page
title: Archive
---

{% for post in site.posts %}
  **[ {{ post.title }} ]({{ post.url }})**&nbsp;&nbsp;*{{post.date}}*<br>
  {{post.note}}
{% endfor %}
