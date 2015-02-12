---
layout: post
title: Machine Learning & Prediction.io
tags: [Machine Learning, Prediction.io]
---

Over the last 48 hours, I have taken a first dive into Machine Learning.  At [Hack Reactor](http://www.hackreactor.com), the final thesis project is the culmination of all your work.  My group -- [Sasha Bayan](https://github.com/SashaBayan), [Eric Benson](https://github.com/ericbenson), and me -- has decided to build a music recommendation engine focused on new music discovery.  

[Machine Learning](http://en.wikipedia.org/wiki/Machine_learning) quickly became the focus of how we would do this.  At its core Machine Learning is about software that can learn from data.  It can show you relationships between data (what things are alike and what things are not) and how relationships change based on user action.

<!--more-->

## Basics of how ML (Machine Learning) works

With all ML you must seed your server with training data.  This training data is example data that tells the machine what data items are like and dislike.  Based on this training, the machine looks for correlations between the various data points, to find a definition of how things are ranked or classified.  

As an example, let's say that the below is the data set:

```
Song A - 1997 5 mins Jazz
Song B - 2005 3 mins Jazz
Song C - 1997 2 mins Hip Hop
Song D - 2014 2 mins Pop
```

We could then train the machine as follows:

Song A is like Song C

The machine will look across this data and come to the conclusion that songs are alike when they are made in the same year.  

Song B is like Song A

Now the machine will re-weight the value of the year a song was made because these two like songs are not matched by year.  The machine would also provide weight to the same genre becaue of the Jazz similarity.

Song C is like Song D

Now the machine will correlate the length of the songs.  The machine will also have to factor in Song A's length as C and A are alike.  It will also factor in Song B because C is like A which is like B.  

And so on and so forth with more data provided in training being better.

## Prediction.io

There are many, many different algorithms to achieve this.  I am no mathematical expert by any stretch, so I won't venture into the territory of trying to explain them.

In my search, I stumbled across an awesome piece of technology called [Prediction.io](http://prediction.io/).  Prediction.io abstracts away some of the more complex aspects of implementing Machine Learning.  The package is built on top of [Apache Spark](https://spark.apache.org/), [Apache Hadoop](http://hadoop.apache.org/), [Apache Hbase](http://hbase.apache.org/), [ElasticSearch](http://www.elasticsearch.org/), and [Java](https://www.oracle.com/java/index.html).

Prediction.io provides the following three template algorithms for your use:

* Recommendation - using MLlib ALS
* Classification - using MLlib Naive Bayes
* Similar Product - using MLlib ALS and Cosine

MLlib ALS is an algorithm using [collaborative filtering](http://spark.apache.org/docs/1.2.0/mllib-collaborative-filtering.html) to provide recommendations based on users who have similar profiles and actions as you.

[MLlib Naive Bayes](http://spark.apache.org/docs/1.2.0/mllib-naive-bayes.html) is an algorithm that assumes interdependence of the features of the data.  

[MLlib Cosine](https://en.wikipedia.org/wiki/Cosine_similarity) maps the data onto a space and measure the distance between the data points.

This is just a tiny scratch on the surface of what I and my group will learn over the course of the next few weeks.  I am excited for this journey and will write about my future findings.

