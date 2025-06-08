# Plus One – LeetCode Problem Solution

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
## Today i work on the vs code to develop the chatbot using hugging face but im not just copy paste the code and it gives the output 
![WhatsApp Image 2025-06-08 at 11 50 55_81bd319d](https://github.com/user-attachments/assets/854968b3-adaf-48b5-9de9-d792a204b218)

![WhatsApp Image 2025-06-08 at 11 51 17_60ad927b](https://github.com/user-attachments/assets/1d8f1f9b-4e27-4177-b341-5612b48eb799)
![WhatsApp Image 2025-06-08 at 11 53 46_8da6d95c](https://github.com/user-attachments/assets/2a0363ed-ab9e-4e81-b196-a67577c36da2)
