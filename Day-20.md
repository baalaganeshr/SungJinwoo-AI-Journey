# Day 20: Binary Tree Inorder Traversal (16/6/25)

## Problem Statement
Given a binary tree, return the inorder traversal of its nodes' values.

**Inorder Traversal Order:**
1. Left subtree
2. Root node
3. Right subtree

**Constraints:**
- 0 ≤ Number of nodes ≤ 100
- -100 ≤ Node.val ≤ 100

## Examples

Input: [1,null,2,3]    Input: [1,2,3,4,5,null,8,null,null,6,7,9]
Output: [1,3,2]         Output: [4,2,6,5,7,1,3,9,8]


class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        result = []
        self.helper(root, result)
        return result
    
    def helper(self, node, result):
        if not node:
            return
        self.helper(node.left, result)
        result.append(node.val)
        self.helper(node.right, result)

```
Key Features
✅ Two Implementations: Both recursive and iterative solutions

✅ Space Efficiency: Iterative uses O(h) space (h = tree height)

✅ Time Complexity: O(n) for both approaches

✅ Handles Edge Cases: Empty tree, single node

Complexity Analysis
Approach	Time	Space
Recursive	O(n)	O(h)*
Iterative	O(n)	O(h)
*Recursive space complexity includes call stack
