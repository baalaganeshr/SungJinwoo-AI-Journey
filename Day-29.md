## Day 29: Path Sum (25/6/25)

## Problem Statement
Given a binary tree and a target sum, determine if there exists a root-to-leaf path where the sum of node values equals the target.

**Constraints:**
- 0 ≤ Number of nodes ≤ 5000
- -1000 ≤ Node.val ≤ 1000
- -1000 ≤ targetSum ≤ 1000

## Examples

Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22 → True
Explanation: Path 5→4→11→2 sums to 22

Input: root = [1,2,3], targetSum = 5 → False
Input: root = [], targetSum = 0 → False

```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        
        # Check if current node is leaf and matches remaining sum
        if not root.left and not root.right:
            return targetSum == root.val
        
        # Recursively check left and right subtrees
        remaining = targetSum - root.val
        return self.hasPathSum(root.left, remaining) or self.hasPathSum(root.right, remaining)
