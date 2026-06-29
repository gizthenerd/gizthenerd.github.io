---
layout: default
title: Blog
permalink: /blogs/
---

<div class="blog-header">
  <div class="section-title">Blog</div>
</div>

<ul class="post-list">

  {% for post in site.posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%B %d, %Y" }}</span>
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      {% if post.description %}<p>{{ post.description }}</p>{% endif %}
    </li>
  {% endfor %}

  {% for post in site.data.external_posts %}
    <li>
      <span class="post-meta">
        {{ post.date | date: "%B %d, %Y" }}
        {% if post.source %}&nbsp;·&nbsp;<em>{{ post.source }}</em> <span class="external-label">↗</span>{% endif %}
      </span>
      <h3><a href="{{ post.url }}" target="_blank" rel="noopener">{{ post.title }}</a></h3>
      {% if post.description %}<p>{{ post.description }}</p>{% endif %}
    </li>
  {% endfor %}

</ul>

{% if site.posts.size == 0 and site.data.external_posts.size == 0 %}
  <p style="color: var(--text-faint); font-size: 0.82rem;">// no posts yet — check back soon</p>
{% endif %}
