---
layout: post
title: [Python] Merge Strings Alternately
sitemap: false
categories: [study, python]
tags: [study, python]
hide_last_modified: true
---

## Code

You are given two strings word1 and word2. Merge the strings by adding letters in alternating order, starting with word1. If a string is longer than the other, append the additional letters onto the end of the merged string.

~~~python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        self.word1 = word1
        self.word2 = word2
        word3 = ""

        length = max(len(word1), len(word2))
        i = 0
        while i < length:
            if i >= len(word1) :
                word3 = word3 + word2[i]
            elif i >= len(word2) :
                word3 = word3 + word1[i]
            else:
                word3 = word3 + word1[i] + word2[i]    
            i+=1
        return word3

s = Solution()
s.mergeAlternately("abc", "pqr") 
~~~
