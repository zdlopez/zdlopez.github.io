---
layout: post
title: N-Queens Runtimes
tags: [Hack Reactor, nQueens]
---

I thought I would post some N-queens runtimes for all to review.  These were run using our code that utilized the Parrallel.js library to optimize the work across multiple core cpus.  I ran these this morning using my MacBook Pro with a Core i5 at 2.6 GHz and 2 cores.  

The machines at Hack Reactor have 4 cores and we were able to run N=19 in 48.5 mins.

<!--more-->

Here is the screenshot for 10 to 15.

![N-Qeens 10 to 15]({{ site.url }}/assets/N-Queens Parallel 10-15.png)

Here is the screenshot for 16 and 17.

![N-Queens 16 and 17]({{ site.url }}/assets/N-Queens Parallel 16-17.png)

Can't really run much more as the the run time scales pretty fast.  Ultimately, we need to get this distributed across multiple machines.