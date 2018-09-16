Title: Raspberry Pi Spotify Jukebox
Date: 2016-07-24 00:00
Author: jamesleighton
Tags: projects, raspberry pi
Slug: raspberry-pi-spotify-jukebox
Status: published

**Goal**

To create a simple to use office based music jukebox that everyone can use and no-one can take overall control of.

It needs to be clear, simple, and intuitive. It should be reliable, and not require manual intervention.

**Materials**

-   Raspberry Pi (I used a 3, probably could have used an older model)
-   Speaker with aux-in (Could use Bluetooth, but to keep things simple I didn't)
-   Aux cable

**Software**

-   Raspbian Lite
-   Mopidy
-   Spotmop Plugin
-   Spotify Premium Account

**Instructions**

Start by installing your Linux distrubtion of choice on your Pi, I used \[distro here\].

Head over to the [Mopidy project page](https://docs.mopidy.com/en/latest/installation/), and have a read through their Raspi Jessie instructions. You will need the [Spotify plugin](https://github.com/mopidy/mopidy-spotify) and the [Last.Fm plugin](https://github.com/mopidy/mopidy-scrobbler) if you wish to have a record of all the [music you play](http://www.last.fm/user/office-music). You may still need to [manually fix the scrobbler](https://github.com/mopidy/mopidy-scrobbler/issues/20), but it looks like this is getting fixed soon.

**Conclusions**

-   Pi Auxilary Audio Out is [terrible](https://www.reddit.com/r/raspberry_pi/comments/2yu3kd/rpi_2_poor_audio_quality/). I should probably spend more time figuring out bluetooth since the speaker we use supports it. Alternatively, you could use a HDMI to 3.5mm adapter which apparently will give you better sound. Or you could use a USB Sound card.
-   Need to figure out how to save the volume level as the default so on a reboot I do not need to SSH in and reset the volume \[command line snippet here next time I go to the office\]

