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
    <span class="post-date"><i class="fas fa-calendar-alt"></i> {{ post.date | date_to_string }}



    {% if post %}
      {% assign categories = post.categories %}
    {% else %}
      {% assign categories = page.categories %}
    {% endif %}
    <i class="far fa-folder-open"></i>
    {% for category in categories %}
     <a href="{{site.baseurl}}/category/{{category|downcase}}/">{{category}}</a>
    {% unless forloop.last %}&nbsp;{% endunless %}
    {% endfor %}


    {% if post %}
      {% assign tags = post.tags %}
    {% else %}
      {% assign tags = page.tags %}
    {% endif %}
  <i class="fas fa-tags"></i>
  {% for tag in tags %}
  <a href="{{site.baseurl}}/tags/#{{tag|slugize}}">{{tag}}</a>
    {% unless forloop.last %}&nbsp;{% endunless %}
    {% endfor %}

  </span>

{% endfor %}
