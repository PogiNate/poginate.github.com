---
layout: post
title: "Douglas Adams and JavaScript"
date: 2014-10-06 15:20:18 -0600
comments: true
categories: [programming, short, JavaScript, math]
---

I was brushing up on some JavaScript for work and came across a problem that has bugged me before: testing for `NaN`[^notANumber]. I've never dug too deeply into this one, I've just known that if you try something like this:

``` javascript
	var a = NaN
	if (a == NaN){
	   //a is NaN, do something
	}
	else{
	   //a is a number, do something else
	}
```

The code would always do something else. so I usually found a different way to solve the problem. 

Today I actually dug into it and found that in JavaScript the value `NaN` has some odd properties:

1. It's a number.
2. It is the one value in JavaScript that can never equal itself. 

So that's annoying, but actually lends itself to a very easy solution: if you want to test if a variable is `NaN` you can test it like this:

``` javascript
	if (a !== a){
		// a is NaN
	}else{
		// a is a number
	}
```

But people who are good at JavaScript already know this. This is not news. 

What struck me about this is that Douglas Adams invented a word for this kind of value: 

> ... a recipriversexcluson, a number whose existence can only be defined as being anything other than itself. 
> Douglas Adams, *The Ultimate Hitchhiker's Guide to the Galaxy (p. 345). Random House Publishing Group. Kindle Edition. *

Somehow this made me actually like JavaScript more. 

* * *

[^notANumber]: If you don't know, `NaN` is a special value meaning "Not a Number" and is used to check if the variable you're working with actually has numerical data.