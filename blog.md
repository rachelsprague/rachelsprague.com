---
layout: page
title: Blog
body_class: blog-index
permalink: /blog/
---

<h1>Blog</h1>

<div class="blog-cards">
  {% for post in site.posts %}
    <a href="{{ post.url }}" class="blog-card">
      {% if post.image %}
        <img src="{{ post.image }}" alt="{{ post.title }}">
      {% endif %}
      <div class="card-content">
        <h3>{{ post.title }}</h3>
        <p class="card-date">{{ post.date | date: "%b %-d, %Y" }}</p>
      </div>
    </a>
  {% endfor %}
</div>