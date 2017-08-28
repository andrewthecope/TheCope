@@Title=Saturday Blitz: MetroGnome
@@Date=Saturday, 26 August 2017


I'm not particularly busy today, so I figure it's time to BLITZ.

A blitz is when I try to make an entire app in one day. I tried this a [few weeks back](http://www.thecope.net/2017/7/30/proofread) and I completely failed, but try again I must. 

Today's app idea is called "MetroGnome", a haptic metronome app for the Apple Watch. I have been practicing the piano solo version of [Rhapsody in Blue](https://www.youtube.com/watch?v=nH9pU7z1NVk) over the past few months, and I've been wanting a metronome watch for the more difficult sections. I own a metronome, but wouldn't it be great to have my watch vibrate to the beat? 

Watch extensions for metronome apps do exist, so first things first, I'm going to check them out.

I'll be back.


### Update: 2:34pm

Well crap. Some app reviews seem to indicate that the metronome watch apps don't work when the watch screen is off. I'd imagine that this is a limitation of watchOS. For battery saving, I'd assume.

I'll look for a workaround. Maybe this has changed in watchOS 4? Maybe there's some hack I can devise? 

Off I go on a journey to save the Blitz.


### Update: 2:34pm

Crisis averted. It isn't immediately obvious, but watchOS allows background haptics during a current workout session. Enabling background haptics in watchOS, is a three step process:

1. Enable HealthKit in the app capabilities.
2. In the watch extension plist, add the `WKBackgroundModes`  key with a value of an array containing a `workout-processing` string.
3. In the watch extension plist, add the `UIBackgroundModes` key with a value of an array containing a `audio` string.

Would this pass app review to use for a metronome app? Probably not. But for a Blitz, it's a great solution.

### Update: 4:05pm

Ok, here's comes the fun part: actually making the app.  The app has 4 amazing features:

* A great name: "MetroGnome"
* Haptic metronome 
* Tap watch screen to set tempo
* Increment tempo with Digital Crown

Conveniently enough, I have already named my XCode project and set up the haptics, so only two more features to go.

First I'll tackle the tempo setting feature. I want to be able to tap my watch a specific pace and have the metronome calculate the BPM for me.  To do this, I will time the length of time it takes for the user to tap 4 times, and set the appropriate BPM. 

The math involved in calculating beats per minute took an embarrasingly long time for me to figure out, but here it is:

```
4 Taps   60 sec   4 taps
------ * ------ = ------ = # Beats per Minute
# Sec.   1 min.   # min
```


Here I go.

### Update: 8:51pm

Ok, sorry. Got delayed drinking wine with my mom. But I'm back.

### Update: 10:10pm

It works! ...pretty well anyway! I'm having quite the lovely evening working on this, but there is an ever-growing threat of getting sleepy. I'll start work on the digital crown feature, but if you don't hear from me, It is because I drifted off to a sleepy oblivion.

### Update: Sunday, 2:36pm

I didn't last very long last night. About 10 minutes and I called it quits.

I have a free hour or so, I'll continue working my important, world-changing work on MetroGnome. 

I am hoping to enable the users the ability to increment the metronome using the watch's Digital Crown. I suspect this will be very simple (he said naively). 

