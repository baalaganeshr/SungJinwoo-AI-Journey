# 28. Find the Index of the First Occurrence in a String

## Problem  Statement

Given two strings `needle` and `haystack`, return the **index of the first occurrence** of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

---

## Examples


## Input: haystack = "sadbutsad", needle = "sad"
Output: 0

## Input: haystack = "leetcode", needle = "leeto"
Output: -1
## Approaches
1. Built-in Method (Recommended)
Uses Python’s optimized string method .find().

python
Copy
Edit
# class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.find(needle)
Complexity:

Time: O(n) average case

Space: O(1)

## 2. Sliding Window Approach
Checks every substring of the same length as needle in haystack.

python
Copy
Edit
# class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        n_len = len(needle)
        for i in range(len(haystack) - n_len + 1):
            if haystack[i:i+n_len] == needle:
                return i
        return -1
# Complexity:

Time: O(m * n) (where m = len(haystack), n = len(needle))

Space: O(1)

Key Points
If needle is an empty string, return 0

If needle is longer than haystack, return -1

Use str.find() for best performance

Sliding window is easier to understand, but less efficient

Example Walkthrough
Input: haystack = "sadbutsad", needle = "sad"

Check substring at index 0: "sad" == "sad" → Return 0

(If continued, would find again at index 6, but return the first match)

Summary
Use .find() for the fastest solution.

Sliding window method is useful for interviews and learning.

Always handle edge cases (empty strings, needle longer than haystack).
```python
