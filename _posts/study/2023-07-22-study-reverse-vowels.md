---
layout: post
title: LeetCode - Reverse Vowels of a String (Array/String)
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Reverse Vowels of a String

Given a string s, reverse only all the vowels in the string and return it.

The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases, more than once.

~~~python
class Solution:
    def reverseVowels(self, s: str) -> str:
        vowels = ['a','e','i','o','u', 'A', 'E', 'I', 'O', 'U']
        countVowels = sum(s.count(x) for x in vowels)
        replaceVowels = []
        rtn = list(s)
        k = 0

        for i in range(len(rtn)) :
            if rtn[i] in vowels:
                replaceVowels.append(rtn[i])

        for j in range(len(rtn)) :
            if rtn[j] in vowels:
                rtn[j] = replaceVowels[countVowels-(k+1)]
                k += 1
                
        return "".join(rtn)

s = Solution()
inputStr = "aA"
s.reverseVowels(inputStr)            
        
~~~