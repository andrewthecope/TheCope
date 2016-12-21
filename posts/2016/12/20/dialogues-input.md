@@ Title=Dialogues: The Input Screen
@@ Date=December 20, 2016

A few days ago, I began the work to add dialogue support in Learn Your Lines.  I receive an email requesting this feature about once a week and I think it will be fun to make. So I’m doing it. 

In general, dialogues are simpler than regular text.  Memorizing a dialogue is similar to using flashcards. There is a q-line and a line, a front and a back.  The actual memorization part naturally fits the study modes that already exist in the app. The big problem is input.  Inputting the text from a script into the app is tricky. A lot of friction is involved with requiring a user to type hundreds of lines, especially on a touch-screen. 

Here are some of my options:
1. Do my best to create a UI for an input screen and hope that people find it good enough.
2. Allow easy import from plain text. Let users type their lines on another device (in a simple format. Lines separated by newlines?) and paste in as a big block of text.
3. Some crazy-cool image-to-text feature which parses text from an image.
4. Create some web interface to input text, which is synced automatically to the user’s device. 

I think option 1 is unavoidable. There needs to be some kind of form to input on device. I don't think it should be the only solution, but it should exist. 

The more I think about option 2, the more I like it. It allows dialogues to be inputted like speeches and monologues, just by copying a big block of text.  I think I will do this. 

Arguably, option 3 is the ideal. But I'm not smart enough so it's not going to happen. 

Which brings me to option 4.  The combination of 1 and 4 are probably the ideal. Thanks to my work on [Number 2](http://www.thecope.net/2016/11/1/LetUsPoop) , I am fairly comfortable with Apple’s CloudKit, which would simplify the issues with running a cloud service. But I think this is a bigger task than I should take on right now. I will file option 4 away as a future project. 

So off I go to work on new screens. I will report back with the results. 
