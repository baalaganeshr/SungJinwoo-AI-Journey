# Find Length of the Last Word

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
