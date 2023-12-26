---
layout: post
title: Java DSA
categories: algorithm
sitemap: false
hide_last_modified: true
published: true

---
## [Algorithm] Java DSA - Stack and Queue

### Stack
* LIFO
* i.e. ArrayList - adding, removing at the end is O(1), in front both are O(n)
* i.e. LinkedList - adding at the end is O(1), removing at the end is O(n), in front both are O(1)

### Queue
* FIFO
* i.e. ArrayList - enqueue, dequeue at the end is O(1), in front both are O(n)
* i.e. LinkedList - enqueue at the end is O(1), dequeue at the end is O(n), in front both are O(1)

###  Stack implementation using array

~~~java
public class ArrayStack {
    // what data structure shall I implement?
    // capacity of stack --> constant arg
    // data type inside the stack --> generic? integer?
    // when it's full or empty, throw an exception?

    private int array[];
    private int top;
    private int capacity;

    ArrayStack(int capacity) {
        this.array = new int[capacity];
        this.capacity = capacity;
        this.top = -1;
    }

    public void push(int item) {
        if(isFull()) {
            throw new RuntimeException("Stack is full");
        }
        array[++top] = item;
    }

    public int pop() {
        if(isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        return array[top--];
    }

    public int peek() {
        if(isEmpty()) {
            throw new RuntimeException("Stack is empty");
        }
        return array[top];
    }

    public boolean isFull() {
        return top==capacity-1;
    }

    public boolean isEmpty() {
        return top==-1;
    }
}

~~~
