---
layout: post
title: "Introducing A.K.A.: The Alias Manager"
date: 2013-04-12 11:33
comments: true
categories: ['dotfiles','software','self-promotion', cli, ruby]
---

One of the joys of moving from a Windows machine at work to OSX is that I'm back to having access to the unix command line. The downside, of course, long commands that I [usually get wrong][1]. 

Which is why I spent some time a few weeks ago creating [A.K.A.][2] Simply put, A.K.A. is a simple way to manage all the aliases that you usually put into your shell of choice's startup file without editing your dot files by hand or cluttering up your profile when you could be cluttering up a completely separate file. 

Now all you have to do is add `source ~/.alias` and use this script to keep everything nice and organized.

Again, it's a simple difference; If you know what aliases are you probably aren't afraid of editing dot files, but `aka` removes the friction of pulling up your favorite editor, finding where all your aliases are, saving, etc. Everything is a single command issued right at the prompt, all the saving and moving around is handled for you. The result is that I have far **more** aliases, and far more **useful** aliases, because I can add them or change them without breaking my flow. If I realize that I hate typing `git status` I just run `aka -a gs "git status"` and now I've got a much shorter version of that command. The downside, of course, is that I get intensely frustrated using anyone else's computer where `gs` doesn't work. But I can cope with that.

My favorite (slightly under-documented) command is `aka -L`, which outputs a nicely formatted list of all your aliases and what they do when you run them. It's a simple thing, but I like it.

In the event that you actually decide to use this feel free to put suggestions or feature requests or comments either on this page's comment line or on the [github page][3]. 

[1]:  http://xkcd.com/1168/
[2]:  http://natedickson.com/A.K.A./
[3]:  https://github.com/PogiNate/A.K.A.

