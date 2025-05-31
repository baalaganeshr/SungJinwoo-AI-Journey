 # LeetCode 9. Palindrome Number — Solution Documentation Date : 29/5/25
## Day 2 - 29/05/25

## Problem Statement

Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.

**A palindrome** is a number that reads the same forward and backward.

### Example

* Input: `x = 121`  → Output: `true`
* Input: `x = -121` → Output: `false`
* Input: `x = 10`   → Output: `false`

**Constraints:**

* -2<sup>31</sup> ≤ x ≤ 2<sup>31</sup> - 1

## Approach

* Negative numbers are **not** palindromes.
* Numbers ending with 0 (except 0 itself) are **not** palindromes.
* Reverse the last half of the digits, and compare it to the first half.
* Do **not** convert the number to a string!

## Step-by-Step Algorithm

1. **Edge Cases:**

   * If `x < 0`, return `False`.
   * If `x` ends with a 0 (and is not 0 itself), return `False`.
2. **Reversing Half the Number:**

   * Create a variable `reversed_half = 0`.
   * While `x > reversed_half`:

     * Pop the last digit from `x` (`x % 10`).
     * Append that digit to `reversed_half`.
     * Remove the last digit from `x` (integer division by 10).
3. **Final Comparison:**

   * If the number has even digits: `x == reversed_half`.
   * If the number has odd digits: `x == reversed_half // 10` (ignore the middle digit).

## Final Solution (Python 3)

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0 or (x != 0 and x % 10 == 0):
            return False
        reversed_half = 0
        while x > reversed_half:
            digit = x % 10
            reversed_half = reversed_half * 10 + digit
            x = x // 10
        return x == reversed_half or x == reversed_half // 10
```

## Beginner-Friendly Version (No Type Hints)

If you need to run it in Python2 or without type hints, use:

```python
class Solution:
    def isPalindrome(self, x):
        if x < 0 or (x != 0 and x % 10 == 0):
            return False
        reversed_half = 0
        while x > reversed_half:
            digit = x % 10
            reversed_half = reversed_half * 10 + digit
            x = x // 10
        return x == reversed_half or x == reversed_half // 10
```

## Key Points

* No string conversion needed.
* Handles negative numbers and zeros correctly.
* Efficient: Time complexity is O(log₁₀(n)), Space complexity O(1).
* Always use Python3 on LeetCode for type hints support!

## Troubleshooting

* If you get a **SyntaxError** on LeetCode, check that you are using **Python3** as your language.
* If you get `NameError: global name 'Solution' is not defined`, make sure you did **not remove** the `class Solution:` header.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------
# DAY-3 # Date 30/5/25 Roman Numeral to Integer Converter

This project contains a Python solution for converting Roman numeral strings into integers.

---

## Problem Overview

Roman numerals are written from largest to smallest from left to right, but sometimes a smaller numeral comes before a larger one, meaning subtraction (e.g., IV = 4, IX = 9). This code handles both normal and subtraction cases to give the correct integer value.

---

## Solution Approach

1. **Mapping Creation:**  
   A dictionary (`roman_to_int`) maps each Roman numeral to its integer value.

2. **Reverse Iteration:**  
   Iterate through the input string from right to left. This allows easy comparison to handle subtraction cases.

3. **Subtraction Handling:**  
   - If the current numeral is less than the previous (in the original string), subtract its value from the total.
   - Otherwise, add its value to the total.

4. **Final Calculation:**  
   The variable `total` stores the final integer result.

Example
Input: "MCMXCIV"

Output: 1994

Explanation:

M (1000), CM (900), XC (90), IV (4)

1000 + 900 + 90 + 4 = 1994



---

## Python Solution

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        roman_to_int = {
            'I': 1,
            'V': 5,
            'X': 10,
            'L': 50,
            'C': 100,
            'D': 500,
            'M': 1000
        }
        
        total = 0
        prev_value = 0
        
        for char in reversed(s):
            current_value = roman_to_int[char]
            if current_value < prev_value:
                total -= current_value
            else:
                total += current_value
            prev_value = current_value
        
        return total
----------------
```
# Day-4 Date 31/5/25 LeetCode 14. Longest Common Prefix — Solution Documentation

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


