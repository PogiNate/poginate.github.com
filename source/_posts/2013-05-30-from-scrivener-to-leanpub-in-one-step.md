---
layout: post
title: "From Scrivener to Leanpub in One Step"
date: 2013-05-30 00:46
comments: true
categories: [Painless Vim, scrivener, writing, automator]
---

I'm working on *[Painless Vim]* in [Scrivener], because I love its organizational capabilities [^2] …or have I mentioned my love of Scrivener before? (yes)

The problem arises when I want to push my text to [Leanpub]. Scrivener has two very good ways to get your text out of Scriv into the world: you can *export* each text as a file, or you can *compile* it into a single document ready to send off to a printer. They've both got their pros and cons, but to really understand them we need a brief detour into how publishing on Leanpub works:

### Brief Detour Into How Publishing on Leanpub Works

to publish your text on Leanpub you put all your chapters or whatever into individual `.txt` files, which you put into a special Dropbox folder called something like `~/Dropbox/name_of_book/manuscript/`. then you include a file called `Book.txt` to tell Leanpub what order the text files should be in when the book is put together. You can also create a `Sample.txt` file that tells Leanpub which text files to put into a free sample that potential buyers can download, and  a `Preview.txt` file that lets you just render a specific part of the book to make sure the formatting looks the way you want it. Okay, that's your brief tutorial on Leanpub.

So, back to getting text out of Scrivener into this folder.

The compile option seems like a great choice at first: it creates a single text file made up of all the text in your document, formatted however you like, and once you've created your compile settings it's a single click operation. 

The problem is with the Sample and Preview options. Since your text is all in a single file you can't pick and choose individual parts of the text to give away for free. You could have two separate compile settings, but that seems very labor intensive.

So, the "export" option is the way to go, right? Every text section in your Scrivener project is exported as a single text file, just like Leanpub wants, you can create `Sample.txt` and `Preview.txt` files and everything is good. 

Well, one problem. Let's say  you've got your book laid out in Folders instead of as just a list of text files in Scrivener. When it exports your book it creates the full file structure:

	Painless Vim
	| 
	+- Part I
	|	|
	|	+- Chapter 1.txt
	|	+- Chapter2.txt
	+- Part II
		|
		+- Chapter 3.txt	 


And so forth. You get the picture. This is a problem because Leanpub doesn't do subfolders; you need all the files to be in the root of the `manuscript/` directory. So, after doing an export from Scrivener I needed a way to flatten out the file system.

### Enter Automator

Here's the fun part. I could have written a ruby script to go through the exported file and copy all the `.txt` files to the `manuscript` folder. But that would have taken *minutes*. Like, *dozens* of them. So I decided to once again let Automator have a crack at it.

And it was **easy**. Automator has gotten a lot more useful since last I played with it[^1], with things like variables and other things you'd expect from a real scripting environment. What's more, I was able to set up my workflow as a "folder action", watching the `~/Documents/Painless/` folder which I created specifically for this purpose. Now I just tell Scrivener to export into that directory and Automator takes it from there. 

The Automator workflow I set up is dead simple:

1. Save the name of whatever just appeared in `Painless` in a variable called `New Folder` [^names] .
1. Get everything in the new folder, recursively
1. Filter that list by file extension (in this case, we only want .txt files)
1. Copy all those text files to `~/Dropbox/painless_vim/manuscript/`, overwriting any existing files.
1. Delete whatever is stored in `incoming`. 

And there you have it. The last step is just to make the export from Scrivener one step shorter, because it doesn't have to ask if you want to overwrite your last export.

There are a lot of advantages to this setup. I can now export a single text file or folder instead of the entire project, and just that file will get overwritten. For single file exports this is nearly instantaneous, opposed to the *three whole seconds* it takes to export my entire project.  I  can also have *all* my files, including my `Book.txt, Sample.txt` and `Preview.txt` managed in Scrivener, which I couldn't do if I were doing the Compile option. 

Over all I'm very pleased with this workflow. It's taken one of the pain points out of writing *Painless Vim*. 

[^1]: at least four years ago

[^2]: Okay, I know it seems odd that I'm writing a book called *Painless Vim* and here I am admitting that I'm using a completely different editor to write it. What's the deal here? The deal is that it's really easy to copy and paste text around between editors (especially using Hog Bay's [QuickCursor](http://www.hogbaysoftware.com/products/quickcursor), but that's an entirely different footnote), and while I do most of the actual writing in vim, I keep the text files in Scrivener for reasons that will be expounded upon in a future blog post.

[^names]:Let's not make fun of bad variable names here, Thank you so much.

[Painless Vim]: https://leanpub.com/painless_vim

[Scrivener]: www.literatureandlatte.com/scrivener.php

[Leanpub]: https://leanpub.com