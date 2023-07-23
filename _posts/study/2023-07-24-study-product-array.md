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
        answer = [1] * len(nums)
        pre = 1
        post = 1
        for i in range(len(nums)) :
            answer[i] *= pre
            answer[-1-i] *= post
            pre *= nums[i]
            post *= nums[-1-i]
        return answer

s = Solution()
inputList = [1,2,3,4]
s.productExceptSelf(inputList)        
~~~