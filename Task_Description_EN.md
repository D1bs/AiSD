# Sorting with Constraints

You are given an integer array `nums` and three parameters:
- `maxValue`: the maximum possible value of an element in the array.
- `maxCount`: the maximum number of comparison operations you are allowed to perform.
- `maxMemory`: the maximum amount of additional memory (in cells) you are allowed to use.

Your task is to sort the array in non-decreasing order while adhering to **all** constraints.

**Constraints:**
- Array length: `1 <= nums.length <= 10^5`
- `-10^5 <= nums[i] <= maxValue <= 10^5`
- `1 <= maxCount <= 10^12`
- `1 <= maxMemory <= 10^6`

**Definitions:**
- **Comparison Operation** — any operation where two elements from the array are compared with each other (e.g., `a < b` or `nums[i] > nums[j]`).
- **Additional Memory** — any space used beyond the input array. Counted in "cells" (e.g., a single `int` variable is one cell, creating an auxiliary array of length `k` is `k` cells). Memory for temporary variables in your algorithm must also be accounted for.

You need to implement the function: function sortWithConstraints(nums, maxValue, maxCount, maxMemory)


**Important:** You must choose a sorting algorithm that guarantees completion without exceeding any of the constraints. Using built-in sort functions is forbidden.

---

**Example 1:**

Input: nums = [3, 1, 2], maxValue = 100, maxCount = 1000, maxMemory = 1000
Output: [1, 2, 3]
Explanation: Constraints are very loose, any efficient algorithm (e.g., Quicksort, Merge Sort) will work.

**Example 2:**

Input: nums = [100000, -100000], maxValue = 100000, maxCount = 1, maxMemory = 1000000
Output: [-100000, 100000]
Explanation: The comparison limit is very strict, but the array is small and memory is large. Counting Sort is ideal here, requiring O(n + k) memory and O(n + k) operations but minimal comparisons.

**Example 3:**

Input: nums = [5, 4, 3, 2, 1], maxValue = 5, maxCount = 30, maxMemory = 5
Output: [1, 2, 3, 4, 5]
Explanation: Memory constraint is very strict (cannot create a large auxiliary array). However, the comparison limit is quite loose. Insertion Sort or Selection Sort, which use O(1) extra memory, are suitable here.
