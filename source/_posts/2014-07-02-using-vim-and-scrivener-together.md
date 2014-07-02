---
layout: post
title: "Using Vim and Scrivener Together"
date: 2014-07-02 15:50:25 -0600
comments: true
categories: [vim, scrivener, writing, painless tmux, markdown]
---

I've been working on [Painless Tmux](http://leanpub.com/painless_tmux) and trying to apply a lot of what I learned while writing [Painless Vim](http://leanpub.com/painless_vim) to make the process easier and more streamlined. 

And one of the problems that I've been beating my head against is this:

Tables. 

Tables in Markdown are a mess. Understandably so, because you're trying to keep everything nicely lined up in plain text, which just doesn't happen. Compound that with proportional fonts in Scrivener and you have something that nobody should ever have to look at. There's a couple of problems here, of course. 

The first is that it's easy for bugs to hide in messy code[^orText], and I've had to run my manuscript files through Leanpub's markdown generator multiple times before I got my tables right. 

So: step one: after putting all the data in a table let's get the table all lined up and looking nice. This is where vim steps in. Specifically, vim with the [Tabular](https://github.com/godlygeek/tabular) plugin. 

Using Tabular I can turn a table that looks like this:


	| Heading 1 | Heading 2 |  
	|  ------ | ------ |  
	| some text | A second bit o' text |   
	| Still more text, this time of a different length | small text	| 

into this:

	| Heading 1                                        | Heading 2            |
	| ------                                           | ------               |
	| some text                                        | A second bit o' text |
	| Still more text, this time of a different length | small text           |

all by typing `:Tab /|` in vim[^learnMore]. 

[^learnMore]: See [Aligning Text with Tabular.vim](http://vimcasts.org/episodes/aligning-text-with-tabular-vim/) for a full explanation of how the plugin works. 

So far so good. But when I paste this back into Scrivener it looks terrible again, because Scrivener uses proportional fonts[^myScriv]:

{% img  /assets/images/kerned-scriv.png Scrivener with proportional text %}

This was an even easier problem to solve, I just didn't realize it it until today. Scrivener lets you use all kinds of rich text features while writing, all of which it ignores when exporting or compiling your text for output. This means, of course, that I can style my tables with a monospaced font and suddenly they line up the way they were supposed to all along. 

{% img  /assets/images/monospaced-scriv.png Scrivener with Monospaced text %}

But changing the fonts manually every time I make a table is a drag. Enter the "presets" feature that Scrivener uses. Its basically the Apple "Styles" menu, but enhanced and made more Scrivener-like. All I had to do was highlight the monospaced section, then in the menu go to `Format->Formatting->New Preset From Selection` and now I can make any of my text nicely monospaced with the click of a button. And while I was at it I re-styled the "Body" preset to be the the way I (currently) like it. 

So there you have it: a couple of simple, common sense tips for making tables less of a nightmare in your Markdown manuscripts. Enjoy!

* * *

[^myScriv]: Sure, you *could* use monospaced fonts in Scrivener, but not in *my* Scrivener. Unless I'm writing code I like my fonts properly kerned, thank you. 

[^orText]: or semantically marked text. Stay with me here.
