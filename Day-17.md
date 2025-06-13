# Day 17: Remove Duplicates from Sorted List (13/6/25)

## Problem Statement
Given the head of a sorted linked list, delete all duplicates such that each element appears only once.

**Examples:**
```python
Input: 1 → 1 → 2
Output: 1 → 2

Input: 1 → 1 → 2 → 3 → 3
Output: 1 → 2 → 3
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
``` Python
class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        current = head
        while current and current.next:
            if current.val == current.next.val:
                current.next = current.next.next
            else:
                current = current.next
        return head
``` Text Cases
def create_list(arr):
    dummy = ListNode()
    current = dummy
    for val in arr:
        current.next = ListNode(val)
        current = current.next
    return dummy.next

def print_list(head):
    result = []
    while head:
        result.append(head.val)
        head = head.next
    return result

# Test execution
sol = Solution()

test1 = create_list([1,1,2])
result1 = sol.deleteDuplicates(test1)
print(print_list(result1))  # Output: [1, 2]

test2 = create_list([1,1,2,3,3])
result2 = sol.deleteDuplicates(test2)
print(print_list(result2))  # Output: [1, 2, 3]

test3 = create_list([])
result3 = sol.deleteDuplicates(test3)
print(print_list(result3))  # Output: []

```
Explanation
Algorithm:

Traverse the linked list while comparing each node with its next node

When duplicates are found (current.val == next.val), skip the next node

Otherwise, move to the next node

Complexity:

Time: O(n) - Single pass through the list

Space: O(1) - No additional data structures used

Edge Cases Handled:

Empty list (returns None)

Single node list (returns the node unchanged)

All duplicates (returns single node)

Visual Example
text
Initial: 1 → 1 → 2 → 3 → 3
Step 1: 1 → 2 → 3 → 3 (skip first duplicate)
Step 2: 1 → 2 → 3 (skip second duplicate)
Final: 1 → 2 → 3
Learning Points
Linked list traversal techniques

In-place modification of linked lists

Handling edge cases in pointer-based structures
