# Day 31: Pascal's Triangle II (27/6/25)

## Problem Statement
Given a 0-indexed `rowIndex`, return that specific row from Pascal's triangle.

**Constraints:**
- 0 ≤ rowIndex ≤ 33

## Examples

Input: 3 → Output: [1,3,3,1]
Input: 0 → Output: [1]
Input: 1 → Output: [1,1]

```python

class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        row = [1] * (rowIndex + 1)
        
        for i in range(1, rowIndex):
            # Compute from right to left to avoid overwriting
            for j in range(i, 0, -1):
                row[j] += row[j-1]
        
        return row
