# Ollama + n8n Integration Guide

> **Issue**: Ollama model works in terminal but fails to connect in n8n workflows

This guide provides step-by-step solutions to fix Ollama connectivity issues with n8n automation platform.

## 🔍 Problem Diagnosis

**Symptoms:**
- ✅ Ollama responds correctly in terminal/CLI
- ❌ n8n Ollama node shows connection errors
- ❌ Workflows fail at Ollama Chat Model node

## 🔧 Solution Steps

### 1. Configure n8n Ollama Node Settings

Open your **Ollama Chat Model** node and verify these exact settings:

| Setting | Correct Value | ❌ Common Mistakes |
|---------|---------------|-------------------|
| **Base URL** | `http://localhost:11434` | `https://localhost:11434`, `http://127.0.0.1:11434` |
| **Model** | `codellama:7b` | Case mismatch, wrong model name |
| **Credential** | `None` | Unnecessary API credentials |

### 2. Test Connection URL

**Verify Ollama is accessible:**
1. Open browser and navigate to: `http://localhost:11434`
2. **Expected result:** Ollama info page displays
3. **If page doesn't load:** Connection issue exists

### 3. Fix Common Connection Issues

#### Option A: Standard Setup
```yaml
Base URL: http://localhost:11434
Credential: None
Model: codellama:7b  # Use exact name from `ollama list`
```

#### Option B: Docker Environment
If n8n runs in Docker container:
```yaml
Base URL: http://host.docker.internal:11434
# or use your machine's IP
Base URL: http://192.168.1.100:11434
```

### 4. Troubleshooting Checklist

**Step-by-step verification:**

- [ ] Remove any existing credentials (set to "None")
- [ ] Use exact URL: `http://localhost:11434`
- [ ] Match model name exactly from `ollama list` output
- [ ] Test the node connection
- [ ] Restart n8n if changes don't take effect

### 5. Environment-Specific Fixes

#### Local n8n Installation
```bash
# Ensure Ollama is running
ollama serve

# Test connection
curl http://localhost:11434/api/version
```

#### Docker n8n Installation
```yaml
# In docker-compose.yml or run command
networks:
  - bridge
extra_hosts:
  - "host.docker.internal:host-gateway"
```

## ✅ Verification Steps

After applying fixes:

1. **Test Ollama directly:**
   ```bash
   ollama list
   ollama run codellama:7b "Hello world"
   ```

2. **Test n8n connection:**
   - Execute workflow with Ollama node
   - Check node execution logs
   - Verify successful response

3. **Browser test:**
   - Visit `http://localhost:11434`
   - Confirm Ollama service info displays

## 🎯 Most Common Solution

**90% of issues are fixed by:**

```yaml
Base URL: http://localhost:11434
Credential: None
Model: [exact name from ollama list]
```

## 🚀 Next Steps After Success

Once connected successfully:

### Workflow Optimization
- **Keep `ollama serve` running** when using n8n
- **Use consistent model names** across workflows
- **Monitor resource usage** for large models

### Advanced Usage
- Build SME automation workflows
- Test different prompts for business use cases
- Create local AI pipelines without API costs

### Best Practices
- **Document working configurations** for team reference
- **Test connections** after system restarts
- **Use version control** for n8n workflows

## 🔄 Maintenance Commands

```bash
# Check Ollama status
ollama list
ollama ps

# Restart Ollama service
pkill ollama
ollama serve

# Update models
ollama pull codellama:7b
```

## 📝 Common Error Messages

| Error | Cause | Solution |
|-------|-------|----------|
| "Connection refused" | Ollama not running | Run `ollama serve` |
| "Model not found" | Wrong model name | Check `ollama list` output |
| "Invalid credentials" | Unnecessary auth | Set credential to "None" |
| "Network timeout" | Wrong URL/port | Use `http://localhost:11434` |

## 🎉 Success Indicators

**You've successfully integrated when:**
- ✅ n8n Ollama node executes without errors
- ✅ Workflow completes with AI responses
- ✅ No connection timeout messages
- ✅ Consistent performance across workflow runs

---

**💡 Pro Tip:** Save this configuration as a template workflow in n8n for future projects!

**Tags:** `n8n`, `Ollama`, `Local AI`, `Automation`, `Troubleshooting`

# Day 5-6: AI Agent Workflow Breakthrough

## Major Achievements
- ✅ N8N environment setup complete
- ✅ First AI Agent workflow created
- ✅ Ollama CodeLlama 7B integrated
- ✅ Chat interface with memory system
- ✅ Local AI infrastructure operational

## Technical Setup
- N8N Docker installation
- Ollama CodeLlama 7B model
- Workflow components: Chat trigger → AI Agent → Memory

## Testing Results
[hello

Hello!

can tell me some joke

Sure! Here's a joke for you:

Why was the math book sad?

Because it had too many problems.

I hope that made you smile!

]

## Business Applications Identified
[Integrate mcp server]

## Next Steps
[Tomorrow's Python exam + Azure access plan]
