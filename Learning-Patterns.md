# 🟢 Two Sum — Beginner-Friendly Explanation

## Problem

Given a list of numbers, **find two numbers that add up to a specific target**.

**Example:**
- Numbers: `[2, 7, 11, 15]`
- Target: `9`
- **Answer:** `2 + 7 = 9` (positions 0 and 1)

---

## Step-by-Step Solution

### 1. Visualize the List as Boxes

Think of each number as a box lined up in a row.  
Your job: **Find two boxes whose numbers add up to the target.**

---

### 2. Brute-Force Approach (Try Every Pair)

Try all possible pairs of numbers.  
As soon as you find a pair that adds to the target, stop.

---


4. What Each Line Does


nums = [...] — Your list of numbers

target = 9 — The goal you want to reach

found = False — Haven’t found the answer yet

for i in range(len(nums)): — Look at each position in the list

for j in range(i + 1, len(nums)): — For each position, look at every next position (no repeats)

if nums[i] + nums[j] == target: — Check if the two numbers add up to the target

print(...) — Show which boxes (positions) and which numbers you found

break — Stop searching when the answer is found

5. How Does It Work?
Checks every unique pair:

First checks 2+7, 2+11, 2+15

Then 7+11, 7+15

And so on

If it finds a match (2+7=9), it prints the answer and stops

6. Key Points
Index is the position in the list (starts at 0)

range(len(nums)) gives you every position

Inner loop starts after current outer loop position (no repeats)

When found is True, both loops stop (so you only find the first solution)

Works for any list and target!

🔑 Summary
Try every pair of numbers

Stop as soon as you find a match

Print out where and what the match is

### 3. Python Code

```python
nums = [2, 7, 11, 15]   # The numbers you have
target = 9              # The sum you want to find

found = False           # Flag to track if you found the answer

for i in range(len(nums)):               # Look at each box (from start to end)
    for j in range(i + 1, len(nums)):    # Look at each box AFTER the current one
        if nums[i] + nums[j] == target:  # If these two add up to the target
            print("Found at positions:", i, "and", j)
            print("Numbers are:", nums[i], "and", nums[j])
            found = True
            break   # Stop inner loop if found
    if found:
        break       # Stop outer loop if found
