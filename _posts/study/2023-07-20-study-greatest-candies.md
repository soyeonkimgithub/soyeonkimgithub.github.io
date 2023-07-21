---
layout: post
title: LeetCode - Kids With the Greatest Number of Candies (Array/String)
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Kids With the Greatest Number of Candies

There are n kids with candies. You are given an integer array candies, where each candies[i] represents the number of candies the ith kid has, and an integer extraCandies, denoting the number of extra candies that you have.

Return a boolean array result of length n, where result[i] is true if, after giving the ith kid all the extraCandies, they will have the greatest number of candies among all the kids, or false otherwise.

~~~python
class Solution:
    def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
        
        result = []
        maxCandy = max(candies)
        for i in range(len(candies)) :
            if candies[i] + extraCandies >= maxCandy :
                result.append(True)
            else:
                result.append(False)    

        return result            

s = Solution()

candies = [2,3,5,1,3]
extraCandies = 3

s.kidsWithCandies(candies, extraCandies)            
        
~~~