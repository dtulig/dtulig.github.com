---
layout: default
title: Talks
meta: Talks I have given at events, meetups, and conferences.
permalink: /talks/
---

<div id="home">
  <h1>Talks</h1>
  <ul class="posts">
    {% for post in site.posts %}
    {% if post.categories contains 'talks' %}
    <li><span>{{ post.date | date_to_string }}</span>
      &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
    {% endfor %}
  </ul>

</div>