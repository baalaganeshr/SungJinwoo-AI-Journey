#Day-7--3/6/25--Leetcode
Remove Duplicates from Sorted Array

**Problem:** Remove duplicates from a sorted array in-place. Keep only one copy of each number.

**Date:** June 2, 2025

## The Problem

Given a sorted array, remove duplicates so each number appears only once. Do this without using extra space.

**Example:**
```
Input:  [1, 1, 2, 2, 3]
Output: [1, 2, 3, _, _]  (return 3)
        ↑  ↑  ↑
     first 3 are unique
```

## Simple Solution

**Idea:** Use two pointers - one slow, one fast. When fast pointer finds a new number, copy it to slow pointer position.

```python
class Solution:
    def removeDuplicates(self, nums):
        if not nums:
            return 0
        
        # i = slow pointer (where to place next unique number)
        i = 1
        
        # j = fast pointer (checking each number)
        for j in range(1, len(nums)):
            if nums[j] != nums[i - 1]:  # Found new unique number
                nums[i] = nums[j]       # Place it at position i
                i += 1                  # Move to next position
        
        return i  # Number of unique elements
```

## How It Works

1. **First element is always unique** - Start from index 1
2. **Compare current with previous unique** - If different, it's new
3. **Copy new unique number** - Place at next available position
4. **Count unique numbers** - Return how many we found

## Step by Step Example

```
Array: [1, 1, 2, 2, 3]
       i=1, j=1

Step 1: j=1, nums[1]=1, nums[0]=1 → Same, skip
        [1, 1, 2, 2, 3]  i=1

Step 2: j=2, nums[2]=2, nums[0]=1 → Different!
        [1, 2, 2, 2, 3]  i=2 (copied 2 to position 1)
         ↑  ↑

Step 3: j=3, nums[3]=2, nums[1]=2 → Same, skip
        [1, 2, 2, 2, 3]  i=2

Step 4: j=4, nums[4]=3, nums[1]=2 → Different!
        [1, 2, 3, 2, 3]  i=3 (copied 3 to position 2)
         ↑  ↑  ↑

Result: First 3 elements [1, 2, 3] are unique
        Return 3
```

## Visual Explanation

```
Before: [1, 1, 2, 2, 3]
         ↑  ←--- duplicates

After:  [1, 2, 3, _, _]
         ↑  ↑  ↑
      unique numbers
```

## Test It

```python
def test():
    solution = Solution()
    
    # Test case 1
    nums1 = [1, 1, 2]
    k1 = solution.removeDuplicates(nums1)
    print(f"Input: [1,1,2]")
    print(f"Output: {nums1[:k1]} (k={k1})")  # [1, 2]
    
    # Test case 2
    nums2 = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
    k2 = solution.removeDuplicates(nums2)
    print(f"Input: [0,0,1,1,1,2,2,3,3,4]")
    print(f"Output: {nums2[:k2]} (k={k2})")  # [0, 1, 2, 3, 4]
    
    # Test case 3: Empty array
    nums3 = []
    k3 = solution.removeDuplicates(nums3)
    print(f"Input: []")
    print(f"Output: {nums3[:k3]} (k={k3})")  # []

test()
```

## Why This Works

- **Array is sorted** - Duplicates are next to each other
- **Two pointers** - One finds new numbers, one places them
- **In-place** - No extra space needed
- **Maintains order** - Unique numbers stay in same sequence

## Key Points

✅ **Works only on sorted arrays**  
✅ **Modifies array in-place**  
✅ **Returns count of unique numbers**  
✅ **First k elements contain the result**  

## Time & Space

- **Time:** O(n) - Check each element once
- **Space:** O(1) - Only use two pointers

**Simple and efficient!** 🎯
