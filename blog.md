---
layout: page
title: Blog
---

{% for post in site.posts %}
  **[ {{ post.title }} ]({{ post.url }})**&nbsp;&nbsp;*{{ post.date | date_to_string }}*<br>
  {{post.note}}
{% endfor %}
