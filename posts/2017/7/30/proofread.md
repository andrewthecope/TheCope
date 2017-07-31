@@Title=Sunday Blitz: Proofread
@@Date=Sunday, 30 July 2017

I’ve decided to spend my Sunday making a new app. I have other projects that are more important to work on, but I’ve been consumed by this idea for a few days now and I figure I’ll be able to make it by the end of the day. We’ll see how it goes. 

And yes, spending an entire weekend day at my computer is proof that I need more friends, but here we are.  

## Introducing “Proofread”
This is my idea: An app that allows users to markup text with an iPad Pro and Apple Pencil with standard proofreading symbols. 

<img src="proofread/symbols.png" width=60%>


The app recognizes the symbols and translates the edits onto the text automatically. I call it Proofread. This is a pretty simple idea, but will certainly be a technical challenge. 

The way I see it, there are three challenges to overcome:

1. Drawing Apple Pencil input responsively. 
2. Developing a system to recognize the markup symbols. 
3. Translating markup onto the text.

I spent some time yesterday thinking about these three challenges, and I have some ideas for each, but I’ll take them one at a time. So first things first, I’m off to learn about the Apple Pencil APIs. 

I’ll report back. 

# Update #1 (Sunday 8:30pm)
Well that took longer than I expected. I was probably naive for thinking I could finish this project by the end of the day, but it’s not my fault. Some issues I ran into:

1. I thought it would be a good idea to download the XCode 9 beta. This delayed me for hours. 
2. The Apple Pencil APIs are much more complicated than I anticipated. I started by watching the [2016 WWDC video](https://developer.apple.com/videos/play/wwdc2016/220/)  on the subject. The nice man on the video made it all sounds so simple. Looking at Apple’s [example project](https://developer.apple.com/library/content/samplecode/SpeedSketch/Introduction/Intro.html), things are more complicated. With another hour or so of trial and error, I ended up with a working drawing engine for the app. 

<img src="proofread/phase1.jpg" width=60%>

Next on the agenda is recognizing the markup symbols. I don’t foresee this being particularly easy. 

I’ll report back. Might go to sleep at some point…

