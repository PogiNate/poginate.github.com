---
layout: post
title: "tmux and Octopress"
date: 2013-03-21 5:22
comments: true
categories: [writing, nerd fun, CLI] 
---

Naturally, the first thing I did after getting Octopress up, running, and actually *deployed* to a real live server was set up a writing workflow that will make it easy to post to this blog. And by "easy", I of course mean "weird and convoluted, but in a way that makes sense to me". What else would I mean?

The first ingredient in my workflow is [tmux](http://tmux.sourceforge.net/). If you haven't played with it yet you'll find that  it's a fast and easy way to access your project from multiple angles. You'll have one terminal window open and in that one window you can be editing a file, keeping an eye on `top` and running your build tasks all at once, while a second tab has your development server running in it. I discovered tmux using Brian Hogan's [amazing book](http://pragprog.com/book/bhtmux/tmux) and haven't looked back. 

The second part of the recipe here is [tmuxinator](https://github.com/aziz/tmuxinator), a nice little ruby app that lets you set up tmux layouts in `YAML` instead of writing the commands out as actual tmux commands, like so:

{% gist 5212311 %}

You can see I have `rake preview` and `top` running on a "background" tab, so I can preview the site, and `vim` running on the first tab with a couple of regular old `zsh` panes at the project root and at the `_posts` directory, so I can issue other commands to the system and use Marked.app to preview my posts, etc. etc.  

Obviously I haven't been using this particular setup for all that long yet, but it's got a lot of promise. I'm pleased with how it's turning out.
