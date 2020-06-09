---
layout: post
title: The Commandments Revisited
excerpt: <i>About amending God's words</i>
---

We defined 4 commandments about defining functions in the [first post](https://dtrik.github.io/little-schemer/) about Scheme. As I 
mentioned in the closing statement of the [last post](https://dtrik.github.io/plot-thickens/), we are now going to refine two of 
those and also declare two new commandments.

### First Commandment
#### Initial Version
Always ask *null?* as the first question in expressing any function.

#### Final Version
* When recurring on a list of atoms, *lat*, ask two questions about it: (*null? lat*) and else.
* When recurring on a number, *n*, ask two questions about it: (*zero? n*) and else.
* When recurring on a list of S-expressions, *l*, ask three questions about it: (*null? l*), (*atom? (car l*)), and else.

### Fourth Commandment 
#### Initial Version
Always change at least one argument while recurring. 

It must be changed to be closer to termination. The changing argument must be tested in the terminating condition: 

* when using *cdr*, test termination with *null?*

#### Final Version
Always change at least one argument while recurring. 
* When recurring on a list of atoms, *lat*, use (*cdr lat*).
* When recurring on a number, *n*, use (*sub1 n*).
* When recurring on a list of S-expressions, *l*, use (*car l*) and (*cdr l*) if neither (*null? l*) nor (*atom? (car l)*) are true.

It must be changed to be closer to termination. The changing argument must be tested in the termination condition:

* when using *cdr*, test termination with *null?* and
* when using *sub1*, test termination with *zero?*.

### Fifth Commandment
* When building a value with [o+](https://github.com/dtrik/little-schemer/blob/master/LS_Functions/add.scm), always use 0 for the value
of the terminating line, for adding 0 does not change the value of an addition.
* When building a value with [x](https://github.com/dtrik/little-schemer/blob/master/LS_Functions/multiply.scm), always use 1 for the
value of the terminating line, for multiplying by 1 does not change the value of a multiplication.
* When building a value with *cons*, always consider () for the value of the terminating line.

### Sixth Commandment
Simplify only after the function is correct.

'Til Later
