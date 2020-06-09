---
layout: post
title: The Plot Thickens
excerpt: <i>About continuing to scheme</i>
---

The Little Schemer continues to be an interesting task. I have now completed 5 chapters, the last section of chapter 5 has been a 
bit of a struggle. The rest was fairly simple. As an interesting sidenote, while looking at a [code example](https://eloquentjavascript.net/00_intro.html#c_5GjN2pXyt/)
in Javascript, I could connect that to the commandments in Scheme which felt very nice. 

Chapter 4 is about numerical operations on atoms as well extending it to S-expressions. We also start refining the commandments.
The simplest example of operations on numbers is incrementing a number by 1:
```scheme
(define add1
  (lambda (n)
    (+ n 1)))
```
We create all mathematical operations using add1 and sub1. 

Chapter 5 is all about *s. We continue refining the original commandments as well as to redefine many of the original functions to 
operate on all instances instead of the first instance. 
For example, rember is a function that removes the first instance of an atom passed as argument from a list:
```scheme
(define rember
  (lambda (a lat)
    (cond
      ((null? lat) '())
      ((eq? (car lat) a) (cdr lat))
      (else (cons (car lat)
                  (rember a (cdr lat)))))))
```

To extend this to rember* for removing all instances of the atom passed as argument from a list:
```scheme
(define atom?
    (lambda (x)
      (and (not (pair? x)) (not (null? x)))))

(define rember*
  (lambda (a l)
    (cond
      ((null? a) '())
      ((atom? (car l))
       (cond
         ((eq? a (car l)) (rember* (cdr l)))
         (else (cons (car l) (rember* (cdr l))))))
      (else (cons (rember* (a (car l))
                  (rember* a (cdr l))))))))
```

I will update the commandments in a new post.

'Til Later
