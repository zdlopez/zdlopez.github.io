---
layout: post
title: jQuery Event Listeners on Dynamically Created DOM Elements
tags: [jQuery, DOM]
---

![jQuery]({{ site.url }}/assets/jquery.gif)

jQuery is a powerful way to manipulate DOM (Document Object Model) elements on a webpage.  I will cover a common mistake when trying to build a website with dynamic content that responds to user interactions.  

In the following image, which is a sort of twitter clone, new tweets are generated and displayed to the page.  The user of the site is allowed to click on any user name to see that user's full stream of tweets.  

<!--more-->

![jQuery]({{ site.url }}/assets/twittler.png)

As these new tweets are created, it would be normal to assume that we need an event listener on these.  Let's look at some code. 

Here is how new tweets are set up:

    var $tweet = $('<div class="tweet col-md-12"><div class ="user col-md-8"><a href="#" class="link '+ tweet.user + '">' + '@' + tweet.user + '</a> ' + tweet.message + '</div><div class="time"> posted at ' + tweet.created_at.toLocaleTimeString() + '</div></div>');

The important part to note is that these "div"s have a class of "tweet" and the anchor (the "a") has a class of "link".  These will be our likely suspects to utilize to get our page to respond to user clicks.

We could structure a listener like this:

    $('.link').on('click', function(e){
      //do stuff
    }); 

This sets up a listener on elements that have the "link" class.  Anytime there is a click registered this code should execute, but it doesn't.

In this case, you have to remember that listeners are set up on the loading of the website.  As you are tracking dynamic content, this content may or may not exist at document load.  This means the listener may not be attached to anything.  You could try this on the "tweet" class as well, but you would end up with the same result.

A simple solution would be to add a container for the tweets.  The container can exist on document load and new tweets can be inserted into it.  This could look like:

    <div id="tweetspace">
    </div>

Then we can add the tweets like so:

    $tweet.prependTo($tweetspace); 

With this change to the html and adding our tweets to our new "tweetspace", we can modify our listener to act on this container.

    $('#tweetspace').on('click', 'a' function(e){
      //do stuff
    }); 

In the above code, two things changed.  First, the listener is targeting "tweetspace" which exists on document load.  Then the second argument to "on" is now "a", allowing us to only register clicks that are in "tweetspace" and are of an element type of 'a'.

## Summary

* Think through what exists and when
* Add a listener to a container that holds the dynamic content and not the content itself

In these first few weeks of Hack Reactor, I would say that this sort of issue has cropped up on half the projects.  An important lesson to learn.

