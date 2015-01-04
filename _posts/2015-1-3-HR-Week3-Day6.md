---
layout: post
title: Hack Reactor - Week 3 Day 6
tags: [Hack Reactor, Coffee Script, Backbone, Testing, Sinon]
---

Another close of week in the books.  We are now a quarter through the program.  Time has passed by so fast.  This program is so full of information and excitement that I can't really believe all that I have learned and in just how little time.

Today we finished the second day of the Backbone and Coffee Script sprint.  Backbone being new, plus Cofee Script being new, made this challenging and interesting.  It also made it harder to detect exactly where errors were.  Could they be the syntax of Coffee Script, or the Backbone methods?
 <!--more-->

Highlights of the day:

* Testing & Sinon
* The Hack Reactor Talent Show

### Testing & Sinon

My pair, Omar Duarte, and I spent spent a lot of time working through writing tests for our application.  The Chai syntax seems pretty strait forward as you are almost writing english.  

Example:

```coffeescript
assert.strictEqual testHand.score(), 21
```

The above, as you can probably guess, just means that the function testHand.score() has to return a value equal to 21.  This is an assertion that returns true or false.  Using Mocha and Chai together allows for a nice webpage interface of tests like so:

![Testing]({{ site.url }}/assets/testing-mocha.png)

We also used [Sinon](http://sinonjs.org/) Spys to ensure that function were called based on Backbone events and other triggers.  

A spy basically wraps a given function, providing access to you to check different things like # of times of called.  This allows you to test various functionality within your application.  

Sample here:

```coffeescript
it 'should see if the dealer is hits after player stands', ->
    game = new Game()
    player = game.get('playerHand')
    dealer = game.get('dealerHand')

    spy = sinon.spy(dealer, 'hit')
    player.stand()
    expect(spy.called).to.equal(true)
```

This code wraps the dealer's hit function in a spy.  This allows us to use the last line to ensure that this function was called.  

Testing is very useful, but it can also be painful to do it well.

My pair and I ran into a nasty bug based on the way we installed sinon.  I want to point it out here so others may avoid it.  We included the sinon lib file into our html testing page, but the "spy" function was not available.  Apparently with sinon, we need to include the sinon.js file from the "pkg" directory as this one is built with other files included.  Found this out from this helpful blog by [Jake Trent](http://jaketrent.com/post/spies-sinon-chai/).

### The Hack Reactor Talent Show

All I can say is **ZOMG!**  There is so many talented and hilarious people in Hack Reactor.  It is just awesome and reaffirms for me how great this place is.  

There were jokes, improv, songs, and so many of these things included sweet javascript jokes.  So great.  

