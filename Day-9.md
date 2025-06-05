# Search Insert Position

## Problem Description
Given a sorted array of distinct integers and a target value, return the index where the target is found. If not found, return the insertion index to maintain order.

## Solution
### Binary Search Approach
- **Time Complexity:** O(log n)
- **Space Complexity:** O(1)

- Example Usage

python

print(Solution().searchInsert([1,3,5,6], 5))  # Output: 2

print(Solution().searchInsert([1,3,5,6], 2))  # Output: 1

print(Solution().searchInsert([1,3,5,6], 7))  # Output: 4

How to Use

Copy the code into a file named search_insert_position.py

Import the Solution class where needed

Call the searchInsert method with your sorted array and target value

Note: Don't forget to import List from typing if needed:

python
from typing import List
This version has:

Clear section headers

Proper code formatting

Complete import statement

Better readability

All necessary information in a structured format

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                return mid
            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left

