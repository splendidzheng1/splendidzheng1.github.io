---
layout: default
title: 标签
permalink: /tags.html
---

<h1>标签分类</h1>

{% assign tags = "" %}
{% for post in site.posts %}
  {% for tag in post.tags %}
    {% unless tags contains tag %}
      {% assign tags = tags | append: "," | append: tag %}
    {% endunless %}
  {% endfor %}
{% endfor %}
{% assign tag_list = tags | split: "," %}

{% for tag in tag_list %}
<section id="{{ tag | slugify }}">
  <h2>#{{ tag }}</h2>
  <ul>
  {% for post in site.posts %}
    {% if post.tags contains tag %}
      <li><a href="{{ post.url }}">{{ post.title }}</a> — {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
  </ul>
</section>
<hr>
{% endfor %}
