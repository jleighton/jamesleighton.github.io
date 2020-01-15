---
title: Logging pages read to Exist.io via Shortcuts
date: 2020-01-15 07:45
author: jamesleighton
categories: Projects
tags: existio tracking shortcuts
slug: Logging-pages-read-to-Exist-io-via-Shortcuts-app
Status: published
layout: post
image: /images/B8D54505-44D3-4E76-9332-3E7DA729C5AB.jpeg
---

I was messing around with the [Exist.IO](http://exist.IO) API over the weekend to see what I could build. I noticed that there was a 'Pages read' attribute that I could post to.

Perfect! I then wondered how easily I could build an iOS app that would let me submit that each day (Spoiler: quite a lot of work) however, I remembered that Shortcuts was a thing and decided to see if it was possible to use a shortcut to post to an API.

The answer is yes - I have a home screen icon that asks me how many pages I've read and sends it to exist.

![Shortcut App - Prompt to enter pages read](/images/B8D54505-44D3-4E76-9332-3E7DA729C5AB.jpeg){:class="img-fluid"}

![Successful Log to Exist.io](/images/BAA4505E-F3F0-47F6-A073-2D5956EC3946.jpeg){:class="img-fluid"}

To get started with this, you should head over to the [Exist.IO developer pages](http://developer.exist.io/) and have a read through.

Firstly, Create a developer client from your account settings within Exist, and make sure it has access to the pages_read attribute. This will give you the information you require to generate the access tokens needed for the Shortcut.

<a href="/images/Screenshot_2020-01-15_at_07.40.00.png" data-toggle="lightbox" data-title="Exist Developer Dashboard!" data-gallery="example-gallery">
    <img src="images/Screenshot_2020-01-15_at_07.40.00.png" class="img-fluid">
</a>

The follow the OAuth2 authentication steps, and create your access token. (I have some Python code that will help do this, but I need to tidy it up before I release it.)

Lastly, You can load the following shortcut on your phone or ipad and paste in your authentication token and that is it!

[https://www.icloud.com/shortcuts/b493d6e88fcf47d293e6cb5cc8ff9224](https://www.icloud.com/shortcuts/b493d6e88fcf47d293e6cb5cc8ff9224)

![Exist Dashboard](/images/pages-read2.png){:class="img-fluid"}
