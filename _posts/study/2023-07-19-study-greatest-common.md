---
layout: post
title: LeetCode - Greatest Common Divisor of Strings
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Greatest Common Divisor of Strings

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
