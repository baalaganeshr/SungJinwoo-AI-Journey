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

