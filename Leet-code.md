LeetCode 9. Palindrome Number — Solution Documentation Date : 29/5/25
Day 2 - 29/05/25
Problem Statement
Given an integer x, return true if x is a palindrome, and false otherwise.

A palindrome is a number that reads the same forward and backward.

Example
Input: x = 121 → Output: true
Input: x = -121 → Output: false
Input: x = 10 → Output: false
Constraints:

-231 ≤ x ≤ 231 - 1
Approach
Negative numbers are not palindromes.
Numbers ending with 0 (except 0 itself) are not palindromes.
Reverse the last half of the digits, and compare it to the first half.
Do not convert the number to a string!
Step-by-Step Algorithm
Edge Cases:

If x < 0, return False.
If x ends with a 0 (and is not 0 itself), return False.
Reversing Half the Number:

Create a variable reversed_half = 0.

While x > reversed_half:

Pop the last digit from x (x % 10).
Append that digit to reversed_half.
Remove the last digit from x (integer division by 10).
Final Comparison:

If the number has even digits: x == reversed_half.
If the number has odd digits: x == reversed_half // 10 (ignore the middle digit).
Final Solution (Python 3)
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
Beginner-Friendly Version (No Type Hints)
If you need to run it in Python2 or without type hints, use:

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
Key Points
No string conversion needed.
Handles negative numbers and zeros correctly.
Efficient: Time complexity is O(log₁₀(n)), Space complexity O(1).
Always use Python3 on LeetCode for type hints support!
Troubleshooting
If you get a SyntaxError on LeetCode, check that you are using Python3 as your language.
If you get NameError: global name 'Solution' is not defined, make sure you did not remove the class Solution: header.

