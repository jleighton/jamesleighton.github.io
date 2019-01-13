---
title: Bootstrap 4 - New Blog Theme
date: 2019-01-13 11:17
Author: jamesleighton
categories: Projects
tags: jekyll blog pelican
slug: new-blog-theme-bootstrap-4-how-i-made-it
status: published
image: /images/bootstrap-logo.png
layout: post
---

I decided last week that I really wanted a card based theme for my blog. After all, [cards are cool](https://www.intercom.com/blog/why-cards-are-the-future-of-the-web/).

After spending a few hours messing around with existing themes, and trying to customise them to my vision for what I wanted... someone at my local hackspace suggested I took a look at Bootstrap when I couldn't get them to generate valid HTML properly. This was cool because I got to learn something new (see [2019 goals](/2018/12/29/2019-goals/)!) but because Bootstrap is modern and responsive and made creating the cards I longed for super duper simple.

[Bootstrap](https://getbootstrap.com/) is a HTML/CSS/JS framework for building modern websites and applications, and I initially felt like the task was going to be enormous and promptly gave up when I couldn't get anything to work right away. It turned out with not very much effort I was able to make a pretty decent looking blog.

![Bootstrap 4](/images/bootstrap-logo.png){:class="img-fluid"}

The next day I reconsidered my efforts and set about building the blog from the ground up, and then implementing it into my new Jekyll theme after I had something that looked nice. This turned out to be a 'good idea'.

A few more hours later, I had the framework for how I envisaged the blog to look. We had the cards for blog posts on the home page, no pagination - because pagination annoys me - and a working navigation bar. I just needed to work on the post layout (the page you are reading now) and it turns out someone had done the hard work. I found [this template](https://github.com/blackrockdigital/startbootstrap-blog-post/) blog post available under an MIT licence ready to drop into Jekyll.

Turning my HTML template into a Jekyll theme was pretty site, and you can see how I did it by looking at the [Github repository](https://github.com/jleighton/jleighton.github.io) for this blog. I am planning to write a long form how-to guide for this but that will take a while. Pretty much you need to do the following:

* Split the layout into it's most basic form. Header, blog layout, sidebar, navbar, etc etc. Whatever makes the most sense.
* Add the header code to a file in the ```_includes``` folder, add the navbar code to another file, add the jumbotron code to yet another file, the footer code etc. You get the idea. You basically need to split out the theme so Jekyll knows what to include and where
* Create layout templates that live in ```_layouts```. These include your post template, the default home page, a blank page that just has the Bootstrap scaffolding (see [Travel Map](/uk-travel-map) page). These layout templates will reference the files in ```_includes```.
* These templates are reference in your markdown content so Jekyll can render your content how you want it to.

The idea of having the layout logic separated as much as possible into discrete files is that it makes updating your sidebar or the way you want the post cards to display super easy and less error prone.

[This post](https://jekyllrb.com/tutorials/convert-site-to-jekyll/) from the official Jekyll site gives a good run down of how this process of theme creation works, and is worth the read. Before you start, I would definitely try to have a full understanding of how Jekyll works under the hood plus a decent working knowledge of HTML & CSS.

To theme my blog I used [Bootswatch United](https://bootswatch.com/united/) which is a theme for Bootstrap. Long time readers much recognise the colour; my old Pelican blog used the same theme! Using Bootstrap themes is as simple as adding the CSS link to your header. There are loads of different themes available but I just love orange.

    <!-- Optional theme -->
    <link href="https://stackpath.bootstrapcdn.com/bootswatch/4.2.1/united/bootstrap.min.css" rel="stylesheet" integrity="sha384-integrity-code-here" crossorigin="anonymous">
    <!-- End Optional theme -->



I am pretty happy with the blog as it stands, but there are always things to improve. I am still looking a decent commenting solution that isn't Disqus and doesn't require my commenters to have Gitub accounts. As always, if you have any suggestions please drop me a tweet! @geekyjames

### Features

- Card layouts for all blog posts based from one card template.
- Easy to generate a page for a specific category or tags.
- Home page is the about page, rather than the wall of blog posts.
- Fully responsive for desktop, tablet and mobile
- Orange!

![My blog homepage](/images/blog-history-most-recent.png){:class="img-fluid"}
