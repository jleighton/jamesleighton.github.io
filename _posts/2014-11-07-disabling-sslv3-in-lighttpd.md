---
Title: Disabling SSLv3 in Lighttpd
Date: 2014-11-07 11:47
Author: jamesleighton
categories: How-To
Tags: geek lighttpd
Slug: disabling-sslv3-in-lighttpd
Status: published
---

To disable SSLv3 in Lighttpd to mitigate the [Poodle attack](https://en.wikipedia.org/wiki/POODLE), add the following to your lighttpd.conf file.

<div class="highlight">

    ssl.use-sslv2 = "disable"
    ssl.use-sslv3 = "disable"

</div>

You need to be running at least Lighttpd 1.4.29

[![Toy Poodle in Riga 3](/images/poodle.jpg){width="512"}](https://commons.wikimedia.org/wiki/File%3AToy_Poodle_in_Riga_3.JPG "By Томасина (Own work) [CC-BY-SA-3.0 (http://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons")
