---
layout: post
title:  "On Building a CLI Gem"
date:   2016-09-27 11:50:30 +0000
---


This project, more than any of the others to date, was like building a house: Beginning with the end in mind - along with scope adjustments and obstacles along the way. At long last, the working gem can be found [here](https://rubygems.org/gems/seattle_events), at RubyGems.org. Here is the general process I followed:

**Creating the blueprint: Imagine and decide what to build**

Before anything else, I had to plan my gem by deciding what value I wanted it to provide with its use and how I wanted the user interface to operate. I decided on a command line interface (CLI) for viewing learn-to-code events in the Seattle area. The first level would provide a list of upcoming events and the second level would provide details of those events upon user selection.

**Laying the foundation: Start with the project structure**

I used Bundler (http://bundler.io/rubygems.html) to create the gem file structure pictured ([here](http://imgur.com/aBoSXPQ)).

**Framing the house: Specify dependencies**

The place to begin was with the entry point – the file run. I created the executable file (“seattle_events”) within the bin directory where program loader must learn what command to use to execute the file. In this case, I used the shebang operator #!/usr/bin/env ruby to tell the bash or operating system to use the ruby interpreter.

Next, ensure that all dependencies were in place. This was tested by placing a simple piece of code (“puts ‘Hello world.’”) in the executable file to test that all files and pieces of the program were “talking” to each other. When I ran ./bin/seattle events and saw the return, “Hello world,” I knew that my executable was working.

**Building the walls and roof: Build the CLI interface**

With the basic functionality of the base gem established, I could begin to build the program itself. This involved creating basic methods that mimicked the functionality of my program and "stubbing out" the interface. In other words, I placed placeholder information that would later be replaced by methods that would output as planned.

I wanted my program to work as follows:

Have an event list formatted as below:

1. Fri Sep 16 – Dev Bootcamp – “CoWorking at Dev Bootcamp”
2. Mon Sep 19 – Learn to Code - “Workshop: Introduction to HTML and CSS (9.19)”

Have a user menu allowing a user to

* pick a numbered event for more details
* make a reprint of the list
* exit the program

**Install the plumbing and ductwork: Outline methods and find objects**

Getting more granular, I had to ask myself, "what are the attributes of a list object?"Keeping it simple, the attributes I chose were :date, :name, :time, :description, :rsvp_url. I gave each of these an attr_accessor and set to work getting hard-coded objects to flow through the program as I wanted. You can see an example of the stubbed out code [here](http://i.imgur.com/MJRxhIf.png).

It was at about this time where I realized that the scope of the project was beyond what was efficient to build my first gem. I needed to create a "Minimum Viable Product," working out the initial kinks to produce the product, and iterate improvements upon the gem. So I went from wanting to scrape all of the many Seattle-area learn to code meetup sites to focusing on one: Galvanize's Learn-to-Code Meetup.

**Install the electrical lines, build the inside, and make it open to the public**

Finally, I programmed to pull data from the website and enable the program to instantiate new objects from real data. Then, I built and published the gem according to rubygems.org. Publishing in itself was a challenging process to understand errors that came up as the code was brought into different environments. Users identified bugs that had to be fixed, which was invaluable.

After all is said and done, building seattle_events.gem was a process well worth going through. With the "base model" built, I can start the remodel.

**References:**

[RubyGems.org: Make your own gem](http://guides.rubygems.org/make-your-own-gem/)
[RubyGems.org: Publishing your gem](http://guides.rubygems.org/publishing/)
[Using Bundler with Ruby Gem Gemspecs](http://bundler.io/rubygems.html)

