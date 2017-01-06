@@ Title=Dialogues: Test Mode
@@ Date=January 4th, 2017

The time has come. I have (more or less) finished the [Input Screen](http://www.thecope.net/2016/12/20/dialogues-input), [Read Mode](http://www.thecope.net/2016/12/27/dialogues-read), and [Memorize Mode](http://www.thecope.net/2016/12/30/dialogues-memorize) for Learn Your Lines for Dialogues. In the grand scheme of things, none of this was terribly complicated. I build upon things that already existed within Learn Your Lines. My idea for Test Mode is more involved. Here's what I plan to do.

I view Test Mode as the virtual equivalent to the friend you sucker into helping run lines. This friend will read the q-line, wait for you to say the line, and correct you if you are wrong. Your friend is nice for helping you, but your friend is human and has limited patience. 

Computers are not human and have unlimited patience. This is the opportunity I see in Test Mode. 

So there's three tasks that Test Mode needs to be able to do:

1. **Read the q-line.** Easy enough. I've already implemented the text-to-speech stuff. 

2. **Listen to you say the line and correct you if you are wrong.** This one is far tougher. 

3. **Review the lines you missed.** Should be easy given that I can do 2.

You will notice the crux of the whole operation is the speech recognition capabilities of task 2. Conveniently enough, Apple launched a Speech Recognition API in iOS 10 and it's fairly straightforward to implement. Where I see myself running into problems is comparing the spoken text to the actual line. Ideally, I can show the user exactly what was inserted or left-out in a visual way (the gold standard is Quizlet's [Speller](https://quizlet.com/80082989/spell)). Diff checking algorithms exist, but it gets complicated very quickly when considering punctuation and dictation errors. This will take experimentation to get right. 

If I am able to pull this off, it would be incredibly cool and hopefully very useful. I'm frothing at the mouth to begin. 

I'll report back.  

