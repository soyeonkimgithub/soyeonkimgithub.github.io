---
layout: post
title: Java DSA
categories: languages
sitemap: false
hide_last_modified: true
published: true

---
## [Java] Linked List

### Big O
* is a way to comparing codes mathmatically about how efficient they run.
* time complexity -> measures in the number of operations that it takes to complete something
* space complexity -> measures memory space used
* Omega(best case), Theta(average case), Al Macron(worst case)
* O(n) -> O of n, i.e. for loop from 0 to n, proportional
* O(n^2) -> O of n squared, i.e. loop within a loop
* O(1) -> O of one, i.e. a simple one operation like '+', constant time, most efficient!
* O(log n) -> O of log n, i.e. out of 8 items in array, find one item using divide and conquer, 3 steps, log8 = 3 (log sub two of eight equals three)
* Big O of Array Lists -> i.e. add or remove something at the end, list.add(100) or list.remove(4) it will be O(1), but when we need to re index, list.add(0,100) or list.remove(0) it will be O(n)
* ref. https://www.bigocheatsheet.com/

### Linked List vs Array List
* linked list is dynamic in length, while array is fixed in length
* linked list, instead of all of items being in a contiguous place in memory(that's why we have index), items are going to be spread out
* linked list has head for first node, tail for last node and others point next node
* Big O 

| Action       | Linked List | Array List  |
| -----------  | ----------- | ----------- |
| Append       | O(1)        | O(1)        |
| Remove Last  | O(n)*       | O(1)*       |
| Prepend      | O(1)        | O(n)        |
| Remove First | O(1)*       | O(n)*       |
| Insert       | O(n)        | O(n)        |
| Remove       | O(n)        | O(n)        |
| Lookup by Index | O(n)        | O(1)        |
| Lookup by Value | O(n)        | O(n)        |

###  Floyd's Tortoise and Hare algorithm
Write a method called hasLoop that is part of the linked list class.

The method should be able to detect if there is a cycle or loop present in the linked list.

The method should utilize Floyd's cycle-finding algorithm, also known as the "tortoise and hare" algorithm, to determine the presence of a loop efficiently.

~~~java
    public boolean hasLoop() {

        Node slow = head;
        Node fast = head;
        while(fast!=null && fast.next!=null) {

            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                return true;
            }
        }
        return false;
    }
~~~

### Find middle node
Implement a method called findMiddleNode that returns the middle node of the linked list.

If the list has an even number of nodes, the method should return the second middle node.

~~~java
    public Node findMiddleNode() {
        Node slow = head;
        Node fast = head;

        while(fast!=null && fast.next!=null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
~~~
