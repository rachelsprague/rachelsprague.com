---
layout: page
title: Blog
body_class: blog-index
permalink: /blog/
---
<!-- <h1>Blog</h1> -->
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a> — <em>{{ post.date | date: "%b %-d, %Y" }}</em>
    </li>
  {% endfor %}
</ul>