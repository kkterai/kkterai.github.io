---
layout: post
title:  "Sessions: Transforming Stateless into Stateful"
date:   2016-10-17 16:29:01 -0400
---


Say you are visiting your favorite online retailer for a specific unique item and start entering your login data. You login but find that the site has already forgotten you - and now you are unable to shop for your mom's birthday present that must ship today! Sounds like a frustrating...and fortunately very unusual situation, right? 

Although a smooth online shopping experience can be taken for granted, this would not be unusual if we only had HTTP to work with.

**First, what is HTTP?**

HTTP provides a standardized way for computers to communicate with each other. Specifically, it defines how clients' request data will be constructed and sent to the server, and how servers respond to these requests.

In short, HTTP is

* the foundation for data communication for the World Wide Web. 
* a generic and stateless protocol which can be used for other purposes.
* an application-level protocol for distributed, collaborative, hypermedia information systems. 
* a TCP/IP based communication protocol, that is used to deliver data (HTML files, query results, etc.) on the World Wide Web

As a result of HTTP being a stateless protocol, the server and client are aware of each other *only during a current request.* Afterwards, both of them forget about each other. Due to this nature of the protocol, **neither the client nor the browser can retain information between different requests across the web pages**.

**Enter Sessions **

Sessions are a way in which web and application servers maintain state; it's basically just a hash that stores data on the server and passes that data to the client as a cookie. Session cookies, available during a user's current session, are stored in the browser while persistent cookies, storing information relevant to future visits, is stored on the user's computer. 

Data stored in the session can be accessed in the same way as any hash. In Sinatra, the "session hash" is set up to store the `user_id` and sessions are enabled within the controller by adding two lines in the configure block:

<a href="http://imgur.com/LOmh7Ps"><img src="http://i.imgur.com/LOmh7Ps.png?1" title="source: imgur.com" /></a>

When sessions are enabled in an app, every controller action has access to the session hash until the session is ended (i.e. the session hash is cleared). Continuing with the initial example, users can shop in peace, moving from page to page within an application without being "forgotten," innumerable shopping crises averted.


References:

[TutorialsPoint](http://www.tutorialspoint.com/http/)
[Learn.co: Sessions and Cookies](https://learn.co/tracks/full-stack-web-development/sinatra/sessions/sessions-and-cookies)
