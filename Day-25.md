# Day 25: Balanced Binary Tree (21/6/25)

## Problem Statement
Given a binary tree, determine if it is height-balanced (the left and right subtrees of every node differ in height by no more than 1).

**Constraints:**
- 0 ≤ Number of nodes ≤ 5000
- -10⁴ ≤ Node.val ≤ 10⁴

## Examples

Input: [3,9,20,null,null,15,7] → True
Input: [1,2,2,3,3,null,null,4,4] → False
Input: [] → True


Balanced Tree (Example 1):
        3
       / \
      9  20
        /  \
       15   7

Unbalanced Tree (Example 2):
        1
       / \
      2   2
     / \
    3   3
   / \
  4   4

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        def check(node):
            if not node:
                return 0, True
            
            left_height, left_balanced = check(node.left)
            right_height, right_balanced = check(node.right)
            
            current_height = 1 + max(left_height, right_height)
            is_balanced = left_balanced and right_balanced and abs(left_height - right_height) <= 1
            
            return current_height, is_balanced
        
        _, balanced = check(root)
        return balanced
