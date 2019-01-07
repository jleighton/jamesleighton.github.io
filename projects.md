---
title: Projects
layout: page
---
Here is the archive of my projects. They range from programming, to electronics, 3D printing, and more.

<div class="row">
{% for post in site.tags.projects %}

<div class="column">


  <div class="card">
  <a href="{{ post.url }}" title="{{ post.title }}">
      <img src="{{ post.image }}" alt="{{ post.title }}" style="width:100%;">
      {{ post.title}}</a>
      {% if post %}
        {% assign tags = post.tags %}
      {% else %}
        {% assign tags = page.tags %}
      {% endif %}<br />
    <span style="font-size: 75%;"><i class="fas fa-tags"></i>
    {% for tag in tags %}

    <a href="{{site.baseurl}}/tags/#{{tag|slugize}}">{{tag}}</a>
      {% unless forloop.last %}&nbsp;{% endunless %}
      {% endfor %}</span>
      {{ post.content | strip_html | truncatewords: 25 }}
    </div>

</div>
{% endfor %}

</div>
