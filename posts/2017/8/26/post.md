@@Title=Saturday Blitz: MetroGnome
@@Date=Saturday, 26 August 2017
I'm not particularly busy today, so I figure it's time to BLITZ.

A blitz is when I try to make an entire app in one day. I tried this a few weeks back and I completely failed, but try again I must. 

Today's app idea is called "MetroGnome", a haptic metronome app for the Apple Watch. I have been practicing the piano solo version of Rhapsody in Blue over the past few months, and I've been wanting a metronome watch for the more difficult sections. I own a metronome, but wouldn't it be great to have my watch vibrate to the beat? 

Watch extensions for metronome apps do exist, so first things first, I'm going to check them out.

I'll be back.


Update: 2:34pm

Well crap. Some app reviews seem to indicate that the metronome watch apps don't work when the watch screen is off. I'd imagine that this is a limitation of watchOS. For battery saving, I'd assume.

I'll look for a workaround. Maybe this has changed in watchOS 4? Maybe there's some hack I can devise? 

Off I go on a journey to save the Blitz.


Update: 2:34pm

Crisis averted. It isn't immediately obvious, but watchOS allows background haptics during a current workout session. Enabling background haptics in watchOS, is a three step process:

1. Enable HealthKit in the app capabilities.
2. In the watch extension plist, add the WKBackgroundModes  key with a value of an array containing a workout-processing string.
3. In the watch extension plist, add the UIBackgroundModes key with a value of an array containing a audio string.

Would this pass app review to use for a metronome app? Probably not. But for a Blitz, it's a great solution.

