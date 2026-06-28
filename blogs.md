---
layout: page
title: Blog
permalink: /blogs/
---

{% comment %}
  Merge internal posts and external posts from _data/external_posts.yml,
  sort by date descending, and render together.
{% endcomment %}

{% assign external = site.data.external_posts | default: empty_array %}

{% assign all_posts = site.posts %}

<ul class="post-list">

  {% comment %} Internal posts {% endcomment %}
  {% for post in site.posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%B %d, %Y" }}</span>
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      {% if post.description %}<p>{{ post.description }}</p>{% endif %}
    </li>
  {% endfor %}

  {% comment %} External posts {% endcomment %}
  {% for post in site.data.external_posts %}
    <li>
      <span class="post-meta">{{ post.date | date: "%B %d, %Y" }}
        {% if post.source %}&nbsp;·&nbsp;<em>{{ post.source }}</em> <span class="external-label">↗ external</span>{% endif %}
      </span>
      <h3><a href="{{ post.url }}" target="_blank" rel="noopener">{{ post.title }}</a></h3>
      {% if post.description %}<p>{{ post.description }}</p>{% endif %}
    </li>
  {% endfor %}

</ul>

{% if site.posts.size == 0 and site.data.external_posts.size == 0 %}
  <p>No posts yet. Check back soon!</p>
{% endif %}

<style>
  .post-list { list-style: none; padding: 0; }
  .post-list li { margin-bottom: 2rem; }
  .post-meta { font-size: 0.85rem; color: #888; }
  .external-label { font-size: 0.75rem; color: #aaa; }
</style>
