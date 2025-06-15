# Day 19: Merge Sorted Arrays (15/6/25)

## Problem Statement
Merge two sorted arrays `nums1` and `nums2` into `nums1` which has enough space (filled with 0s). 

**Constraints:**
- `nums1.length == m + n`
- `nums2.length == n`
- -10⁹ ≤ nums1[i], nums2[j] ≤ 10⁹

## Examples
```python
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]

Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]

class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        p1, p2, p = m-1, n-1, m+n-1
        
        while p1 >= 0 and p2 >= 0:
            if nums1[p1] > nums2[p2]:
                nums1[p] = nums1[p1]
                p1 -= 1
            else:
                nums1[p] = nums2[p2]
                p2 -= 1
            p -= 1
        
        # Copy remaining elements from nums2
        nums1[:p2+1] = nums2[:p2+1]
`````````


Key Features
✅ In-place Merge: Modifies nums1 without extra space

✅ O(m+n) Time: Single pass through both arrays

✅ Handles Edge Cases: Empty arrays, all elements in one array

✅ Stable Sort: Maintains original order of equal elements

Complexity
Time: O(m + n) - Each element is visited once

Space: O(1) - No additional storage used

Test Cases
python
sol = Solution()

# Case 1
nums1 = [1,2,3,0,0,0]
sol.merge(nums1, 3, [2,5,6], 3)
print(nums1)  # [1,2,2,3,5,6]

# Case 2 (Edge case: empty nums2)
nums1 = [1]
sol.merge(nums1, 1, [], 0)
print(nums1)  # [1]

# Case 3 (Edge case: empty nums1)
nums1 = [0]
sol.merge(nums1, 0, [1], 1)
print(nums1)  # [1]
Visual Explanation
text
Initial:
nums1 = [1, 2, 3, 0, 0, 0] (m=3)
nums2 = [2, 5, 6] (n=3)

Step-by-Step:
1. Compare 3 (nums1) and 6 (nums2) → Place 6
   [1, 2, 3, 0, 0, 6]
2. Compare 3 and 5 → Place 5
   [1, 2, 3, 0, 5, 6]
3. Compare 3 and 2 → Place 3
   [1, 2, 3, 3, 5, 6]
4. Compare 2 and 2 → Place 2
   [1, 2, 2, 3, 5, 6]
Learning Points
Backward merging avoids overwriting

Pointer manipulation in arrays

Efficient space utilization
