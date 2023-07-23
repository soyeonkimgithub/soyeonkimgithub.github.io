---
layout: post
title: LeetCode - Product of Array Except Self (Array/String)
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

~~~python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = [0] * len(nums)
        for i in range(len(nums)) :
            prod = 1
            for j in range(len(nums)) :
                if j != i :
                    prod = prod * nums[j]
            answer[i] = prod
        return answer

s = Solution()
inputList = [-1,1,0,-3,3]
s.productExceptSelf(inputList)                 
        
~~~