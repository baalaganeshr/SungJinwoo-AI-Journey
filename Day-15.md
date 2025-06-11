# Day 15: Maximum Frequency Difference (11/6/25)

## Problem Statement
Given a string `s` (digits '0'-'4') and integer `k`, find the maximum difference between:
- Frequency of a character with **odd count** (a)
- Frequency of a character with **even count** (b)
in any substring of length ≥ `k`.

**Constraints:**
- 3 ≤ s.length ≤ 3×10⁴
- 1 ≤ k ≤ s.length

## Examples
| Input       | k | Output | Explanation                          |
|-------------|---|--------|--------------------------------------|
| "12233"     | 4 | -1     | "12233": freq('1')=1 (odd), freq('3')=2 → 1-2 = -1 |
| "1122211"   | 3 | 1      | "11222": freq('2')=3 (odd), freq('1')=2 → 3-2 = 1 |
| "110"       | 3 | -1     | No valid substring                   |

## Optimized Solution
### Prefix Sum with Parity Tracking
```python
from math import inf

class Solution:
    def maxDifference(self, s: str, k: int) -> int:
        n = len(s)
        
        # prefix[d][i] = count of digit d in s[0..i-1]
        prefix = [[0] * (n + 1) for _ in range(5)]
        for i, ch in enumerate(s, 1):
            d = int(ch)
            for dig in range(5):
                prefix[dig][i] = prefix[dig][i - 1]
            prefix[d][i] += 1

        best = -inf

        for odd in range(5):  # Possible odd-frequency digits
            for even in range(5):  # Possible even-frequency digits
                if odd == even:
                    continue

                # Track minimum (prefix[odd] - prefix[even]) by parity
                minDiff = [[inf, inf], [inf, inf]]
                left = 0

                for r in range(1, n + 1):
                    # Update minDiff for valid prefixes
                    while (left <= r - k and
                           prefix[odd][left] < prefix[odd][r] and
                           prefix[even][left] < prefix[even][r]):
                        
                        pa = prefix[odd][left] & 1
                        pb = prefix[even][left] & 1
                        diff_l = prefix[odd][left] - prefix[even][left]
                        minDiff[pa][pb] = min(minDiff[pa][pb], diff_l)
                        left += 1

                    # Check substrings ending at r-1
                    if r >= k:
                        cntA = prefix[odd][r]
                        cntB = prefix[even][r]
                        
                        need_pa = 1 - (cntA & 1)  # Need odd count in window
                        need_pb = cntB & 1        # Need even count in window
                        
                        if minDiff[need_pa][need_pb] < inf:
                            cand = (cntA - cntB) - minDiff[need_pa][need_pb]
                            best = max(best, cand)

        return -1 if best == -inf else best
```
Key Features
✅ Prefix Arrays: Track digit counts at each position

✅ Parity Optimization: Uses bitwise AND (&1) for odd/even checks

✅ Sliding Window: Efficiently checks valid substrings

✅ Early Termination: Skips invalid digit pairs

Complexity
Time: O(n) - Single pass through string for each digit pair

Space: O(n) - Prefix arrays storage

Test Cases
python
sol = Solution()
print(sol.maxDifference("12233", 4))    # -1
print(sol.maxDifference("1122211", 3))  # 1
print(sol.maxDifference("0000", 2))     # 0
Learning Progress
Day 15/30 of coding challenges

Date: 11 June 2025

Today's Focus: Advanced frequency analysis

Need Clarification?
Why prefix arrays?

Enables O(1) range frequency queries

How parity helps?

Tracks odd/even counts without full recomputation

Edge cases handled?

Returns -1 when no valid substring exists
