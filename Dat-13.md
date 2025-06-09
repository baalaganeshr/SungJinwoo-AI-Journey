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
