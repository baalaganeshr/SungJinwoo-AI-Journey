# Day 28: Find All K-Distant Indices (24/6/25)

## Problem Statement
Given an array `nums`, find all indices `i` where there exists at least one index `j` such that:
1. `nums[j] == key`
2. `|i - j| <= k`

Return the indices in increasing order.

**Constraints:**
- 1 ≤ nums.length ≤ 1000
- 1 ≤ nums[i] ≤ 1000
- 1 ≤ k ≤ nums.length

## Examples

Input: nums = [3,4,9,1,3,9,5], key = 9, k = 1 → Output: [1,2,3,4,5,6]

Input: nums = [2,2,2,2,2], key = 2, k = 2 → Output: [0,1,2,3,4]

```python
class Solution:
    def findKDistantIndices(self, nums: List[int], key: int, k: int) -> List[int]:
        key_indices = [i for i, num in enumerate(nums) if num == key]
        result = []
        
        for i in range(len(nums)):
            for j in key_indices:
                if abs(i - j) <= k:
                    result.append(i)
                    break
        
        return result
