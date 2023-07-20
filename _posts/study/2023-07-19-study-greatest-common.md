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
class Solution(object):
    def gcdOfStrings(self, str1, str2):
        """
        :type str1: str
        :type str2: str
        :rtype: str
        """
        self.str1 = str1
        self.str2 = str2
        divisor = ""
        str1Div = ""
        str2Div = ""

        for i in range(len(str1)):
            print(str1Div, str1[i], divisor)
            if str1Div != "" and str1[i] != divisor and str1[i] in divisor:
                break
            str1Div = str1Div + str1[i]
            str2Div = ""
            for j in range(len(str2)):
                str2Div = str2Div + str2[j]
                if str1Div == str2Div:
                    divisor = str1Div
                elif len(str1Div) < len(str2Div) or j == (len(str2)-1):
                    break
                else:
                    continue
        return divisor 

s = Solution()
s.gcdOfStrings("ABCDEF", "ABC")     

~~~
