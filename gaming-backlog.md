---
title: Gaming Backlog
layout: page
---

[![Backloggery](http://backloggery.com/ZombieUnicorn/sig.gif)](https://backloggery.com/zombieunicorn)

My gaming backlog is a massive pile of shame. Here lies the evidence; this page will be a log of my progress through my backlog across all my gaming platforms and serve to me as a reminder as to why I genuinely need to not buy any more games...

<div class="posts">
  {% for post in site.categories.Backlog %}
  <div class="post2">


<h3 class="post-title">{{ post.title }}</h3>
  <em><span class="post-date">

  <i class="fas fa-calendar-alt"></i> {{ post.date | date_to_string }}



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
{% if post.image %}
<img src=" {{ post.image }}" style="width:25%; float: left; padding-right:8px;" title="{{ post.title }}" />
{% else %}

 {% for category in categories %}
 <img src="https://www.jamesleighton.com/images/cat-{{category|downcase}}.png" style="width:25%; float: left; padding-right:8px;" title="{{ post.title }}" />
   
  {% endfor %}

{% endif %}

     <div class="justified-post-content" style="text-align:justify;"> {{ post.excerpt }} </div><a href="{{ post.url }}">[ Read More ]</a>
  </div>
  <div style="clear: both;"></div>
      
      
      
      
  
  {% endfor %}
</div>

