---
layout: post
title: Algorithm 
categories: study
sitemap: false
hide_last_modified: true
published: true
---

## [Algorithm] Recursion

#### Iteration and Recursion
An iterative function is one that loops to repeat some part of the code, and a recursive function is one that calls itself again to repeat the code.
Using a simple for loop to display the numbers from one to ten is an iterative process. Sudoku game or factorial function is an example of recursive process.
Recursion is at least twice as slow as iteration - first we unfold recursive calls (push them on the stack) and after the base case we retrieve these stack frames one by one
~~~python
def tail(n):
    # related function calls do not depend on each other
    # there is no downward dependence
    print("calling tail() with n='"+str(n)+"'")

    # base case
    if n == 0:
        return
    print(n)
    tail(n-1)

def head(n):
    # function calls must be tracked
    # related function calls depend on each other
    # problem: stack overflow
    # solve : head recursion -> tail recursion -> iteration
    print("calling head() with n='"+str(n)+"'")
    if n == 0:
        return

    head(n-1)
    print(n)

tail(5)
~~~

#### Factorial
~~~python
def factorial_head(n):
    # base case
    if n == 0:
        return 1
    return n * factorial_head(n-1)

def factorial_tail(n, accumulator=1):
    # base case
    if n == 1:
        return accumulator
    return factorial_tail(n-1, n*accumulator) # there is no backtracking

print(factorial_tail(5))
~~~

#### Fibonacci number
~~~python

~~~