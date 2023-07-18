---
layout: post
title: LeetCode - Greatest Common Divisor of Strings
categories: example
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Greatest Common Divisor of Strings

Given two strings str1 and str2, return the largest string x such that x divides both str1 and str2.

~~~python
class Solution(object):
    def gcdOfStrings(self, str1, str2):
        """
        :type str1: str
        :type str2: str
        :rtype: str
        """

        self.str1 = str1
        self.str2 = str2
        rtn = ""

        for i in range(len(str1)):
            for j in range(len(str2)):
                if i == j and str1[i] == str2[j]:
                    if str1[i] in rtn :
                        break
                    else :    
                        rtn = rtn + str1[i]        
                    break
        return rtn      
        
s = Solution()
s.gcdOfStrings("ABCABC", "ABC")       

~~~
