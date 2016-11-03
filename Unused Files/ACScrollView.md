@@ Title=Optimizing a  Paged UIScrollView
@@ Date=August 7th, 2016

Here's a Learn Your Lines support email I received a couple months ago:
>Andrew,<br>
>Slow as sin. Fix.

Nice and concise.  Here's what that email was probably  referring to (from version 2.0):
[Picture of loading the ThreeModesViewController]

Depending on the amount of text specified to load, selecting text to memorize could take a couple of seconds while blocking the main thread--certainly not my best work. The solution turned out to be fairly tricky. The big problem, I discovered, was programmatically creating  two large `UIScrollView`s for Read and Memorize modes. 

I attempted to fix this in multiple different ways, and after much fiddling, I got something working.  

For vanity reasons, I named my solution `ACScrollView`.  I figured that since these scrollviews are paged (meaning you only see one panel at a time), there's no reason to load all the pages at once. Better would be to load one at a time as you scroll through.

#ACScrollView
I just wrote out a long and confusing explanation, but after realizing that none of it was very interesting, I made little pictures instead.  


 ACScrollView contains only three panes which are reused as the user scrolls. Once the user finishes scrolling, the scrollview reloaded the unseen scroll views and jumps back to the center pane. To the user, nothing looks out of the ordinary, except that the scrollview can contain a huge amount of pages while maintaining a constant load time /[O(1) if you are so inclined/]. Infinite Scroll is also enabled by this method, meaning that the user can keep looping through the pages while scrolling forward or backward, which is works very well for Learn Your Lines, and could be useful for many other situations. 
 
 For Read Mode, I expanded ACScrollView to 2 dimensions, thus requiring 5 pages to be loaded at a particular time. The picture below explains it better than I ever could. 

I have posted the generalized code for ACScrollView on my github. Maybe it will be of use to someone out there. 

