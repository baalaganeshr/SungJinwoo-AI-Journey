# Day 24: Convert Sorted Array to BST (20/6/25)

## Problem Statement
Given a sorted array in ascending order, convert it to a height-balanced binary search tree.

**Constraints:**
- 1 ≤ nums.length ≤ 10⁴
- -10⁴ ≤ nums[i] ≤ 10⁴
- Input array is strictly increasing

## Examples

Input: [-10,-3,0,5,9] → Output: [0,-3,9,-10,null,5]
Input: [1,3] → Output: [3,1] or [1,null,3]


Input: [-10, -3, 0, 5, 9]

Construction:
1. Root: 0 (middle element)
2. Left subtree: [-10, -3]
   - Root: -3
   - Left: -10
3. Right subtree: [5, 9]
   - Root: 9
   - Left: 5

Resulting Tree:
        0
       / \
     -3   9
     /   /
  -10   5

```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        def build(l, r):
            if l > r:
                return None
            mid = (l + r) // 2
            node = TreeNode(nums[mid])
            node.left = build(l, mid - 1)
            node.right = build(mid + 1, r)
            return node
        
        return build(0, len(nums) - 1)
