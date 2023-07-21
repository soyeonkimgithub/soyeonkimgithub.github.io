---
layout: post
title: LeetCode - Can Place Flowers (Array/String)
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Can Place Flowers

You have a long flowerbed in which some of the plots are planted, and some are not. However, flowers cannot be planted in adjacent plots.

Given an integer array flowerbed containing 0's and 1's, where 0 means empty and 1 means not empty, and an integer n, return true if n new flowers can be planted in the flowerbed without violating the no-adjacent-flowers rule and false otherwise.

~~~python
class Solution:
    def canPlaceFlowers(self, flowerbed: List[int], n: int) -> bool:
        nFlower = 0 
        bed = flowerbed
        for i in range(len(bed)) :
            if bed[i] == 0 :
                leftbed = (i == 0) or (bed[i-1] == 0)
                rightbed = (i == len(bed) - 1) or (bed[i+1] == 0)
                if leftbed and rightbed:
                    bed[i] = 1
                    nFlower += 1
                    if nFlower >= n :
                        return True                  
        return nFlower >= n                

s = Solution()
flowerbed = [1,0,0,0,1,0,0]
n = 2        
s.canPlaceFlowers(flowerbed, n)          
        
~~~