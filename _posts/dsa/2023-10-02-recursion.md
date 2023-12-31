---
layout: post
title: DSA 
categories: dsa
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
the product of all positive integers less than or equal to n.
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

#### Fibonacci sequence
is a sequence in which each number is the sum of the two preceding ones.
~~~python
def fibonacci_head(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fibonacci_head(n-1) + fibonacci_head(n-2)

def fibonacci_tail(n, a=0, b=1):
    if n == 0:
        return a
    if n == 1:
        return b
    return fibonacci_tail(n-1, b, a+b)

def fibonacci_iteration(n):
    a, b = 0, 1

    while n > 0:
        n = n - 1
        a, b = b, a + b

    return a

    # if n == 0:
    #     return a
    # elif n == 1:
    #     return b
    # else:
    #     for i in range(2, n+1) :
    #         a, b = b, a + b
    #     return b

print(fibonacci_iteration(6))

~~~

#### Towers of Hanoi
a puzzle consisting of three rods and a number of disks of various diameters, which can slide onto any rod. The puzzle begins with the disks stacked on one rod in order of decreasing size, the smallest at the top. The objective of the puzzle is to move the entire stack to the last rod.
~~~python
def hanoi(disk, source, middle, dest ):

    if disk == 0:
        print('1.disk %s from %s to %s' % (disk, source, dest))
        return

    hanoi(disk-1, source, dest, middle)
    print('2.disk %s from %s to %s' % (disk, source, dest))
    hanoi(disk-1, middle, source, dest)

hanoi(2, 'A', 'B', 'C')
~~~

#### Euclidean Algorithm
is an efficient method for computing the greatest common divisor of two integers, the largest number that divides them both without a remainder.
-> based on the principle that the greatest common divisor of two numbers does not change if the larger number is replaced by its difference with the smaller number. -> GCD(a, b) == GCD(b, a%b)
~~~python
def gcd(a, b):
    # base case
    if a % b == 0:
        return b
    return gcd(b, a % b)

def gcd_iter(a, b) :
    while a % b != 0:
        a, b = b, a % b
    return b

if __name__ == '__main__':
    print(gcd_iter(24, 9))
~~~