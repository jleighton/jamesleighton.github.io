---
title: Gaming Backlog
layout: page
---

[![Backloggery](http://backloggery.com/ZombieUnicorn/sig.gif)](https://backloggery.com/zombieunicorn)

My gaming backlog is a massive pile of shame. A game is classed as 'beaten' either when I see the credits roll, or I decide to move on. Life is too short to play games you aren't enjoying!

I will try and keep my [Backloggery](http://backloggery.com/ZombieUnicorn/) up to date, and post semi regular blog posts about my progress through the backlog.

<div class="posts">

<ul>
  {% for post in site.categories.Backlog %}

<li><a href="{{ post.url }}" title="{{ post.title }}">{{ post.title}}</a></li>

  {% endfor %}
  </ul>
</div>
