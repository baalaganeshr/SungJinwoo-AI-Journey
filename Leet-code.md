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
```
# Day-5 20.Valid Parentheses

> **LeetCode Problem**: Check if parentheses, brackets, and braces are properly balanced and closed in correct order.

## 🎯 Problem Description

Given a string containing only `()`, `{}`, and `[]` characters, determine if the brackets are valid.

**Valid means:**
- Every opening bracket has a matching closing bracket
- Brackets are closed in the correct order
- Each closing bracket matches the most recent unmatched opening bracket

## 📝 Examples

| Input | Output | Explanation |
|-------|--------|-------------|
| `"()"` | `true` | Simple pair matches |
| `"()[]{}"` | `true` | Multiple pairs in sequence |
| `"(]"` | `false` | Wrong bracket type |
| `"([)]"` | `false` | Wrong closing order |
| `"{[]}"` | `true` | Nested brackets |

## 💡 Solution Approach

**Stack-based solution:**
1. Use a stack to track opening brackets
2. For each character:
   - **Opening bracket** → Push to stack
   - **Closing bracket** → Check if it matches the top of stack
3. String is valid if stack is empty at the end

**Time Complexity:** O(n)  
**Space Complexity:** O(n)

## 🔧 Implementation

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        # Map each closing bracket to its opening bracket
        bracket_map = {')': '(', '}': '{', ']': '['}
        
        for char in s:
            if char in bracket_map:  # Closing bracket
                # Check if stack is empty or top doesn't match
                if not stack or stack.pop() != bracket_map[char]:
                    return False
            else:  # Opening bracket
                stack.append(char)
        
        # Valid if no unmatched opening brackets remain
        return len(stack) == 0
```

## 🧪 Test Cases

```python
def test_valid_parentheses():
    solution = Solution()
    
    # Test cases
    assert solution.isValid("()") == True
    assert solution.isValid("()[]{}")  == True
    assert solution.isValid("(]") == False
    assert solution.isValid("([)]") == False
    assert solution.isValid("{[]}") == True
    assert solution.isValid("") == True  # Empty string
    
    print("All test cases passed! ✅")

# Run tests
test_valid_parentheses()
```

## 🚀 How to Run

```bash
# Clone the repository
git clone <your-repo-url>

# Navigate to the directory
cd valid-parentheses

# Run the solution
python valid_parentheses.py

# Run tests
python test_valid_parentheses.py
```

## 🤔 Key Insights

- **Why Stack?** LIFO (Last In, First Out) nature perfectly matches bracket closing order
- **Edge Cases:** Empty string (valid), single bracket (invalid), mixed types
- **Optimization:** Early return when mismatch found

## 📚 Related Problems

- **Remove Invalid Parentheses** (Hard)
- **Generate Parentheses** (Medium)
- **Longest Valid Parentheses** (Hard)

---

**Author:** [Your GitHub Username]  
**Difficulty:** Easy  
**Tags:** `Stack`, `String`, `LeetCode`
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

