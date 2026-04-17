---
layout: default
title: "Blog"
permalink: /blog/
---

<div class="blog-header animate-fade-in">
  <h1 class="page-title">Blog ✍️</h1>
  <span class="post-count">{{ site.posts.size }} posts</span>
</div>

{% if site.posts.size > 0 %}
  {% for post in site.posts %}
  <article class="post-card animate-fade-in">
    <div class="post-card-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
      {% for tag in post.tags %}
        <span class="tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <h2 class="post-card-title">
      <a href="{{ post.url }}">{{ post.title }}</a>
    </h2>
    <p class="post-card-excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
    <a href="{{ post.url }}" class="read-more">Read more →</a>
  </article>
  {% endfor %}
{% else %}
  <div class="card animate-fade-in" style="text-align:center; padding: 3rem;">
    <p style="font-size:2rem;">🌸</p>
    <p style="color:#9b7ab5;">Posts are on the way, stay tuned~</p>
  </div>
{% endif %}
