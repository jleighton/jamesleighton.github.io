---
title: Gaming Backlog
layout: page
---

[![Backloggery](http://backloggery.com/ZombieUnicorn/sig.gif)](https://backloggery.com/zombieunicorn)

My gaming backlog is a massive pile of shame. A game is classed as 'beaten' either when I see the credits roll, or I decide to move on. Life is too short to play games you aren't enjoying!

I will try and keep my [Backloggery](http://backloggery.com/ZombieUnicorn/) up to date, and post semi regular blog posts about my progress through the backlog.

<div class="posts">
<h3>What I've Been Playing</h3>

<div class="row_card">

  <div class="column_card">


    {% for post in site.tags.backlog %}
  <div class="card2">
  <div class="container2">
<a href="{{ post.url }}" title="{{ post.title }}">
    <img src="{{ post.image }}" alt="{{ post.title }}" style="width:100%;">
    {{ post.title}}</a>
    <i class="fas fa-tags"></i>
    {% for tag in post.tags %}
    <a href="{{site.baseurl}}/tags/#{{tag|slugize}}">{{tag}}</a>
      {% unless forloop.last %}&nbsp;{% endunless %}
      {% endfor %}
  </div>
  </div>
    {% endfor %}

  </div>

</div>
