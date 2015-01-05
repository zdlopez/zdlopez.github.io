---
layout: post
title: nQueens further explained
tags: [nQueens, Algorithms]
---

A few weeks back I posted (and tweeted) the following:

```javascript
function q(n){x=0,a=(1<<n)-1;function i(l,c,r){if(c==a)x++;var p=~(l|c|r)&a,b;for(;p;p-=b){b=p&-p;i((l|b)<<1,c|b,(r|b)>>1)}}i();return x}
```

In this post, I am going to expand the shortened code and explain what's happening.

As a refresher, you can see here for the wiki on [nQueens](http://en.wikipedia.org/wiki/Eight_queens_puzzle).

Here we go, first let's start by adding some line breaks where they make sense. The code was all in one line as line breaks cost characters and would prevent it from being tweetable. 

```javascript
function q(n){
x=0,a=(1<<n)-1;
function i(l,c,r){
if(c==a)x++;
var p=~(l|c|r)&a,b;
for(;p;p-=b){
b=p&-p;
i((l|b)<<1,c|b,(r|b)>>1)
}
}
i();
return x
}
```

Okay, now this is a bit more readable.  Let's comb through and add some indentation.

```javascript
function q(n){
  x=0,a=(1<<n)-1;
  function i(l,c,r){
    if(c==a)x++;
    var p=~(l|c|r)&a,b;
    for(;p;p-=b){
      b=p&-p;
      i((l|b)<<1,c|b,(r|b)>>1)
    }
  }
  i();
  return x
}
```

Now let's add some var declarations, curly braces, and semicolons that were stripped for character count.

```javascript
function q(n){
  var x=0,
      a=(1<<n)-1;
  function i(l,c,r){
    if(c==a){
      x++;
    }
    var p=~(l|c|r)&a,
        b;
    for(;p;p-=b){
      b=p&-p;
      i((l|b)<<1,c|b,(r|b)>>1)
    }
  }
  i();
  return x;
}
```

Now let's transform the single character variable names to meaningful names as follows:

* q : queenSolutions
* n : is the n in nQueens, so it is the size of the board and number of queens to place
* x : numSolutions
* a : all
* l : left
* c : columns
* r : right
* p : possible
* b : bit
* i : innerRecursiveFunction

```javascript
function queenSolutions(n){
  var numSolutions = 0,
      all = ( 1 << n ) - 1;
  function innerRecursiveFunction( left, columns, right ){
    if( columns == all ){
      numSolutions++;
    }
    var possible = ~( left | columns | right ) & all,
        bit;
    for( ; possible ; possible -= bit ){
      bits = possible & -possible;
      innerRecursiveFunction( ( left | bits ) << 1, columns | bit, ( right | bit ) >> 1 )
    }
  }
  innerRecursiveFunction();
  return numSolutions;
}
```

Cool.  Let's now add some line by line comments, so you can follow what's happening.

Note:  all, columns, left, right, possible, and bit are all binary representations of number, each with a lenght of "n".  So as an example if we are seeking the solutions for n = 8, then all = 1111 1111 (space added for clarity).

```javascript
function queenSolutions(n){
  var numSolutions = 0, //this variable will be used to track the total solutions found
      all = ( 1 << n ) - 1;  //this is a mask for bitwise operations, with value of 1 in each place.  For example with "n" as 4, all is 1111
  function innerRecursiveFunction( left, columns, right ){ //this is our recursive function
    if( columns == all ){ //if columns is equal to all then, this is a valid solution
      numSolutions++;  //increase the count by 1
    }
    var possible = ~( left | columns | right ) & all, //possible tracks the available spots of where a queen can be placed
        bit;  //variable declaration with all 0s in each bit position
    for( ; possible ; possible -= bit ){ //on a successive iteration, possible will equal possible minus bit
      bit = possible & -possible;  //this will be a mask for the next line, setting up the next call
      innerRecursiveFunction( ( left | bits ) << 1, columns | bit, ( right | bit ) >> 1 )  //bit shifts and or combinations to pass in the state of current solution
    }
  }
  innerRecursiveFunction(); //initial call to start the program, sends in 0 for all parameters
  return numSolutions;  //return the number of solutions
}
```

In the next post on this topic, I will cover the main bitwise operations lines.  For those who want to read more, check out this [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.51.7113&rep=rep1&type=pdf).  This academic paper is the basis and proof of this algorithm.





