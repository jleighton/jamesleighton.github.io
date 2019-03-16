---
title: Tracking planes from your laptop (ADS-B)
date: 2019-03-16 10:42
author: jamesleighton
categories: Projects
tags: sdr hackspace projects 
slug: tracking-planes-from-your-laptop-ads-sdr-software-defined-radio
Status: published
layout: post
image: /images/plane.png
---
My [local hackspace](https://maidstone-hackspace.org.uk/) recently acquired [SDR dongle](https://amzn.to/2F9eXu5) for us to use, and since I've been wanting to have a play around with Software Defined Radios I spent an evening learning how to use it. Here is my quick rundown of how to track ADS-B plane transmissions using Mac OSX 10.14 and displaying them on a map.

![The SDR dongle and assorted bits](/images/dongle.png){:class="img-fluid"}

For some background on software defined radios, the idea is that the radio's characteristics can be changed on the fly by software so you can receive all sorts of different types of transmissions across the spectrum. 

A common chip (RTL2832) used in USB Digital TV (DVB-T) tuners could be used as an effective software defined radio, so more people became interested. More information can be [found here](https://www.rtl-sdr.com/about-rtl-sdr/).

[ADS-B](https://en.wikipedia.org/wiki/Automatic_dependent_surveillance_%E2%80%93_broadcast) is a system used by commercial flights to relay position, and speed information to the ground. It is the basis of sites such as FlightRadar24.


I tried a few different versions of dump-1090; the earlier ones used the Google Maps API which is no longer free and doesn't work without a google dev account. Eventually I settled on dump1090-mutability which uses OSM (OpenStreetMap tiles) and worked well.

I found instructions from [here](https://www.dzombak.com/blog/2017/01/Monitoring-aircraft-via-ADS-B-on-OS-X.html) which worked well. 

Instead of using nginx, I simply used python's [SimpleHTTPServer](https://lifehacker.com/start-a-simple-web-server-from-any-directory-on-your-ma-496425450) because I use it all the time and it saved installing yet another program. 

![Flights shown on the map](/images/flight-data-map.png){:class="img-fluid"}

We managed to pick up on flights over 40 miles away! An idea for the 'future projects' list is to get this setup again with the proper antennas designed for 1090mhz transmissions. More research required...