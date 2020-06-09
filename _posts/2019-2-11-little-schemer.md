---
layout: post
title: The Little Schemer
excerpt: <i>About learning to scheme</i>
---

Before you wonder, no, I have not suddenly starting plotting and weaving webs. 

[The Little Schemer](https://mitpress.mit.edu/books/little-schemer-fourth-edition) is one of the classics of the genre for 
learning Lisp. The book attempts to teach Scheme/Lisp using the [Socratic Method](https://en.wikipedia.org/wiki/Socratic_method).
Concepts are introduced in a question and answer format.

## Socratic Method Example

 <table style="width:100%">
  <tr>
    <th>Question</th>
    <th>Answer</th>
  </tr>
  <tr>
    <td>Is it true that this is an atom? '1492</td>
    <td>Yes, because 1492 is a string of digits</td>
  </tr>
  <tr>
    <td>What is the car of l where l is '(a b c)</td>
    <td>a, because a is the first atom of this list</td>
  </tr>
  <tr>
    <td>What is the cdr of l where l is '(a b c)</td>
    <td>'(b c), because '(b c) is the list without (car l)</td>
  </tr>
</table> 

... and so on.

Based on the 3 chapters I have completed so far, it is really engaging.

## Primitives

It starts with the concepts of atoms and lists of atoms and then gradually introduces functional programming, and 
specifically recursive functions. They are built on a platform of primitives that are present in Scheme/Lisp.
The primitives I have used so far for creating my own functions are:
1. *car* - returns the first element from a non-empty list
> Law of Car states that the primitive *car* is defined only for non-empty lists

2. *cdr* - returns the list l without (car l)
> Law of Cdr states that the primitive  *cdr* is defined only for non-empty lists. Cdr of any non-empty list is always another 
list.

3. *cons* - returns a list formed by adding an atom to the front of the list
> Law of Cons states that the primitive *cons* takes two arguments. The second argument to cons must be a list. The result is a 
list.

4. *null?* - checks if a list is composed of zero S-expressions
> Law of Null? states that *null?* is defined only for lists. 

5. *atom?* - checks if S-expression is an atom

6. *eq?* - compares two non-numeric atoms
> Law of Eq? states that the primitive *eq?* takes two arguments. Each must be a non-numeric atom. 

## Functions

A function in Scheme has the following template:
```scheme
(define funcname
  (lambda (arguments)
    (function_definition)))
```
For example, a function that checks if an argument passed to it is a list of atoms or not is defined as follows:
```scheme
(define lat?
  (lambda (l)
    (cond
      ((null? l) #t)
      ((atom? (car l)) (lat? (cdr l)))
      (else #f))))
 ```
 All the functions I have written so far can be found at: [Little Schemer Functions Repo](https://github.com/dtrik/little-schemer)
 
<h2>The Commandments</h2>
 
 The methodology to compose functions correctly can be expressed as commandments. The ones I have studied so far are:
 
 1. Always ask *null?* as the first question in expressing any function
 2. Use *cons* to build lists
 3. When building a list, describe the first typical element, and then *cons* it onto the natural recursion
 4. Always change at least one argument while recurring. It must be changed to be closer to termination. The changing argument must
 be tested in the terminating condition: when using *cdr*, test termination with *null?*
 
 The above is a summary of the contents I have studied till now. I hope to add more posts as I learn more. I will be updating the
 functions I create in the same GitHub repo.
 
'Til Later
