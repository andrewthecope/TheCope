@@Title=iOS Automation: Post to TheCope
@@Date=Monday, 28 August 2017


At the beginning of the summer, I purchased a Smart Keyboard Case for my iPad.  It was expensive, but I was allured by the idea of writing blog posts entirely from my iPad. My blog system that is serving this website is pretty convoluted, and iOS is not suited for updating my blog out-of-the-box.  Still, I was determined and inspired by iOS automation aficionados like [Federico Viticci](https://www.macstories.net) to make it work.

Through a series of iOS apps and python scripts, I have a system that I find completely awesome (and delightfully overcomplicated). Here's how it works:

## Working Copy
My blog is run on a engine called [Camel](https://github.com/cliss/camel) created by [Casey Liss](https://twitter.com/caseyliss). It's a static site generator based on some files in a directory. I love the simplicity of this, especially once I configured my webhost (Heroku) to automatically deploy the site when I push a git commit.  

Obviously, with no ([as of right now](https://www.macrumors.com/2017/06/05/apple-new-ios-11-files-app-for-ipad/)) exposed file system in iOS, I needed to find an app where I can commit to github.  I knew Federico Viticci uses [Working Copy](https://workingcopyapp.com), so I bought it. 

With Working Copy, I was able to add new posts and commit to Github. But to do this manually every time I wanted to post required too much friction. So the next step was automating my posting workflow.

## Workflow?
The first thing I tried was the app [Workflow](https://workflow.is) which can send commands to Working Copy via `xcallback-url`s.  The issue is that I personally can't stand the GUI interface for creating workflows. I love that it exists and is more accessible than code, but I'm a programmer and all I wanted to do was write a damned `if` statement.  So I looked into scripting with code on iOS.

## Pythonista? 
The app [Pythonista](http://omz-software.com/pythonista/) is an app that allows you to run Python scripts on iOS. It is incredibly powerful. The app also allows you to run scripts from a share extension and a Today Widget. 

It took some learning and finagling, but eventually I created a script that could publish a generic markdown file into Working Copy, adding the appropriate metadata that Camel requires. 

The problem was, I was using the app [Bear](http://www.bear-writer.com) (which I adore and have been meaning to write about) to write posts. Bear has a funky implementation of Markdown which works great for note taking, but less good for writing in plain Markdown.  Also, the share extension receives plain text, instead of plain Markdown. To preserve my formatting, I needed to export the post as markdown, highlight the text, and then activate the share extension. It was too much hassle, so I abandoned Bear and looked for another app.

## Editorial!
I purchased the writing app [Editorial](http://omz-software.com/editorial/) a while back, but found it too complicated originally. 

 Now that I had more needs out of a text editor, Editorial was perfect for the task.
 
 Editorial is almost unbelievably powerful. The app has three features that I love:
 
1. Everything is customizable. I was able to get the writing experience to be just right.
2. You can preview posts with custom CSS. Just swipe right! I added the stylesheet I use for this website, so I can see exactly how it will look on thecope.net in the preview.
3. In-app workflows that you can create with the GUI interface or by writing a python script (Editorial is created by the same guy who created Pythonista). 

After I played with Editorial, I had all the pieces for my perfect blog-writing setup.

## The Final Workflow
1. Create a new post in Editorial
2. Write a regular post. No need to add Camel metadata. Just type.
3. Run my "Post to TheCope" workflow by typing `[colon]post` (I can't write it here without setting it off)

Automatically, the script adds the camel metadata (the title and today's date), posts it in the correct place in Working Copy, and appends "Posted to [link]" to my document in Editorial.

If I run the script again, it will update the post, even if I'm editing on a different day. 

The whole thing is quite slick. Perhaps it's more complicated than it needs to be, but I'm delighted to have it all set up. 