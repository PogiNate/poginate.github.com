---
layout: post
title: "(Mostly) MultiMarkdown Blogging in Octopress"
date: 2013-04-09 09:55
comments: true
categories: [MultiMarkdown, Octopress, Blogging]
---

So, my big concern in moving over to [Octopress][2] was the lack of MultiMarkdown compatibility. Specifically the lack of footnotes. I *think* in footnotes a lot of the time[^1]. 

So it was a definite problem to go to something limited to vanilla markdown. I did a few million hours of web searching to find a way to use MultiMarkdown as my renderer, but for some reason Jekyll is surprisingly resistant to the idea, so I gave up.

For a while. I'm not good at actually giving up. I had made my peace with using non-footnoted code for blogging and had moved on, until I noticed that [Brett Terpstra][1], who documented his own move to Jekyll based blogging a few months ago, had footnotes aplenty on his blog[^2]. So I asked him how he was pulling that off.

Here's his answer, in it's entirety:

> I just use Kramdown as my processor. Works way better than Maruku or Rdiscount for me.
> -Brett

That's it, folks. I made a single change to my `_config.yml` file:

{% codeblock kramdown now lang:yaml%}
markdown: kramdown
{%endcodeblock%}

Bingo! Footnotes[^3] now work and you get to jump around a lot more when you read my blog.

So that's it really. If you've been looking for a way to use MultiMarkdown features in  your Octopress blogging the problem is really much simpler than you thought. Direct your thanks to Brett.

[^1]: All the other MultiMarkdown features are amazingly useful as well, but footnotes are just integral to my writing.

[^2]: I also knew that he's a big fan of MultiMarkdown, seeing as he's the creator of [nvALT][4], [Marked][3], and apparently [worked][5] with Fletcher T. Penny on the icon for [MultiMarkdown Composer][6].

[^3]: And a lot of other very nice features.

[1]:  http://brettterpstra.com/
[2]:   http://octopress.org/
[3]:   http://markedapp.com/
[4]:   http://brettterpstra.com/2012/02/28/nvalt-2-2-public-beta/
[5]:   http://multimarkdown.com/faq/icon
[6]:   http://multimarkdown.com

