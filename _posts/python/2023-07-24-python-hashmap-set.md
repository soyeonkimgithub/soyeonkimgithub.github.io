---
layout: post
title: LeetCode - Hash Map / Set
categories: python
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Hash Map / Set

## Find the Difference of Two Arrays
Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:

answer[0] is a list of all distinct integers in nums1 which are not present in nums2.
answer[1] is a list of all distinct integers in nums2 which are not present in nums1.

~~~python
class Solution:
    def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
        answer = []
        answer_num1 = []
        answer_num2 = []

        # get the unique value
        nums1_unique = list(set(nums1))
        nums2_unique = list(set(nums2))
        for i in range(len(nums1_unique)) :
            if nums1_unique[i] in nums2_unique:
                continue
            else:   
                answer_num1.append(nums1_unique[i])

        for i in range(len(nums2_unique)) :
            if nums2_unique[i] in nums1_unique:
                continue
            else:   
                answer_num2.append(nums2_unique[i])

        answer.append(answer_num1)
        answer.append(answer_num2)
        return answer

s = Solution()
num1 = [1,2,3]
num2 = [2,4,6]
s.findDifference(num1, num2)            
~~~

## Unique Number of Occurrences
Given an array of integers arr, return true if the number of occurrences of each value in the array is unique or false otherwise.

~~~python
class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:
        d = {}
        v = set()
        for i in range(len(arr)) :
            d[arr[i]] = arr.count(arr[i])

        for x in d.values() :
            v.add(x)

        return len(d) == len(v)

s = Solution()
a = [-3,0,1,-3,1,1,1,-3,10,0]
s.uniqueOccurrences(a)               
~~~