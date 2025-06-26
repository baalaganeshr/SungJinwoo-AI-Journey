# Day 30: Pascal's Triangle (26/6/25)

## Problem Statement
Given an integer `numRows`, generate the first `numRows` of Pascal's triangle where each number is the sum of the two numbers directly above it.

**Constraints:**
- 1 ≤ numRows ≤ 30

## Examples

Input: 5 → Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
Input: 1 → Output: [[1]]

```python

class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        triangle = []
        
        for row_num in range(numRows):
            row = [1] * (row_num + 1)
            
            # Calculate middle elements for rows >= 2
            for j in range(1, len(row)-1):
                row[j] = triangle[row_num-1][j-1] + triangle[row_num-1][j]
            
            triangle.append(row)
        
        return triangle
