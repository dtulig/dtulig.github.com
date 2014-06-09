---
layout: default
title: Post Archive
meta: The archive of all posts.
permalink: /archive/
---

<div id="home">
  <h1>Archive</h1>
  <ul class="posts">
    {% for post in site.posts %}
    {% if post.categories contains 'posts' %}
    <li><span>{{ post.date | date_to_string }}</span>
      &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
    {% endfor %}
  </ul>

</div>