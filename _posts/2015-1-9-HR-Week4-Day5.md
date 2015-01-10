---
layout: post
title: Hack Reactor - Week 4 Day 5
tags: [Hack Reactor, Express, MySQL, SQL]
---

So much new today:  Databases and a new server fraamework. New sprint started with Benoy Maniara.

Things are still fast furious.

Highlights of the day:

* Express
* MySQL

### Express

[Express](http://expressjs.com/) is framework that makes the node server easier to use.  Still wrapping my head around this one as there is a lot different in the syntax and how it handles requests.  

In essence, a lot more is compartmentalized, so you end up with much more modular code.   

<!--more-->

### MySQL

[MySQL](http://www.mysql.com/) is an open source database management system that uses [SQL](http://en.wikipedia.org/wiki/SQL), or Structured Query Language.  SQL is the language that you use to interface with the database.  

As an example, if you have a database with a table called "users" storing "username" and "age", the following will give you the users who have an age over 25.

```SQL
SELECT * FROM users WHERE age > 25;
```

SQL is probably one of the few languages I remember from college.  Databases make sense to me and we have been able to get the server connected to the DB and writes are happening.

Our next steps are to fully understand express and clean up our SQL markup. 
