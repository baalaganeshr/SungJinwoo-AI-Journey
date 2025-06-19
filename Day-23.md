# Day 23: Maximum Depth of Binary Tree (19/6/25)

## Problem Statement
Given a binary tree, find its maximum depth (the number of nodes along the longest path from root to farthest leaf).

**Constraints:**
- 0 ≤ Number of nodes ≤ 10⁴
- -100 ≤ Node.val ≤ 100

## Examples

Input: [3,9,20,null,null,15,7]  → Output: 3
Input: [1,null,2]                → Output: 2

```python


class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
