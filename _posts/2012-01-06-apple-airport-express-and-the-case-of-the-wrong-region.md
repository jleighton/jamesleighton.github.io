---
Title: Apple Airport Express and the case of the wrong region
Date: 2012-01-06 15:47
Author: jamesleighton
categories: How-To
tags: apple howto networking troubleshooting wifi
Slug: apple-airport-express-and-the-case-of-the-wrong-region
Status: published
---

My Airport Express has been used for about six months via ethernet to stream audio, but recently I moved stuff around and had a tidy up and now my wireless signal in my room is (now, was) rubbish.

Initially I tried reconfiguring it to be a wireless access point, but nothing I could do would make it work. There was apparently no wireless signal being transmitted. Digging around the configuration pages in Airport Utility it seemed my Airport Express thought it was a US unit, those being the only countries available to select in wireless settings. I was informed this shouldn’t really cause an issue (it would only cause two extra channels to be missing) but it was bugging me.

Downgrading and upgrading the firmware didn’t help. You can’t even manually download recent firmware anymore, it all has to be managed completely (downloading and installation) through the utility manager.

Just about to give up, I stumbled across this article on MacBook which details how to [fully reset the Airport Express](http://www.macworld.com/article/36834/2004/08/000282.html). It worked! Basically, unplug the device hold down the reset button (near the connections for speakers and ethernet) and plug it back in whilst continuing to hold down the reset button.

I held the button for around twenty seconds whilst the notification LED flashed orange really quickly. A quick trip back to Airport Utility and I have a functional wireless network again! Yay!
