---
layout: default
title: Lessons
---

<div class="post">
  <h2>{{page.title}}</h2>
  <ul>
    {% for post in site.posts %}
      {% if post.categories contains 'lessons' %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
    </ul>
</div>
