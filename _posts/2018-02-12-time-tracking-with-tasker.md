---
Title: Time Tracking with Tasker (Driving & Sleep Time)
Date: 2018-02-12 14:20
Author: jamesleighton
categories: Lifelogging
Tags: android android-auto productivity tasker timetracking lifelogging
Slug: time-tracking-with-tasker
Status: published
---

I listen to the podcast Cortex when I'm driving, and they got me interesting in looking up time tracking and how maybe this would benefit me. I already use [Rescuetime with Exist](http://jamesleighton.com/2017/08/05/life-tracking-with-exist-io/) as a measure of sleep, productivity, social media posts, and other things that correlate to these like the weather, the length of the day, and more. It's pretty neat and I look at it several times a week.

 

One metric it misses is driving time. As someone who drove 17,000 miles in the last 12 months for work this is pretty key to me. Apparently [rescuetime can do it with an expensive add on,](https://blog.rescuetime.com/new-integration-with-automatic-track-your-driving-time-like-your-computer-time/) but that only works in the US so that's no good.

I had a look through the rest of the Exist integrations and nothing really supports what I want. So, I've found another way of recording this information directly. Sadly it won't be with the rest of my Exist data but aTimeLogger generates its own fancy graphs and allows me to export the data to standard formats.

![Screenshot of aTimeLogger](/images/screenshot_smartselect_2018-02-12-13-45-24.jpg?w=1288)

Android Auto --&gt; [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm&hl=en_GB) --&gt; [aTimeLogger](http://www.atimelogger.com/)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

Basically the flow is as follows. You could also automate this based on connecting to a certain bluetooth radio, or even just an NFC tag you have stuck to your dashboard.

1.  Plug my phone into my car with Android Auto.
2.  Tasker notices the change in UI mode
3.  Tasker sends an intent to aTimeLogger to start timing.
4.  Disconnect from my car
5.  Tasker notices the change
6.  Tasker sends another intent to aTimeLogger to stop timing.

To get this working, add your groupings to aTimeLogger. I added a top level grouping of transportation with train and driving inside this grouping. I guess I'll add flying to this at some point too.

Once this is done, go into Tasker and create two new tasks. One for when you plug your phone in, and one for when you disconnect.  The task below is for when you connect your phone, and is explained line by line:

-   **A1:** Wait for 3 seconds for the connection to stabilise and the radio in the car to sort itself out.
-   **A2:** Using the aTimeLogger plugin in tasker, stop the Driving task if running and start it again.
-   **A3:** Wait another 4 seconds, same reasoning as above.
-   **A4:** Announce over the speakers that tracking is working. This seems to be able to talk over radio just like Google Maps can so is good if you're not actively listening to Spotify or something.

<!-- -->

    Start Tracking Driving (2)
        A1: Wait [ MS:0 Seconds:3 Minutes:0 Hours:0 Days:0 ]
        A2: aTimeLogger [ Configuration:Stop running and start Driving Timeout (Seconds):0 ]
        A3: Wait [ MS:0 Seconds:4 Minutes:0 Hours:0 Days:0 ]
        A4: Say [ Text:I'm tracking your driving now Engine:Voice:default:default Stream:3 Pitch:5 Speed:5 Respect Audio Focus:On Network:Off Continue Task Immediately:Off ]

The stop driving task is pretty much the same, but A2 is reversed so it's Stop driving. Pretty simple. Make sure you actually save your changes as I managed to close them without saving.

Now you need to create some profiles that trigger based on Android Auto being active or not. The best way I found to do this was checking the variable %UIMODE and seeing if it was set to 'car' or not. This is set by Android Auto so its a good indicator as to whether I am in the car or not! Maybe there's a better way but this works for me.  Let me know in the comments?

![Screenshot\_20180212-140517](/images/screenshot_20180212-140517.jpg)

    Profile: Car Active (7)
        State: Variable Value  [ %UIMODE ~ car ]

    Profile: Car Not Active (8)
        State: Variable Value  [ %UIMODE neq car ]

Both of these profiles are then linked to the above tasks which we previously set up. Now next time you connect your phone to Android Auto it should start time tracking in aTimeLogger and announce over your speakers that it's doing so. As soon as you disconnect (I have to turn the ignition off, and open the drivers door before the phone fully disconnects) it will stop and save that time log. You shouldn't have to do anything further! Enjoy the data.

You might have noticed in some of the screenshots that I am also doing something similar with sleep tracking. To do this, I am using [SleepAsAndroid](https://sleep.urbandroid.org/documentation/tutorials/tasker/)alarm clock with its Android Wear add-on to actually track my sleep.

Tasker is listening for the intents from SleepAsAndroid and starting the timer in aTimeLogger then stopping it for me in the morning when I stop my alarm.
