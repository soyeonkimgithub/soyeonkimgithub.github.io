---
layout: post
title: LeetCode - Two Pointers
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Two Pointers

## Move Zeroes
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

~~~python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """ 
        nums2 = [0] * len(nums)
        j = len(nums)
        k = 0
        for i in range(len(nums)) :
            if nums[i] == 0:
                j -= 1
                nums2[j] = 0  
            else :
                nums2[k] = nums[i]
                k += 1   
                
        for i in range(len(nums2)) :
            nums[i] = nums2[i]

s = Solution()
nums = [0,1,0,3,12]
s.moveZeroes(nums)        
~~~

## Is Subsequence
Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).
~~~python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        r = t
        for i in range(len(t)) :
            if t[i] in s:
                continue
            else :
                r = r.replace(t[i],"")
        print(r)
        print(s in r)
        print(s==r)
        return s in r or s == r
        

s = Solution()
input1 = "leeeeetcode"
input2 = "ylyyyeyyyeeeeyyyyetcode"
rtn = s.isSubsequence(input1, input2)           
~~~