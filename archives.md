---
title: Archives
layout: page
---
<h2>Archive</h2>

  {% for post in site.posts %}
  <article>
    <h2>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h2>
    <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
 {{ post.categories }}
  </article>
{% endfor %}
