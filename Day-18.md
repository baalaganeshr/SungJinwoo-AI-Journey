# Day 18: Maximum Difference by Remapping a Digit (14/6/25)

## Problem Statement
Given an integer `num`, find the maximum possible difference between:
1. The largest number created by remapping one digit to another
2. The smallest number created by remapping one digit to another

**Key Notes:**
- Remapping replaces ALL occurrences of a digit
- Can remap to same digit (no change)
- Result can have leading zeros
- Use different mappings for min and max

## Examples
| Input | Output | Explanation |
|-------|--------|-------------|
| 11891 | 99009  | Max: 99899 (1→9), Min: 890 (1→0) → 99899-890 |
| 90    | 99     | Max: 99 (0→9), Min: 0 (9→0) → 99-0 |

## Solution Approach
1. Convert number to string for digit manipulation
2. Find maximum possible number:
   - Replace first non-9 digit with 9
3. Find minimum possible number:
   - If first digit isn't 1, replace it with 1
   - Else replace first non-0 digit with 0
4. Return difference between max and min

```python
class Solution:
    def minMaxDifference(self, num: int) -> int:
        s = str(num)
        
        # Find digit to replace for maximum
        max_digit = None
        for d in s:
            if d != '9':
                max_digit = d
                break
        
        # Calculate maximum number
        max_num = int(s.replace(max_digit, '9')) if max_digit else num
        
        # Find digit to replace for minimum
        min_digit = s[0]
        
        # Calculate minimum number
        min_num = int(s.replace(min_digit, '0'))
        
        return max_num - min_num
