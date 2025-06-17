# Day 21: Same Tree (17/6/25)

## Problem Statement
Given two binary trees `p` and `q`, check if they are structurally identical with the same node values.

**Constraints:**
- 0 ≤ Number of nodes ≤ 100
- -10⁴ ≤ Node.val ≤ 10⁴

## Examples

Input: p = [1,2,3], q = [1,2,3]   → Output: True
Input: p = [1,2], q = [1,null,2]   → Output: False
Input: p = [1,2,1], q = [1,1,2]    → Output: False

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def isSameTree(self, p: TreeNode, q: TreeNode) -> bool:
        if not p and not q:
            return True
        if not p or not q or p.val != q.val:
            return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)


```
Recursive:
1. Check current node values
2. Recursively check left subtrees
3. Recursively check right subtrees

Iterative:
1. Use queue to track node pairs
2. Compare nodes level by level
3. Enqueue child pairs for comparison
