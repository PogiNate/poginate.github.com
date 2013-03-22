---
layout: post
title: "Vines Through the Garden Wall"
date: 2013-03-22 09:23
comments: true
categories: [python, iOS, Drafts]
---


Apple lives a strange double life. They've always had a strange love/hate relationship with developers: they want great 3rd party apps, but they want everything to be *just right*, and if you don't agree with their vision of *just right* then you're plain wrong.

And over time we've seen that weird divide get weirder on OSX. On the surface you've got Gatekeeper, designed to keep the weeds out of the walled garden, but fire up the terminal, install [Homebrew] and suddenly you've got the whole world of open source software all over your nice shiny Mac, with not a peep out of Gatekeeper. and frankly I think that's fine. If people don't want to worry about their computer and just want to install things from the Mac App Store then let them live that way. But for those of us who kind of like all the wild plants inside the walled garden let us install whatever we want.

Unfortunately iOS doesn't get the same freedom. **All** apps are tightly sandboxed, and absolutely not allowed to talk to one another. You keep your code to yourself and pretend you don't know anybody else exists. The Walled Garden is walled all the way up and down.

Except…there is one crack.

Some blessed engineer decided that it would be good if apps could talk to one another, at least rudimentarily. Using the [Open Url Scheme][open] you can pass commands and strings back and forth between apps. It's a surprisingly open, beautifully object-oriented method of dealing with a common problem. As long as the receiving app knows how to handle the commands sent by the calling app it handles it and you've got a vine through the wall.

A few beautiful wild plants have sprung up using this method of communication to enhance your entire workflow. [Drafts], and it's ultra-literate sibling [Terminology] use it, to great effect. Drafts let you create text and pass it just about *anywhere* to use however you want. Dropbox and Evernote both respond to url schemes to allow you to create new notes. 

But even more amazing is [Pythonista]. Somehow omz software managed to get the entire python 2.7 runtime into iOS, and you can create workflows that send data into and out of your python scripts, again using url schemes. For example, I have a bookmarklet in Safari that works like this:

``` javascript
javascript:window.location='pythonista://my_script?action=run&argv='+encodeURIComponent(location.href)
```
When I find a page that I want to pass into my script (the functionality of which is beyond the script of this article, and is *at the same time* incredibly dull) I just hit that bookmarklet and a few seconds later Pythonista has modified the text and passed it on to Drafts, which in turn can send it on to Dropbox. Suddenly the garden walls don't seem as impenetrable. 

[Homebrew]: http://mxcl.github.com/homebrew/
[open]: http://handleopenurl.com/
[Drafts]: http://agiletortoise.com/drafts
[Terminology]: http://agiletortoise.com/terminology/
[Pythonista]: http://omz-software.com/pythonista/
