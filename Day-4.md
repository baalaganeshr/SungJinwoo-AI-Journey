# Day 31/5/25  LeetCode 14. Longest Common Prefix — Solution Documentation

## Problem Statement

Given an array of strings, write a function to find the **longest common prefix** string amongst them.  
If there is no common prefix, return an empty string `""`.

### Example

- Input: `strs = ["flower","flow","flight"]`  
  Output: `"fl"`
- Input: `strs = ["dog","racecar","car"]`  
  Output: `""`

**Constraints:**
- `1 <= strs.length <= 200`
- `0 <= strs[i].length <= 200`
- `strs[i]` consists of only lowercase English letters.

---

## Approach

We use the **Vertical Scanning** method:

1. Compare characters at the same position in every string.
2. Stop at the first mismatch or the end of the shortest string.
3. Return the prefix up to that position.

---

## Step-by-Step Algorithm

1. **Check for Empty Input:**  
   Return `""` if the input list is empty.
2. **Find the Length of the Shortest String:**  
   The common prefix cannot be longer than the shortest word.
3. **Compare Characters Vertically:**  
   - For each character index up to the minimum length:
     - Check if all strings share the same character at this position.
     - If a mismatch is found, return the prefix found so far.
     - Otherwise, add the character to the prefix.
4. **Return Result:**  
   Return the accumulated prefix after checking all character positions.

---

## Solution Code (Python)

```python
from typing import List

class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""
        
        min_len = min(len(s) for s in strs)
        common_prefix = []
        
        for i in range(min_len):
            current_char = strs[0][i]
            for s in strs:
                if s[i] != current_char:
                    return ''.join(common_prefix)
            common_prefix.append(current_char)
        
        return ''.join(common_prefix)

