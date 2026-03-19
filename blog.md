---
layout: page
title: Blog
body_class: blog-index
permalink: /blog/
---

<h1>Blog</h1>

<div class="blog-card-grid">
  {% for post in site.posts %}
  <article class="blog-card">
    {% if post.image %}
      <img src="{{ post.image }}" alt="{{ post.title }}">
    {% else %}
      <!-- Optional placeholder image if no post.image -->
      <div class="blog-card-placeholder"></div>
    {% endif %}

    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

    {% if post.subtitle %}
      <p class="blog-subtitle">{{ post.subtitle }}</p>
    {% endif %}

    <p class="blog-date">{{ post.date | date: "%b %-d, %Y" }}</p>

    {% if post.excerpt %}
      <p class="blog-excerpt">{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
    {% endif %}

    <a class="read-more" href="{{ post.url }}">Read →</a>
  </article>
  {% endfor %}
</div>