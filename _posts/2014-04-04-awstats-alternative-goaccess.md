---
Title: AWStats Alternative: GoAccess
Date: 2014-04-04 18:22
Author: jamesleighton
categories: How-To
tags: geek server
Slug: awstats-alternative-goaccess
Status: published
---
I didn't really want to bother with installing [AWStats](http://awstats.sourceforge.net/) and setting up the cgi stuff that goes with it, as well as setting the web server to ensure the stats stay hidden. I just want to get a rough idea of who's visiting my site and when. I'm usually happy with running a terminal window with tail -f, but sometimes a bit more analysis is needed.

Today I found a cool alternative, [GoAccess](http://goaccess.prosoftcorp.com/).

[![GoAccess Main Screen](/images/goacess.png)](http://goaccess.prosoftcorp.com/)

It has a nice simple and usable interface based on Curses (It'll be familiar if you used Irssi, Mutt, or the like) and gives all the needed information at a glance. It can even output HTML reports if you really want them.

I tried installing the version from the Debian repositories but found (as usual) that it was terribly out of date. I think they had a package for version 0.5, when 0.7.1 is the latest.

If you simply head off to [GoAccess's webpage](http://goaccess.prosoftcorp.com/download), and follow the instructions for compiling from source you'll be up and running in no time at all. Just a note that I had issues downloading and compiling from the Sourceforge download; the resulting program would just crash and segfault. This went away when I checked out the development github code and compiled that way.

If you have issues with dependencies, try installing the following packages which should cover most of the dependencies in one command.

<div class="highlight">

    sudo apt-get install dh-autoreconf build-essential libglib2.0-dev libncurses5-dev libncursesw5-dev libgeoip-dev

</div>

If you're using Lighttpd like me, when you first run GoAccess make sure to select the NCSA Combined Log Format otherwise you'll be missing portions of your data.

![GoAccess Log Confirguration Settings](/images/goacess-conf.png)
