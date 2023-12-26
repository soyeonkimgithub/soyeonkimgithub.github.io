---
layout: post
title: LeetCode - Algorithm
categories: python
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Algorithm

## Fizz Buzz
Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.

~~~python
# better run time
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        arr = []
        for i in range(1, n+1, 1):
            if (i%3==0) & (i%5==0):
                arr.append("FizzBuzz")
            elif i%3==0:
                arr.append("Fizz")
            elif i%5==0:
                arr.append("Buzz")
            else:
                arr.append(str(i))    
   
        return arr

# better memory use
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        f, b, fb = "Fizz", "Buzz", "FizzBuzz"
        arr = [str(x) for x in range(1, n+1)]
        
        for i in range(4, n, 5):
            arr[i] = b

        for i in range(2, n, 3):
            arr[i] = f

        for i in range(14, n+1, 15):
            arr[i] = fb
            
        return arr  
~~~

## Lexicographical Numbers

Given an integer n, return all the numbers in the range [1, n] sorted in lexicographical order.

You must write an algorithm that runs in O(n) time and uses O(1) extra space. 

~~~python
class Solution:
    def lexicalOrder(self, n: int) -> List[int]:        
        return sorted(list(range(1, n+1)), key=str)     
~~~

## Two sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

~~~python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = {}

        for i, v in enumerate(nums) :
            c = target - v

            if c in dic:
                return [dic[c], i]
            
            dic[v] = i

        return [-1, -1]    
~~~

~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       
       // are there multiple solutions?
       // can I use same element twice?
       // what should I return when there is no right two numbers?
       Map<Integer, Integer> map = new HashMap<>();
       for (int i=0; i<nums.length; i++) {
           int diff = target - nums[i];
           if(map.containsKey(diff)) {
               return new int[]{i, map.get(diff)};
           }
           map.put(nums[i], i);
       }
        return new int[]{-1, -1};
    }
}
~~~

## Reverse Integer

Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

~~~python
class Solution:
    def reverse(self, x: int) -> int:
        rev = 0

        sign = 1 if x >= 0 else -1
        x = abs(x)

        while x > 0:
            rev = rev*10 + x%10

            if rev > 2**31 - 1:
                return 0
            x //= 10
            
        return rev * sign    
~~~

~~~java
public int reverse() {
    // signed or unsigned integer?
    // 
}

~~~

## Reverse bit

Reverse bits of a given 32 bits unsigned integer.

~~~python
class Solution:
    def reverseBits(self, n: int) -> int:
        num = bin(n)[2:].zfill(32)  
        return int(num[::-1], 2)
~~~

## Reverse String

Write a function that reverses a string. The input string is given as an array of characters s.

~~~python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        s.reverse()
~~~

* String - immutable, operation leads to waste of space and decrease of performance, reason: String can be reused frequently, JVM creates 'string constant pool' and shares this with other objects, performance getting better, but it cannot be changed
* StringBuffer - mutable, having inner space 'buffer', thread-safe -> for single thread, can have performance issue, then use StringBuilder
* StringBuilder - mutable, not thread-safe, lighter than StringBuffer, commonly used

~~~java
public String reverse() {
    String str = "Hello";
    StringBuilder sb = new StringBuilder();
    return sb.append(str).reverse().toString();
}

public String reverse() {
    String str = "Hello";
    StringBuilder sb = new StringBuilder();
    for(int i=str.length()-1; i>=0 ;i--) {
        sb.append(str.charAt(i));
    }
    return sb.toString();
}
~~~

