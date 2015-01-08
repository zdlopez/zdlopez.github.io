---
layout: post
title: Hack Reactor - Week 4 Day 3
tags: [Hack Reactor, Node, Algorithms, Cron, Entrepreneur Club]
---

Highlights of the day:

* More Node
* Algorithms - Powersets
* Cron
* Entrepreneur Club

### Node

I really like Node and the server process in general.  It just makes a ton of sense to me and it is very satisfying to see info from the server reaching the client.  I am starting to think I am more of a back end guy.  We will see as we have databases and the like coming up soon.

<!--more-->

### Algorithms - Powersets

We had a toy problem today on [powersets](http://en.wikipedia.org/wiki/Power_set) of a given string.  This was a reminder that I need to study up on mathematical problems.  These should come more easily.

### Cron

[Cron](http://en.wikipedia.org/wiki/Cron) is a unix/linux utility that allows for scheduling of jobs in the background on the computer.  This is powerful, but we had a little bug and I wanted to post about for others sake. 

All paths must be absolute and not relative.  This includes calls to applications.  In our case, we needed to call Node on a javascript file that would execute and scrape some web data.  Because of the need for absolute paths, we had to know where Node was installed.  Usually, this is at /usr/local/bin, but this isn't always the case.  To find out, execute the following in terminal:

    bash node -v

This will report back the absolute path which you can use in cron.  Yay!

### Entrepreneur Club

Great talk today by Kiran Rao and Todd Skinner of HR 23.  They talked us through some funding examples and what different positions would mean through funding rounds.  Very enlightening.  

