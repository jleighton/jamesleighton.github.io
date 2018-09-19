---
layout: default
title: How-To Posts
permalink: /category/how-to/index.html
---



<div class="posts">
  {% for post in site.categories.How-To %}
  <div class="post">


<h1 class="post-title">{{ post.title }}</h1>
  <em><span class="post-date">

  <i class="fas fa-calendar-alt"></i> {{ post.date | date_to_string }}



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
</em>



      {{ post.excerpt }}

      <a href="{{ post.url }}">[ Read More ]</a>
  </div>
  {% endfor %}
</div>
