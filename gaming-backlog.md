---
title: Gaming Backlog
layout: page
---

[![Backloggery](http://backloggery.com/ZombieUnicorn/sig.gif)](https://backloggery.com/zombieunicorn)

My gaming backlog is a massive pile of shame. A game is classed as 'beaten' either when I see the credits roll, or I decide to move on. Life is too short to play games you aren't enjoying!

I will try and keep my [Backloggery](http://backloggery.com/ZombieUnicorn/) up to date, and post semi regular blog posts about my progress through the backlog.


<h3>What I've Been Playing</h3>





  <div class="row">
  {% for post in site.tags.backlog %}

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
