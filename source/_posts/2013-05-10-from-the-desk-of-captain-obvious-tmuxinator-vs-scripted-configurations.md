---
layout: post
title: "From The Desk of Captain Obvious: Tmuxinator vs. Scripted configurations"
date: 2013-05-10 10:38
comments: true
categories: [tmux, cli] 
---

I've been using [Tmuxinator](https://github.com/aziz/tmuxinator) for a while now to put together tmux sessions that I can run quickly and easily from the command line. I've even set up an [AKA](http://natedickson.com/blog/2013/04/12/introducing-a-dot-k-a-dot-the-alias-manager/) shortcut, abbreviating `tmuxinator` to `tor`, making it much easier to create new scripted sessions. But recently I discovered an odd thing when I detached from a session created by tmuxinator: they don't show up in my list of sessions when I run `tmux ls`. 

So I played with it a bit more. I could run `tor config1` and get a session laid out according to configuration 1. I'd then detach and create a session by hand, and do the following:

	$ tmux new -s bar -d
	$ tmux ls
	bar: 1 windows (created Thu May 9 07:35:02) [160x39]

Well that's odd. So I'd try 

	tmux attach -t config1

and it would say it can't find the session.  Out of curiosity (did I kill the session instead of just detaching?) I'd run 

	tor config1

again, and I would be back in my already-running session.

Okay, most of you have already gotten here ahead of me. When you run Tmuxinator it's issuing commands from ruby, not from your user session. The tmux process that ruby uses is a child process of ruby, not of your shell. This is fine if you create all your sessions from Tmuxinator, but if you start standing up impromptu sessions just because, or if you have decided to have tmux start whenever your terminal opens it means that your Tmuxinator sessions and your non-Tmuxinator sessions are on totally different servers, so you can't use `<prefix>)` to switch between them.

So I decided to bite the bullet and move my Tmuxinator sessions over to independently executable scripts. It's more steps, not quite as pretty, but the commands are all sensible, and now sessions I create using my scripts are visible on my "main" tmux server. And I'm free of one more external dependency, which is nice.