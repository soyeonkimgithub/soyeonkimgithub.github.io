---
layout: post
title: LeetCode - Two Sum
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Two Sum

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
