---
layout: post
title: "location matters"
date: 2016-01-23 18:45:01 -0700
comments: false
categories: 
---

Sometimes I have a day where I just want to write a damn event binder but this happens instead:

![Just... WHY](http://i.imgur.com/s32cy.gif)

A couple weeks ago someone in LivingSocial slack asked what the diff is between putting script files in the `head` vs lower in the file, below the DOM. I had no hard evidence at the time but had a notion putting the file at the bottom, say just inside the `body` tag, would ensure DOM elements were fully loaded before the script runs.

So today I just spent about an hour beating my head against a wall wondering why a `.click` event wasn't binding.

When this goes wrong, do two things:  
1. Run a `console.log` or `debugger` in the binder to see if it's even binding.  
2. If that doesn't hit, log the DOM element you're trying to hit and check its length.

For some reason, step 2 didn't occur to me for an hour.

__The problem:__  
The script I was calling was coming from Rails asset pipeline and was loading in the document `head`. So, surprise, the length on that DOM selector was a big fat zero.

![So where the hell is it](http://gifsec.com/wp-content/uploads/GIF/2014/04/where-is-everyone-gif.gif?gs=a)

__The solution:__  
Move that sucker into the bottom of my ERB for the time being and wahey, it works!

So yeah. Script location. It's a thing. And now I have some proof documented.

__In other news__  
I'm in the final 36 hours of my staycation. I worked out, hiked, ate a lot of food I really shouldn't have, got caught up on all the _X-Files_ mythology episodes from season 4 - 9, figured out how to make a super awesome old fashioned, and have been giggling at the snowstorms on the east coast. I wish I could jump into the Star Destroyer with its performance snows and school these people.