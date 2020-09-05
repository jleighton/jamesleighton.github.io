---
title: Todoman Reminder Sync for Fastmail
date: 2020-09-05 18:00
author: jamesleighton
categories: How-To
tags: productivity ubuntu fastmail
slug: fastmail-todoman-reminder-sync
status: published
layout: post
image: /images/fastmail.png
---

How to configure calendar sync on Linux (tested on Ubuntu 20.04) for Fastmail using vdirsync and todoman.

This lets me use the same todo list between my linux desktop, and iOS mobile devices (using the built in stock reminders app)

## Vdirsyncer Config

I am using [vdirsyncer](https://github.com/pimutils/vdirsyncer) to connect to Fastmail's servers and before the synchronisation.

```[general]
status_path = "~/.vdirsyncer/status/"
[pair fastmail]
a = "local"
b = "cal"
collections = ["from a", "from b"]
[storage cal]
type = "caldav"
url = "https://caldav.messagingengine.com/"
username = "username@fastmail.com"
password = "fastmail-app-specific-password"
[storage local]
type = "filesystem"
path = "~/.vdirsyncer/fastmail"
fileext = ".ics"
```

## Todoman

[Todoman](https://github.com/pimutils/todoman) is a terminal reminder/todo app that can work with vdirsyncer.

![todoman.png](/images/todoman.png){:class="img-fluid" :alt="Todoman Output in Terminal"}
*Todoman Output in Terminal*
{:.image-caption}

Here is my configuration for todoman that points it at the folders created by vdirsyncer.

```[main]
# A glob expression which matches all directories relevant
path = ~/.vdirsyncer/fastmail/path-for-reminders-cal
date_format = %Y-%m-%d
time_format = %H:%M
default_list = reminders-cal-id (same as the folder, see below...)
default_due = 48
humanize = true
```

To figure out which calendar is the ical reminders feed you can take a look in ~/.vdirsyncer/fastmail. There should be a folder for each of your Fastmail calenders.

Look through the ICS files that you find and you'll find something similar to the this example. You want to use the directory name of the folder that contains your VTODO's - use the directory name for the default_list above as well.

```BEGIN:VCALENDAR
CALSCALE:GREGORIAN
PRODID:-//Apple Inc.//iOS 13.6.1//EN
VERSION:2.0
BEGIN:VTODO
CLASS:PUBLIC
COMPLETED:20200825T165931Z
CREATED:20200825T165843Z
DTSTAMP:20200825T165931Z
LAST-MODIFIED:20200825T165931Z
PERCENT-COMPLETE:100
STATUS:COMPLETED
SUMMARY:Test from ios  
UID:d3cc53dabe0fb4280617dd7c349f2705ea72e59f
END:VTODO
END:VCALENDAR
```

## Calendar Support

It is possible to using a terminal calendar tool like Calcurse or [Khal](https://github.com/pimutils/khal) but I have not set these up yet.

## Automating with Cron

To automate synchronisation, I used cron. Add the following via `crontab -e` to run the sync every 15 minutes.

```*/15 * * * * /home/james/.local/bin/vdirsyncer sync > /dev/null```
