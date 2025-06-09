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


# Remove Element

**Problem:** Remove all instances of a specific value from an array in-place.

**Date:** June 4, 2025 | **Day:** -8

## The Problem

Given array `nums` and value `val`, remove all occurrences of `val`. Return count of remaining elements.

**Example:**
```
Input:  nums = [3,2,2,3], val = 3
Output: nums = [2,2,_,_], return 2
```

## Solution

**Idea:** Use one pointer to track where to place non-target elements.

```python
class Solution:
    def removeElement(self, nums, val):
        k = 0  # Position for next good element
        
        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1
        
        return k
```

## How It Works

1. **k pointer** = where to put next good element
2. **Check each element** = if not equal to val, keep it
3. **Move good elements forward** = copy to position k
4. **Count survivors** = k is the final count

## Step by Step

```
nums = [3,2,2,3], val = 3

i=0: nums[0]=3, equals val → skip
     [3,2,2,3], k=0

i=1: nums[1]=2, not val → keep
     [2,2,2,3], k=1

i=2: nums[2]=2, not val → keep  
     [2,2,2,3], k=2

i=3: nums[3]=3, equals val → skip
     [2,2,2,3], k=2

Result: First 2 elements [2,2], return 2
```

## Test It

```python
def test():
    solution = Solution()
    
    # Test 1
    nums1 = [3,2,2,3]
    k1 = solution.removeElement(nums1, 3)
    print(f"Result: {nums1[:k1]}, k={k1}")  # [2,2], k=2
    
    # Test 2  
    nums2 = [0,1,2,2,3,0,4,2]
    k2 = solution.removeElement(nums2, 2)
    print(f"Result: {nums2[:k2]}, k={k2}")  # [0,1,3,0,4], k=5

test()
```

## Key Points

✅ **Modifies array in-place**  
✅ **Order may change (that's okay)**  
✅ **Only first k elements matter**  
✅ **Single pass through array**

## Time & Space


Day-9 ---5/6/25
# Search Insert Position

## Problem Description
Given a sorted array of distinct integers and a target value, return the index where the target is found. If not found, return the insertion index to maintain order.

## Solution
### Binary Search Approach
- **Time Complexity:** O(log n)
- **Space Complexity:** O(1)

- Example Usage

python

print(Solution().searchInsert([1,3,5,6], 5))  # Output: 2

print(Solution().searchInsert([1,3,5,6], 2))  # Output: 1

print(Solution().searchInsert([1,3,5,6], 7))  # Output: 4

How to Use

Copy the code into a file named search_insert_position.py

Import the Solution class where needed

Call the searchInsert method with your sorted array and target value

Note: Don't forget to import List from typing if needed:

python
from typing import List
This version has:

Clear section headers

Proper code formatting

Complete import statement

Better readability

All necessary information in a structured format

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if nums[mid] == target:
                return mid
            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left

- **Time:** O(n) - Check each element once
- **Space:** O(1) - Only use one extra pointer

**Simple and direct.** 🎯
````
## Day-10----6/5/25
# 28. Find the Index of the First Occurrence in a String

## Problem Statement

Given two strings `needle` and `haystack`, return the **index of the first occurrence** of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

---

## Examples


## Input: haystack = "sadbutsad", needle = "sad"
Output: 0

## Input: haystack = "leetcode", needle = "leeto"
Output: -1
## Approaches
1. Built-in Method (Recommended)
Uses Python’s optimized string method .find().

python
Copy
Edit
# class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        return haystack.find(needle)
Complexity:

Time: O(n) average case

Space: O(1)

## 2. Sliding Window Approach
Checks every substring of the same length as needle in haystack.

python
Copy
Edit
# class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        n_len = len(needle)
        for i in range(len(haystack) - n_len + 1):
            if haystack[i:i+n_len] == needle:
                return i
        return -1
# Complexity:

Time: O(m * n) (where m = len(haystack), n = len(needle))

Space: O(1)

Key Points
If needle is an empty string, return 0

If needle is longer than haystack, return -1

Use str.find() for best performance

Sliding window is easier to understand, but less efficient

Example Walkthrough
Input: haystack = "sadbutsad", needle = "sad"

Check substring at index 0: "sad" == "sad" → Return 0

(If continued, would find again at index 6, but return the first match)

Summary
Use .find() for the fastest solution.

Sliding window method is useful for interviews and learning.

Always handle edge cases (empty strings, needle longer than haystack).
```python
```

#Day-11----7/6/25
## Find Length of the Last Word

## The Problem
- You're given a sentence with words and spaces (like `"Hello World"`)
- You need to find how many letters are in the **last word**
- Ignore any extra spaces at the end

## Examples
1. `"Hello World"` → Last word is `"World"` (5 letters) → Answer: `5`
2. `"   fly me   to   the moon  "` → Last word is `"moon"` (4 letters) → Answer: `4` 
3. `"luffy is still joyboy"` → Last word is `"joyboy"` (6 letters) → Answer: `6`

## How to Solve It
### Simple Steps:
1. Remove extra spaces from the end
2. Find where the last space is
3. Count letters after that last space

4. How It Works
rstrip() - Cleans up extra spaces at the end

rfind(' ') - Finds the position of the last space

The length is calculated from after the last space to the end

Input: 'Hello World'
Output: 5
------------------------------
Input: '   fly me   to   the moon  '
Output: 4
------------------------------
Input: 'luffy is still joyboy'
Output: 6
------------------------------
Input: 'single'
Output: 6
------------------------------
Input: '    '
Output: 0
------------------------------
Input: ''
Output: 0
------------------------------

### Python Solution
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        # Remove trailing whitespace
        s = s.rstrip()
        # Find the last space
        last_space = s.rfind(' ')
        # Return length from last space to end
        return len(s) - last_space - 1 if last_space != -1 else len(s)

# Test cases
test_cases = [
    "Hello World",
    "   fly me   to   the moon  ",
    "luffy is still joyboy",
    "single",
    "    ",
    ""
]

# Create instance of Solution
solution = Solution()

# Run tests
for test in test_cases:
    print(f"Input: '{test}'")
    print(f"Output: {solution.lengthOfLastWord(test)}")
    print("-" * 30)

```

# Day-12----8/6/25
## Plus One – LeetCode Problem Solution

---

## 🚩 **Problem Summary**
Given an array of digits representing a large integer, increment it by one and return the result as an array.

---

## 🛠️ **Approach**
1. Start from the end of the array and add 1.
2. Handle carry-over if the digit becomes 10.
3. If all digits are 9 (e.g., `[9, 9]`), add a new digit `1` at the front.

---

## 🧩 **Python Solution**
```python
from typing import List

class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        n = len(digits)
        # Start from the end
        for i in range(n - 1, -1, -1):
            if digits[i] < 9:
                digits[i] += 1
                return digits
            digits[i] = 0
        # If all digits are 9, add new digit at front
        return [1] + digits
```
✏️ How It Works
Loop through the digits from right to left:

If the digit is less than 9, add 1 and return the array.

If the digit is 9, set it to 0 and move to the next digit.

If you finish the loop (all 9s), return a new array with 1 at the front, followed by all 0s.

📝 Example Walkthroughs
Input	Output	Explanation
| Input    | Output   | Explanation                     |
| -------- | -------- | ------------------------------- |
| \[1,2,3] | \[1,2,4] | Simple increment                |
| \[9,9]   | \[1,0,0] | All digits roll over, new digit |
| \[9]     | \[1,0]   | Single digit edge case          |


⏱️ Complexity Analysis
Time: O(n) – May scan the entire array once.

Space: O(1) – In-place, except when all digits are 9 (O(n) for the result).

🧠 Why This Solution Works
Efficiently handles all cases, including when a new digit is needed.

Optimized for time and space.




# Day 13: Add Binary (9/6/25)

## 📋 Problem Statement
Given two binary strings `a` and `b`, return their sum as a binary string.

**Examples:**
# Input: a = "11", b = "1" → Output: "100" (3 + 1 = 4)
Input: a = "1010", b = "1011" → Output: "10101" (10 + 11 = 21)


## 🧠 Understanding the Problem
- We're adding two binary numbers represented as strings
- The result should also be a binary string
- Need to handle carry-over when 1+1=10 in binary

## 🛠 Solution Approach
1. **Start from the end** of both strings (least significant bit)
2. **Process each digit** while maintaining a carry
3. **Build the result** in reverse order
4. **Handle remaining carry** at the end

## 💻 Python Solution
```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        result = []
        carry = 0
        i, j = len(a)-1, len(b)-1  # Start from last digits
        
        while i >=  or j >= 0 or carry:
            # Sum current digits and carry
            total = carry
            if i >= 0:
                total += int(a[i])
                i -= 1
            if j >= 0:
                total += int(b[j])
                j -= 1
            
            # Append digit and update carry
            result.append(str(total % 2))
            carry = total // 2
        
        # Reverse to get correct order
        return ''.join(reversed(result))
```
## 🧩 Key Steps Explained
Initialization:

result list to collect digits

carry starts at 0

Pointers start at string ends

Digit Processing:

Sum current digits + carry

Current digit = sum % 2

New carry = sum // 2

Finalization:

Reverse digits (since we built least-significant first)

Join into result string

⏱ Complexity Analysis
Time: O(max(m,n)) - We process each digit once

Space: O(max(m,n)) - For storing the result

🚀 Test Your Understanding
Try these test cases:

"0" + "0" → ?

"111" + "1" → ?

"1101" + "1011" → ?

Answers in spoiler tag below:

<details> <summary>Click for answers</summary>
"0"

"1000"

"11000"

</details>
📝 Takeaways
Binary addition follows the same rules as decimal, but with base 2

Carry management is crucial

Working backwards often simplifies digit operations
