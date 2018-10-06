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

```lighttpd
    ssl.use-sslv2 = "disable"
    ssl.use-sslv3 = "disable"
```

You need to be running at least Lighttpd 1.4.29

