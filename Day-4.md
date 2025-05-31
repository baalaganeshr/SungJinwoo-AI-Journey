# 🐞 Troubleshooting Log - AI Agents Setup

## Common Issues & Quick Fixes

### 1. VS Code Not Using Correct Environment
**Problem:** VS Code using wrong Python/kernel
**Fix:**
- Press `Ctrl+Shift+P` → "Python: Select Interpreter"
- Choose `venv311\Scripts\python.exe`
- Or click kernel selector (top-right in notebook)

### 2. Module Not Found Errors
**Problem:** `ModuleNotFoundError: No module named 'dotenv'`
**Fix:**

# Make sure venv is active first
.\venv311\Scripts\Activate.ps1
pip install python-dotenv
3. Pip Installing to Wrong Location
Problem: Packages installing globally instead of venv
Fix:
bash# Always activate venv first
.\venv311\Scripts\Activate.ps1
# Then install
pip install package-name
4. Azure OpenAI Connection Errors
Problem: API connection failed, authentication errors
Fix:

Check .env file has correct values from Azure Portal:

AZURE_OPENAI_API_KEY=your-key-here
AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_CHAT_DEPLOYMENT_NAME=your-deployment-name

No quotes, no spaces, exact match from Azure Portal

5. Wrong Method Names
Problem: AttributeError: no attribute 'complete'
Fix: Use correct Semantic Kernel pattern:
pythonfrom semantic_kernel.functions import KernelFunctionFromPrompt

kernel_function = KernelFunctionFromPrompt(
    function_name="chat",
    prompt="You are helpful. {{$input}}"
)

result = await kernel_function.invoke(kernel=kernel, input="Hello")
6. Async Function Issues
Problem: Getting <coroutine object> instead of result
Fix:
pythonimport asyncio

async def main():
    result = await kernel_function.invoke(kernel=kernel, input="Hello")
    print(result)

# Run async function
asyncio.run(main())
7. PowerShell Navigation
Problem: Can't change directories in PowerShell
Fix:
bash# Use cd command to navigate
cd D:\python\ai-agents-learning
# Then activate venv
.\venv311\Scripts\Activate.ps1
🎯 Quick Checklist Before Running Code

 Virtual environment activated (venv311)
 Correct kernel selected in VS Code
 .env file has all required values
 All packages installed in venv
 Using await for async functions

💡 Pro Tips

Always activate venv before installing packages
Double-check Azure Portal values exactly
Read error messages carefully - they tell you what's missing
Use print(sys.executable) to verify correct Python path

