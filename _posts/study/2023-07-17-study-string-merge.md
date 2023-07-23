---
layout: post
title: LeetCode - Array / String
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Array / String

### Merge Strings Alternately
You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

~~~python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        self.word1 = word1
        self.word2 = word2
        word3 = ""

        length = max(len(word1), len(word2))
        i = 0
        while i < length:
            if i >= len(word1) :
                word3 = word3 + word2[i]
            elif i >= len(word2) :
                word3 = word3 + word1[i]
            else:
                word3 = word3 + word1[i] + word2[i]    
            i+=1
        return word3

s = Solution()
s.mergeAlternately("abc", "pqr") 
~~~

## Two Sum
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

~~~python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        self.nums = nums
        self.target = target

        for i, v in enumerate(nums) :
            for j, r in enumerate(nums) :
                if i != j :
                    if v+r == target :
                        return i, j
                    else:        
                        continue

s = Solution()
nums = [2, 7, 11, 15]
target = 9
s.twoSum(nums, target)        

~~~

## Greatest Common Divisor of Strings

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

~~~python
class Solution:
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        
        if str1 + str2 != str2 + str1:
            return ""

        max_length = gcd(len(str1), len(str2))    
        return str1[:max_length]

s = Solution()
s.gcdOfStrings("TAUXXTAUXXTAUXXTAUXXTAUXX", "TAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXXTAUXX")
        
~~~