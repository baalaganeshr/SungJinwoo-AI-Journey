# Merge Two Sorted Lists

**Problem:** Combine two sorted linked lists into one sorted list.

**Date:** June 2, 2025

## The Problem

You have two sorted linked lists. Merge them into one sorted list.

**Example:**
```
List 1: 1 → 2 → 4
List 2: 1 → 3 → 4
Result: 1 → 1 → 2 → 3 → 4 → 4
```

## Simple Solution

**Idea:** Compare the first nodes of both lists, pick the smaller one, repeat.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def mergeTwoLists(self, list1, list2):
        # Create a dummy starting point
        dummy = ListNode()
        current = dummy
        
        # Compare and connect nodes
        while list1 and list2:
            if list1.val <= list2.val:
                current.next = list1
                list1 = list1.next
            else:
                current.next = list2
                list2 = list2.next
            current = current.next
        
        # Add remaining nodes
        current.next = list1 or list2
        
        return dummy.next
```

## How It Works

1. **Start with dummy node** - Makes building easier
2. **Compare values** - Pick smaller number
3. **Move forward** - Go to next node in chosen list
4. **Repeat** - Until one list is empty
5. **Add leftovers** - Attach remaining nodes

## Step by Step Example

```
list1: [1,2,4]  list2: [1,3,4]

Step 1: Compare 1 vs 1 → Pick first 1
Result: 1

Step 2: Compare 2 vs 1 → Pick 1  
Result: 1 → 1

Step 3: Compare 2 vs 3 → Pick 2
Result: 1 → 1 → 2

Step 4: Compare 4 vs 3 → Pick 3
Result: 1 → 1 → 2 → 3

Step 5: Compare 4 vs 4 → Pick first 4
Result: 1 → 1 → 2 → 3 → 4

Step 6: Add remaining [4]
Final: 1 → 1 → 2 → 3 → 4 → 4
```

## Test It

```python
def test():
    solution = Solution()
    
    # Create test lists
    # [1,2,4]
    list1 = ListNode(1)
    list1.next = ListNode(2)
    list1.next.next = ListNode(4)
    
    # [1,3,4]
    list2 = ListNode(1)
    list2.next = ListNode(3)
    list2.next.next = ListNode(4)
    
    # Merge and print
    result = solution.mergeTwoLists(list1, list2)
    
    # Should print: 1 1 2 3 4 4
    while result:
        print(result.val, end=" ")
        result = result.next

test()
```

## Why This Works

- **Both lists are sorted** - We only need to compare front elements
- **Dummy node trick** - Avoids special cases for empty results
- **Linear time** - Visit each node once
- **No extra space** - Just rearrange existing nodes

## Time & Space

- **Time:** O(n + m) - Look at each node once
- **Space:** O(1) - Only use a few pointers

**That's it!** Simple and efficient. 🎯
