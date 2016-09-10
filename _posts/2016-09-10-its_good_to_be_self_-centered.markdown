---
layout: post
title:  "It's good to be "self"-centered"
date:   2016-09-10 05:38:12 +0000
---


After some mind-bending Ruby labs and great discussions around "self," a look at the concept is due. Helpful to readers? I hope so. Cathartic venting session? Definitely.

So, besides being the inescapable concept that Ruby mastery demands we understand, what is "self" anyway?

Starting with the negative, "self" **does not belong to a particular object**, so it cannot be assigned. Instead, it **points to the object** that "owns" the currently executing code. Most often you won’t need to use **self** explicitly, since you can call methods directly from inside other method definitions(1).

Here is a summary and some examples, below:

<a href="http://imgur.com/fGSJEb5"><img src="http://i.imgur.com/fGSJEb5.png?2" title="source: imgur.com" /></a>





Elaborating on the use of **self** in modules:






<a href="http://imgur.com/MPfZQqd"><img src="http://i.imgur.com/MPfZQqd.png?2" title="source: imgur.com" /></a>

I'll save the use of **self **in metaclasses for another post. In the meantime, coding on!


**References and resources**

(1) [Why's Poignant Guide to Ruby pdf ](http://www.rubyinside.com/media/poignant-guide.pdf)

http://blog.honeybadger.io/ruby-self-cheat-sheet/

[Why's Poignant Guide to Ruby: Book and Resources](http://poignant.guide/book/)
