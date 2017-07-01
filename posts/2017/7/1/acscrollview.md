@@Title=ACScrollView
@@Date=Saturday, July 1, 2017

[ACScrollView on Github](#)

Paged scroll views are an important part of Learn Your Lines. Both Read Mode and Memorize Mode (and Test Mode once I release the new dialogue update) consist of scrollable cards. 

`UIScrollView` has all the features I need, but with one problem: It's too slow to load.  In the original version of Learn Your Lines, it took a very long time to load Read Mode and Memorize Mode if there were too many cards in the scrollview. A feature like "memorize full speech" took up to 10 seconds to load for something fairly long like the "I Have A Dream" Speech. Other than laying out subviews, the app is doing nothing computationally complex, so obviously this was unacceptable. 

The solution is probably obvious to developers who know what they are doing, but I didn't and so it took a while to come up with a good solution:

*Load the cards as you are scrolling.*

In hindsight, I should have known this from the start. It's what Apple does with `UITableView`  and anything else that contains a lot of data. So I wrote a subclass of `UIScrollView` that loads data as the user scrolls. 

In a paged scroll view, the app only needs to load three views at a time: the page the user is currently on, the previous page, and the next page. After the user scrolls, load a new page. When the user reaches the last page, load the first page and you get infinite scrolling without any additional work. 

I've posted my code for this scrollview [on my GitHub](https://github.com/andrewthecope/ACScrollView/). I call it `ACScrollView` for vanity reasons. 

I've written scrollview which scrolls both horizontally and vertically, as well as a two dimensional version that allows the user to scroll both up and down. For now I'm only posting the horizontal version because the other two are messy and you will make fun of me. I'll post these two versions sooner rather than later, but I need to do some refactoring first. 

