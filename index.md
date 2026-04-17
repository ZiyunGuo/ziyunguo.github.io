---
layout: default
title: "首页"
permalink: /
---

<section class="hero animate-fade-in">
  <p class="hero-greeting">
    <span class="lang-zh">你好，我是紫云 ✨</span>
    <span class="lang-en">Hi, I'm Ziyun ✨</span>
  </p>
  <p class="hero-sub">
    <span class="lang-zh">研发工程师 · 新加坡管理大学</span>
    <span class="lang-en">Research Engineer · Singapore Management University</span>
  </p>
  <div class="hero-actions">
    <a href="/blog/" class="btn btn-primary">
      <span class="lang-zh">✍️ 看看博客</span>
      <span class="lang-en">✍️ Read Blog</span>
    </a>
    <a href="/about/" class="btn btn-outline">
      <span class="lang-zh">💜 关于我</span>
      <span class="lang-en">💜 About Me</span>
    </a>
  </div>
</section>

<div class="home-sections">

  <!-- Latest Posts -->
  <section class="latest-posts">
    <h2 class="section-title">
      <span class="lang-zh">最新文章</span>
      <span class="lang-en">Latest Posts</span>
    </h2>
    {% for post in site.posts limit:3 %}
    <article class="post-card animate-fade-in">
      <div class="post-card-meta">
        <time>{{ post.date | date: "%Y-%m-%d" }}</time>
        {% for tag in post.tags %}
          <span class="tag">{{ tag }}</span>
        {% endfor %}
      </div>
      <h3 class="post-card-title"><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <p class="post-card-excerpt">{{ post.excerpt | strip_html | truncate: 100 }}</p>
      <a href="{{ post.url }}" class="read-more">
        <span class="lang-zh">続きを読む →</span>
        <span class="lang-en">Read more →</span>
      </a>
    </article>
    {% endfor %}
    {% if site.posts.size == 0 %}
    <p style="color: var(--color-muted, #9b7ab5); font-size: 0.9rem;">
      <span class="lang-zh">文章正在路上，敬请期待 🌸</span>
      <span class="lang-en">Posts coming soon 🌸</span>
    </p>
    {% endif %}
    <a href="/blog/" class="btn btn-outline" style="margin-top:1rem; display:inline-flex;">
      <span class="lang-zh">查看全部文章 →</span>
      <span class="lang-en">All posts →</span>
    </a>
  </section>

  <!-- Interests -->
  <section class="card animate-fade-in">
    <h2 class="section-title">
      <span class="lang-zh">兴趣方向</span>
      <span class="lang-en">Interests</span>
    </h2>
    <div class="interest-tags">
      <span class="tag tag-pink">🔐 Security Research</span>
      <span class="tag tag-pink">🚩 CTF</span>
      <span class="tag">🐍 Python</span>
      <span class="tag">🐧 Linux</span>
      <span class="tag tag-blue">🌸 Anime</span>
      <span class="tag tag-blue">🎮 Games</span>
      <span class="tag">📚
        <span class="lang-zh">学习笔记</span>
        <span class="lang-en">Learning Notes</span>
      </span>
      <span class="tag">🛡️ Reverse Engineering</span>
    </div>
  </section>

</div>
