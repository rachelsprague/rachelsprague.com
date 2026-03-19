---
layout: page
title: Blog
body_class: blog-index
permalink: /blog/
---

<h1>Blog</h1>

<div class="blog-container">
  {% for post in site.posts %}
  <article class="blog-summary">
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    {% if post.subtitle %}
      <p class="blog-subtitle">{{ post.subtitle }}</p>
    {% endif %}
    <p class="blog-date">{{ post.date | date: "%b %-d, %Y" }}</p>
    {% if post.excerpt %}
      <p class="blog-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
    {% endif %}
    <p><a class="read-more" href="{{ post.url }}">Read more →</a></p>
  </article>
  {% endfor %}
</div>