---
layout: post
title: Hack Reactor - Week 4 Day 2
tags: [Hack Reactor, Node, Azure]
---

![Chatterbox]({{ site.url }}/assets/Chatterbox.png)

Woot!  A super basic chat app built in 4 days! 

See more here:  [Chatterbox](http://nzchat.azurewebsites.net) 

<!---more-->

Highlights of the day:

* Node
* Azure

### Node

As you can see above, [Neil Lokare](http://www.neillokare.com/), and I finished the server and connected the front end.  So the front end was a 2 day sprint to build the visuals and link to an existing web server.  The Node sprint was 2 days and had us replace the back end with our very own server.  

It's amazing that we can get something like this up live in 4 days.  This is a full app that responds to user action and input and stores that data to the server.  Obviously, not super robust, but a great example of what can be done.

### Azure

After finishing the server piece, we took the client end and loaded that onto the server as well.  This worked locally after much debugging to account for the relative location of various scripts and dependencies.  
Then we too the next step of deploying our server and client on a live website.  We created an instance on [Microsoft Azure](azure.microsoft.com).  This required some changes to our code to pick up the website address.  We also had a nasty bug where our data was reading from the wrong location.  After fixing this, the site is live and I feel like I have learned a ton by getting this out to the world.  

Azure offers great power and flexibility that we have just scratched the surface of.  There were some headaches through the process, but it was all learning.  I'm glad to have gone through it and I think that Neil and I will be better prepared for the deployment sprint later on.

Wow!

I'm pumped!  Exciting to have a live product that you can look at and interact with.  Exactly why I am at Hack Reactor.  

