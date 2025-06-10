# Day 14: Square Root Calculation (10/6/25)

## Problem Statement
Given a non-negative integer `x`, find its integer square root (the largest integer whose square is ≤ `x`).

**Constraints:**
- Must not use built-in exponent functions
- 0 ≤ x ≤ 2³¹ - 1

## Examples
| Input | Output | Explanation |
|-------|--------|-------------|
| 4     | 2      | √4 = 2      |
| 8     | 2      | √8 ≈ 2.828 → floor is 2 |

## Solution Approach
### Binary Search Method
1. **Edge Cases:** 
   - Return 0 or 1 directly for x < 2
2. **Search Range:**
   - Left = 2, Right = x//2 (since √x ≤ x/2 for x ≥ 4)
3. **Binary Search:**
   - Find mid-point
   - Compare mid² with x
   - Adjust search range based on comparison

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x < 2:
            return x
            
        left, right = 2, x // 2
        while left <= right:
            mid = left + (right - left) // 2
            squared = mid * mid
            if squared == x:
                return mid
            elif squared < x:
                left = mid + 1
            else:
                right = mid - 1
        return right
```
Practice Test Cases
python
print(Solution().mySqrt(16))   # Output: 4
print(Solution().mySqrt(99))   # Output: 9
print(Solution().mySqrt(1))    # Output: 1
Learning Progress
Day 14/30 of coding challenges

Date: 10 June 2025

Today's Focus: Binary search applications

Need More Explanation?
Why x//2 as upper bound?

For x ≥ 4, √x is always ≤ x/2

Why return right?

When loop ends, right points to the floor value

Try solving these variations:

Find cube root

Implement with Newton's method
