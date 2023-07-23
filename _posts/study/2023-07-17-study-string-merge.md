---
layout: post
title: LeetCode - Array / String
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [Python] LeetCode - Array / String

## Merge Strings Alternately
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

## Two Sum
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

## Greatest Common Divisor of Strings
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

## Kids With the Greatest Number of Candies
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

## Can Place Flowers
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

## Reverse Vowels of a String
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

## Reverse Words in a String
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

## Product of Array Except Self
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

~~~python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = [1] * len(nums)
        pre = 1
        post = 1
        for i in range(len(nums)) :
            answer[i] *= pre
            answer[-1-i] *= post
            pre *= nums[i]
            post *= nums[-1-i]
        return answer

s = Solution()
inputList = [1,2,3,4]
s.productExceptSelf(inputList)        
~~~