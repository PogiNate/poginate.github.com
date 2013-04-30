---
layout: post
title: "Battery Status in tmux"
date: 2013-04-30 10:25
comments: true
categories: [cli, tmux, ruby] 
---

While I usually work plugged into power and a monitor and all that good stuff, there are times where my MacBook Pro and I need to go off the grid for a while. During those times I've found that it's easiest to have a terminal window fullscreen and do everything via the command line. That way I don't really need a mouse at all and I can keep my hands on the keyboard doing whatever it is I'm doing that day. If I need any of my GUI apps [Alfred](http://www.alfredapp.com/) is always right there to help me out, again, without using the trackpad. 

{%pullquote%}
The one [^minor] problem is that when an app is full screen you can't see your battery percentage, and it's possible to actually run yourself out of power without really knowing how close you are. Okay, I admit that it's a minor problem, and highly unlikely. So {"let's be honest: This entire project came about simply because I wanted to add some graphics to tmux."} Ever since I learned you can use [Apple's Color Emoji] set in terminal windows I've been looking for even a semi-useful way to do so. 
{%endpullquote%}

What inspired me was a little section at the end of [Brian Hogan's tmux book](http://pragprog.com/book/bhtmux/tmux) about adding battery status to your status bar at the bottom of tmux windows. He links to [a script](https://raw.github.com/richoH/dotfiles/master/bin/battery) that works cross platform, but that's not really what I wanted. As Steve Jobs once said, if you're working cross platform, you're not getting the most out of your specific platform[^kinda]. So I decided to write my own script.

doing a little bit of searching revealed this lovely command that appears to be OSX specific:

	pmset -g batt

running this will give you a result like this:

	Currently drawing from 'Battery Power'
	  -InternalBattery-0     100%; discharging; 6:44 remaining

As you can see, this string is just begging to be pulled apart via regular expressions. So that's exactly what I did. The first line is super easy to parse; there are only two possible strings (as near as I can tell) that go between the single quotes: 

- Battery Power
- AC Power

So grabbing that string gives us a simple way to know where our energy is coming from. I didn't want to just *say* "Battery" or "AC", though, so I'm using the emoji for battery and lightning respectively[^plug].

On the second line there are three things we want to know: how charged the battery is, if it's charging or discharging (or charged) and how long until it's done doing what it's doing. I decided to represent the charge level of the battery using five stars, because that fits nicely and a 5-star system makes sense to people. I didn't even need emoji for full or hollow stars, they're part of UTF-8, so that was even easier. After a little thought I decided (for now) not to represent the charging/discharging/charged state specifically. I'm still capturing it, I'm just not displaying it.

So a few minutes of ruby hacking later and I have a script that gets me all the info I need and displays it using pretty pictures. Now all I need to do is get it into tmux. Fortunately that was also very simple. This line: 

{% codeblock Display Battery Info lang:bash https://raw.github.com/PogiNate/dots/master/home/.tmux.conf Link to file on Github %}
set -g status-right "#[fg=colour155]#(pmset -g batt | ~/bin/battinfo.rb) | #[fg=colour45]%d %b %R"                                                          
{%endcodeblock%}
runs the `pmset` command and my script and gives me a nice green row of stars and a cyan-ish date, like so:

{% img /assets/images/charged.png Charged tmux status bar %}

And like so:

{% img /assets/images/battery.png Battery power tmux status bar %}

It shows one star empty the moment the battery level falls below 100%, because of math, but I'm fine with that.

So: about an hour's worth of work for something that will technically save me no time at all, ever. According to[ XKCD's chart](http://xkcd.com/1205/), it wasn't worth the time, but I'm still perfectly happy with it. I'm considering updating the script to be more tmux-specific, perhaps even coloring the output based on the charging state, but for now this is good and isn't terribly distracting.

Anyway, the battinfo.rb script is below, my `.tmux.conf` file is on github with all [my other dot files](https://github.com/PogiNate/dots).

{% gist 5490603 %}


[^minor]: very *very* minor

[^kinda]: or [words to that effect](http://www.apple.com/hotnews/thoughts-on-flash/): "The third party may not adopt enhancements from one platform unless they are available on all of their supported platforms. Hence developers only have access to the lowest common denominator set of features."

[^plug]: There is an emoji power plug symbol, but it doesn't show up well on a black background.

[Apple's Color Emoji]: https://en.wikipedia.org/wiki/Apple_Color_Emoji