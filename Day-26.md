# Day 26: Divide String Into Groups (22/6/25)

## Problem Statement
Given a string `s`, integer `k`, and character `fill`, divide `s` into groups of size `k`. For the last group, pad with `fill` if needed.

**Constraints:**
- 1 ≤ s.length ≤ 100
- s consists of lowercase English letters
- 1 ≤ k ≤ 100
- fill is lowercase English letter

## Examples

Input: s = "abcdefghi", k = 3, fill = "x" → Output: ["abc","def","ghi"]
Input: s = "abcdefghij", k = 3, fill = "x" → Output: ["abc","def","ghi","jxx"]
Solution Approach
Iterative Grouping with Padding
Initialize empty result list

Iterate through string in steps of k

For each group:

Take next k characters

Pad with fill if needed

Return the groups

```python
class Solution:
    def divideString(self, s: str, k: int, fill: str) -> List[str]:
        result = []
        for i in range(0, len(s), k):
            group = s[i:i+k]
            if len(group) < k:
                group += fill * (k - len(group))
            result.append(group)
        return result


```
Key Features
✅ Simple Iteration: Processes string in chunks

✅ Automatic Padding: Handles last group gracefully

✅ Efficient: O(n) time complexity

✅ Readable: Clear variable names


