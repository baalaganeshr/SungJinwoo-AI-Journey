# Day 16: Climbing Stairs (12/6/25)

## Problem Statement
You're climbing a staircase with `n` steps. Each time you can take either:
- 1 step
- 2 steps

**How many distinct ways** can you reach the top?

**Constraints:**
- 1 ≤ n ≤ 45

## Examples
| n | Output | Explanation |
|---|--------|-------------|
| 2 | 2      | 1+1 or 2    |
| 3 | 3      | 1+1+1, 1+2, or 2+1 |

## Solution Approaches
### Fibonacci Sequence Pattern
The number of ways follows the Fibonacci sequence:
- Ways(n) = Ways(n-1) + Ways(n-2)
- Base cases: 
  - 1 step → 1 way
  - 2 steps → 2 ways

### Dynamic Programming Solution
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1:
            return 1
        
        # Initialize base cases
        dp = [0] * (n + 1)
        dp[1] = 1  # Only 1 way for 1 step
        dp[2] = 2  # Two ways for 2 steps
        
        for i in range(3, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        
        return dp[n]
```
Space-Optimized Version
python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n == 1:
            return 1
        
        a, b = 1, 2
        for _ in range(3, n + 1):
            a, b = b, a + b
        return b
Key Features
✅ Fibonacci Pattern: Recognizes the sequence pattern

✅ Dynamic Programming: Builds solution from subproblems

✅ Space Optimization: Uses O(1) space with two variables

✅ Handles Edge Cases: Explicit checks for n=1 and n=2

Complexity
Time: O(n) - Single loop through steps

Space:

O(n) for DP array version

O(1) for optimized version

Test Cases
python
sol = Solution()
print(sol.climbStairs(2))  # 2
print(sol.climbStairs(3))  # 3
print(sol.climbStairs(5))  # 8
Learning Progress
Day 16/30 of coding challenges

Date: 12 June 2025

Today's Focus: Dynamic Programming patterns

Need More Explanation?
Why Fibonacci?

Each step depends on the previous two steps' combinations

How DP helps?

Stores intermediate results to avoid recomputation

Can we do better?

Yes, using matrix exponentiation (O(log n) time) but overkill for n ≤ 45



🎯 Outcome of Chapter 2: Semantic Kernel Framework
You have successfully completed Chapter 2: Explore Agentic Frameworks with the following achievements:

✅ What You Accomplished
🔧 Environment Setup
Set up Azure OpenAI service with your student account

Configured API keys and endpoints correctly

Created and deployed gpt-4o-mini model

🤖 Built Your First AI Agent
Created a TravelAgent using the Semantic Kernel framework

Implemented a custom DestinationsPlugin with function calling

Successfully integrated Azure OpenAI with Semantic Kernel

🛠️ Function Calling Mastery
Learned how agents can call external functions

Implemented get_random_destination() function

Saw how agents use tools to provide dynamic responses

💬 Conversational AI
Tested multi-turn conversations

Observed context awareness and memory

Experienced streaming responses

🔍 Technical Skills Gained
Semantic Kernel framework fundamentals

Azure OpenAI integration

Environment variable management

Jupyter Notebook development

Agent debugging and troubleshooting

📊 Key Results
Agent Response 1: Generated detailed Bali, Indonesia day trip plan

Agent Response 2: Provided alternative Sydney, Australia vacation on request

Function Calls: Successfully executed random destination selection

Conversation Flow: Maintained context between user requests

🧠 Knowledge Acquired
Understanding of agentic frameworks architecture

Difference between simple chatbots and intelligent agents

How agents use plugins/tools to extend capabilities

Authentication and API management for AI services

Streaming vs. non-streaming AI responses

🚀 Ready for Chapter 3: Agentic Design Patterns
Now you're prepared to learn:

🎨 Design principles for building effective agents

👥 Human-centric UX considerations

🧭 Best practices for agent behavior

🧵 Advanced conversation patterns

