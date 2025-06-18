# Day 22: Symmetric Tree (18/6/25)

## Problem Statement
Given a binary tree, determine if it  is a mirror of itself (symmetric around its center).

**Constraints:**
- 1 ≤ Number of nodes ≤ 1000
- -100 ≤ Node.val ≤ 100

## Examples

Input: [1,2,2,3,4,4,3]   → Output: True
Input: [1,2,2,null,3,null,3] → Output: False

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        return self.isMirror(root.left, root.right)
    
    def isMirror(self, left: TreeNode, right: TreeNode) -> bool:
        if not left and not right:
            return True
        if not left or not right or left.val != right.val:
            return False
        return self.isMirror(left.left, right.right) and self.isMirror(left.right, right.left)

