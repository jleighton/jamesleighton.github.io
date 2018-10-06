---
Title: Blocking Facebook Connect in Google Chrome
Date: 2011-07-26 16:47
Author: jamesleighton
Tags: block facebook howto
Slug: blocking-facebook-connect-in-google-chrome
Status: published
---

Seeing my Facebook details plastered over other websites always concerns me, and I definitely do not want to login using my Facebook details!

Adblock Plus to the rescue! Found the filter rules [here](http://www.dhcollier.com/2010/05/disabling-facebook-connect-on-non.html) (along with general instructions for FF and Chrome!).

Simply download [Adblock for Chrome](https://chrome.google.com/webstore/detail/cfhdojbkjhnklbpkdaibdccddilifddb) and add the following to the filter:

``` \*.facebook.\*\$domain=\~facebook.com|\~127.0.0.1```

Simple as that, Facebook Connect disappears from every site!
