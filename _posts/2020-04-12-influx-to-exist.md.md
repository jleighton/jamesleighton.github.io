---
title: InfluxDB to Exist.io - Logging Gaming Time
date: '2020-04-12 11:28'
slug: influxdb-to-exist-gaming-time
author: jamesleighton
categories: Projects
tags: existio tracking lifelogging python
image: /images/grafana-dashboard.png
Status: published
--- 
Getting as much data into Exist as I can is important to me. So far this year I've built integrations for...

- Gaming Time
- [Pages Read](https://www.jamesleighton.com/2020/01/15/Logging-pages-read-to-Exist-io-via-Shortcuts-app/) (via iOS Shortcuts)
- Money Spent (using the Monzo API)

This post details how I am tracking gaming time. I found a method around Christmas 2019 that lets you retrieve accurate playtime from your Nintendo Switch via the parental controls app/feature. This was cool, but I don't always play things on my Switch, so we had to go deeper! 

Taking that a bit further, I discovered a [project on Github](https://github.com/c99koder/personal-influxdb) that tracked all of this data (and more!) into '[InfluxDB](https://www.influxdata.com/)'. InfluxDB is a 'time series' database, and as such is really good at storing data like the amount of time you played in a day,  the temperature of your living room, or the level of sunlight your house receives at intervals throughout the day.

You can then visualise this data with ease in ‘[Grafana](https://grafana.com/)’ - I played around with the gaming dashboard available from the [previously mentioned project](https://github.com/c99koder/personal-influxdb), and tailored it for the data I want to see. For example, I don't care about achievements so they got removed from the dashboard layout.

![Grafana Gaming Time Dashboard](/images/grafana-dashboard.png){:class="img-fluid"} 

To take this a step further, I wrote a small python script that retrieves playtime for a given day and submits it to [Exist.io](http://exist.io). This let's it become a part of the trend and correlation engine that powers the Exist dashboard.

![Script Output](/images/console.png){:class="img-fluid"}


![Exist Media Dashboard](/images/exist-media.png){:class="img-fluid"} 

![Exist Gaming Day of week averages](/images/exist-weekly.png){:class="img-fluid"} 

My python code can be found [https://github.com/jleighton/influx_gaming_to_exist](https://github.com/jleighton/influx_gaming_to_exist). I have this code submitting to exist.io every hour on a cronjob. The code that retrieves Switch playtime runs every 4 hours during the day, Steam and Rescuetime run hourly (just before the Exist push happens)

What this means is that whether I play something on Steam, other PC games like OpenTTD, or my Nintendo Switch all the playtime gets captured and logged without a second thought. It just works, and that’s awesome.

I realised that I then needed someway of logging playtime on systems that can't automatically post their data; such as my trusty 3DS, Snes Classic, and any games I play on my phone or tablet. This is a topic for another post, but what I did was build a small python based web interface (Flask based) to log playtime. Sneak peak below...

![Web form to submit Nintendo 3DS Playtime](/images/3ds-time.jpeg){:class="img-fluid"} 