---
layout: post
title: Algorithm 
categories: algorithm
sitemap: false
hide_last_modified: true
published: true
---

## [Algorithm] Selection
find the k-th smallest (or largest) item in a data structure. first we have to sort the data.

#### Quick select algorithm
- it is able to find the k-th smallest (largest) item in an unordered array
- it has O(N) linear running time in best-case
- in worst-cast it has in O(N^2) quadratic running time
- in-place approach - does not need additional memory
- step
  1. choose a so-called pivot item at random
  2. partition the array (based on the value of the pivot)
  3. instead of recursion into both sides, we take just one side (by comparing k and pivot)
     
~~~python
import random

class QuickSelect:

    def __init__(self, nums):
        self.nums = nums
        self.first_index = 0
        self.last_index = len(nums) - 1

    def run(self, k):
        return self.select(self.first_index, self.last_index, k - 1)

    # PARTITION PHASE
    def partition(self, first_index, last_index):
        pivot_index = random.randint(first_index, last_index)
        self.swap(pivot_index, last_index)

        for i in range(first_index, last_index):
            if self.nums[i] < self.nums[last_index]:
                self.swap(i, first_index)
                first_index += 1

        self.swap(first_index, last_index)

        # index of the pivot
        return first_index

    def swap(self, i, j):
        self.nums[i], self.nums[j] = self.nums[j], self.nums[i]

    # SELECTION PHASE
    def select(self, first_index, last_index, k):

        pivot_index = self.partition(first_index, last_index)

        # selection phase when we compare the pivot_index with k
        if pivot_index < k:
            # have to discard the left sub-array and keep considering the items on the right
            return self.select(pivot_index + 1, last_index, k)

        elif pivot_index > k:
            return self.select(first_index, pivot_index - 1, k)

        return self.nums[pivot_index]


x = [1, 2, -5, 10, 100, -7, 3, 4]
select = QuickSelect(x)
print(select.run(1))

~~~

#### Advanced selection - median of medians, introselect
- Median : Middle item in sorted order
- There will be approximately the same amount of items in the left and right subarrays
- median of medians algorithm uses quickselect algorithm but it select the median as the pivot
- O(N) linear running time complexity, O(logN) memory complexity

~~~ python

def median_algorithm(nums, k):

    # split the list into chunks of 5 items
    chunks = [nums[i:i+5] for i in range(0, len(nums), 5)]

    # the median is the middle item in the sorted order
    # NOTE: median of the medians is just approximately the median of the original data scturcure
    medians = [sorted(chunk)[len(chunk)//2] for chunk in chunks]
    pivot_value = sorted(medians)[len(medians)//2]

    # partition phase
    left_array = [n for n in nums if n < pivot_value]
    right_array = [m for m in nums if m > pivot_value]

    # selection phase
    pivot_index = len(left_array)

    if k < pivot_index:
        return median_algorithm(left_array, k)
    elif k > pivot_index:
        return median_algorithm(right_array, k-len(left_array)-1)
    else:
        return pivot_value

def select(nums, k):
    return median_algorithm(nums, k-1)

x = [1, -5, 0, 10, 15, 20, 3, -1, 21, 22, 23, 24, 25, 26, 27, 28, 29]
print(select(x, 1))
print(select(x, 2))
print(select(x, 3))
print(select(x, 4))
~~~

#### Online selection