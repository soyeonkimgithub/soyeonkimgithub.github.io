---
layout: post
title: LeetCode - Reverse Words in a String (Array/String)
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Reverse Words in a String

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

~~~python
class Solution:
    def reverseWords(self, s: str) -> str:
        inputStr = " ".join(s.split())
        wordList = []
        word = ""

        for i in range(len(inputStr)) :
            if inputStr[i] == " " :
                wordList.append(word)
                word = ""
            elif i == len(inputStr)-1 :
                word = word + inputStr[i]
                wordList.append(word)
                word = ""
            else :
                word = word + inputStr[i]
        wordList.reverse() 
        return " ".join(wordList)

s = Solution()
inputStr = "the sky is blue"
s.reverseWords(inputStr)        
        
~~~