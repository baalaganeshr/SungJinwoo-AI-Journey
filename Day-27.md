# Day 27: Minimum Depth of Binary Tree (23/6/25)

## Problem Statement
Given a binary tree, find its minimum depth - the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Key Notes:**
- A leaf node has no children
- Different from maximum depth (which follows the longest path)
- Must reach an actual leaf node (not just any null child)

## Examples

Input: [3,9,20,null,null,15,7]   → Output: 2
Explanation: Shortest path is 3 → 9

Input: [2,null,3,null,4,null,5,null,6] → Output: 5
Explanation: Only path is 2 → 3 → 4 → 5 → 6

Example 1:
        3       ← Depth 1
       / \
      9  20    ← Depth 2 (9 is leaf)
        /  \
       15   7

Example 2:
        2       ← Depth 1
         \
          3     ← Depth 2
           \
            4   ← Depth 3
             \
              5 ← Depth 4
               \
                6 ← Depth 5 (leaf)


```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        
        # Special case for single child
        if not root.left:
            return 1 + self.minDepth(root.right)
        if not root.right:
            return 1 + self.minDepth(root.left)
            
        # Normal case with two children
        return 1 + min(self.minDepth(root.left), self.minDepth(root.right))
