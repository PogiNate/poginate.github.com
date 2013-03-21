---
layout: post
title: "tmux and Octopress"
date: 2013-03-20 22:10
comments: true
categories: [writing, nerd fun, CLI] 
---

Naturally, the first thing I did after getting Octopress up and running and actually *deployed* to a real live server was set up a writing workflow that will make it easy to post to this blog. And by "easy", I of course mean "weird and convoluted, but in a way that makes sense to me". What else would I mean?

I've been using tmux a lot lately, because it's a fast and easy way to get into your system from multiple angles. I do a lot from the command line, and once I discovered that I can have normal vim commands move me from task to task instead of having multiple terminal tabs open I never looked back. 

The second part of the recipe here is tmuxinator, a nice little ruby app that lets you set up tmux layouts in `YAML` instead of writing the commands out as actual tmux commands. So right now I have a simple tmuxinator file that gives me access to everything I might want to see all at once. I have `rake generate` running on a second tab, so I can preview the site, I have `vim` running on the first tab, and a couple of regular old `zsh` panes open as well, so I can issue other commands to the system and whatnot. 

Obviously I haven't been using this particular setup for all that long yet, but it's got a lot of promise. I'm pleased with it.
