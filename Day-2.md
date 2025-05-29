# LeetCode 9. Palindrome Number — Solution Documentation Date : 29/5/25

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

---

**Happy coding!** 🎉 And the Microsoft ai learning 
# 🚀 AI Agents Learning Course — Beginner-Friendly Setup Guide

Want to get hands-on with this course on your own computer?  
Follow these simple steps to get started!

---

## 1. 📥 Clone This Repository

First, download the course files to your computer.

```bash
git clone https://github.com/baalaganeshr/ai-agents-learning.git
cd ai-agents-learning
2. 🐍 Install Python 3.11
Go to the Python 3.11 download page.

Download and install Python 3.11.

IMPORTANT: During setup, check the box that says Add Python to PATH.

3. 🧪 Create Your Own Python Environment
This keeps your course code separate from other projects.

bash
Copy
Edit
py -3.11 -m venv venv311
venv311\Scripts\activate
4. 📦 Install All Required Packages
This command installs everything the course needs.

bash
Copy
Edit
pip install -r requirements.txt
5. 🔒 Set Up Your Secret Keys (.env File)
Copy the example file:

bash
Copy
Edit
cp .env.example .env
(Or, copy and rename it using File Explorer if you prefer)

Open the new .env file in VS Code or Notepad.

Get your GitHub Personal Access Token (how-to guide here).

Paste your token into the file like this:

env
Copy
Edit
GITHUB_TOKEN="ghp_yourTokenHere"
Save the file.

6. 💻 Open and Run Notebooks in Visual Studio Code
Make sure you have both the Python and Jupyter extensions installed in VS Code.

Open the project folder (ai-agents-learning) in VS Code.

Open any notebook file (it ends in .ipynb, like semantic-kernel.ipynb).

At the top right, select the Python 3.11 (venv311) kernel if it asks.

Click the “Run” (▶️) button or use Shift+Enter to run code cells.

7. 🛠 Troubleshooting
Packages not installing? Double-check that you’re using Python 3.11, not a newer version.

Authentication errors? Make sure your GitHub token is correct in your .env file.

.env file issues? Never upload/share your .env file—it should be private.

Example .env File (GitHub Models Only)
env
Copy
Edit
GITHUB_TOKEN="ghp_yourTokenHere"
Common Commands Cheat Sheet
Command	What it does
py -3.11 -m venv venv311	Create a virtual Python environment
venv311\Scripts\activate	Activate your environment (Windows)
pip install -r requirements.txt	Install all course dependencies
cp .env.example .env	Create your secret settings file


