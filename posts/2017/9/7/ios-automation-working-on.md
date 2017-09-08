@@Title=iOS Automation: What I'm Working On
@@Date=Thursday, 07 September 2017


After [creating some workflows](http://www.thecope.net/2017/8/28/post-automation) to post to this blog from my iPad, next on my agenda in iOS Automation was automating the task of updating the "What I'm Working On Now" status text in the website header. Naturally, the simpler the workflow, the more often I'll actually use it. 

Having experimented with [Pythonista](http://omz-software.com/pythonista/) previously, I was interested in creating a today widget that would display my current status, and allow me to update the status from the comfort of the widget.

Pythonista's `ui` framework is quite impressive. I created the widget ui with a few lines of Python. It all just worked without issue... with one exception. It turns out that Apple does not allow text input from a Today Widget. Use of the keyboard is not permitted (a dumb policy, in my opinion), and so I had to rethink some things.

  Here's what I ended up with:
  <img src="http://www.thecope.net/widget.jpg" width=100%>
  
  When the widget loads, it pulls the status text and the link from my website source code in [Working Copy](http://workingcopyapp.com). Because I couldn't type directly into the widget, I added a `+` button to pull text from the clipboard. So to add a new status, I just need to copy text in the format `Status Text /someLinkHere`.  The python script will then parse the pasted text and generate html in the form `<a href="/someLinkHere">Status Text</a>`.
  
  To publish the status update, I can press the `✓` button. The python script will add the generated html as a file in my git repo called `workingon.html`. I have updated my blogging engine to add the contents of `workingon.html` to the site header on load. 
  
  And that's it. There's almost certainly a better way to achieve the same result using fancier web technologies, but I like my static website and I love a good overcomplicated workflow. 
  
  I know I'm a little late to the game here, but this automation stuff is so fun. I only wish it were accessible to more people who could dream up workflows without the complications of url-schemes and OS limitations. Someday soon I hope. 