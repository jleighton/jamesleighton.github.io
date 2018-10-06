---
Title: Connectify's NXDOMAIN Misdirections
Date: 2013-05-31 11:25
Author: jamesleighton
Tags: ads connectify dns geek
Slug: connectifys-nxdomain-misdirections
Status: published
---

I use Connectify Pro on my Windows box to share my internet connection to a wireless access point so I can access the internet on my Kindle, and 3DS. It's simple and it allows me to play Mario Kart online so it's great. I just didn't expect Connectify to take over my DNS setttings and redirect me to pages filled with ads.

![Connectify DNS Shenanigans](/images/this-should-fail.PNG)

I bought a new domain today, and was presented with a page filled with 'Related Links'. Hmm. I did some digging and found out that Connectify's default internal DNS server returns invalid responses. Take a look the screenshots.

![Fake Ad Filled Page courtesy of Connectify](/images/nxdomain-page.PNG)

Clearly non-existant-lol.co.uk doesn't exist. Using Connectify's DNS Resolver I get a page apparently from [DomainSponsor](http://cdn.dsultra.com/t/ds_legal.html). It's definitely Connectify; turn Hotspot mode off, DNS resolution goes back to normal, and I get a standard page/server not available error.

Using Google's Public DNS solves the issue as shown in the first screenshot. Amusingly, Connectify's [support pages](http://support.connectify.me/entries/20338992-Connectify-Hotspot-Command-Line-Interface-Syntax) state the following:

<div class="highlight">

    NXDOMAIN is a setting which causes the DNS server to automatically detect and redirect DNS  requests for nonexistant domains to a Connectify page.  This protects the user from ISP’s sending them to their own potentially fake web pages.

</div>

So instead of a scary ISP page filled with ads, you'll just get Connectify's instead. Nice of them to think about you, isn't it? It's not something you can disable directly within the Connnectify application, instead you have to open the program with specific command line switches.

An easier solution is the remove the reference to your local machine from within network settings and insert 8.8.8.8/8.8.4.4 to bypass your local machine entirely. You should then be able to go back to your standard browsing experience minus dodgy nonexistent domains serving you ads. You can of course use any other DNS server that use trust if Google isn't you thing!

![Google DNS Settings](/images/default-dns-settings.png)
