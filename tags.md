---
layout: page
permalink: /tags/
title: Tags
---


<div id="archives">
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="#{{ tag_name | slugify }}"></div>
    <p></p>

      <a name="{{ tag_name | slugify }}"><h3 class="tag-head">{{ tag_name }}</h3>  </a>

    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
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


    {% endfor %}

    </span>
  
{% endfor %}
</div>
