# Day-6 2/6/25 n8n Crash Course - Simple Guide

**Date:** June 2, 2025

## What is n8n?

n8n is a visual automation tool that connects apps without coding. Think drag-and-drop workflow builder.

**Like:** Zapier but free and more powerful

## Key Terms

- **Node** = One action (send email, call API)
- **Workflow** = Chain of nodes working together
- **Trigger** = What starts your workflow
- **Action** = What the workflow does

## Quick Start (5 Steps)

1. **Open n8n** → Usually at `http://localhost:5678`
2. **Click "New Workflow"**
3. **Add nodes** → Click "+" button
4. **Connect nodes** → Drag lines between them
5. **Test** → Click "Execute Workflow"

## Simple Example

**Goal:** Chat → AI → Email

### Setup:
```
Chat Trigger → Ollama AI → Send Email
```

### Configure Each Node:
1. **Chat Trigger**: Leave default settings
2. **Ollama AI**: 
   - Model: `codellama:7b`
   - Prompt: `{{$json.chatInput}}`
3. **Email**: 
   - Add your email settings
   - Body: `{{$json.output}}`

### Result:
Type message → AI responds → Email sent automatically

## Useful Nodes

**Basic:**
- Chat Trigger (manual input)
- HTTP Request (get data from websites)
- Email (send notifications)

**Smart:**
- IF Node (make decisions)
- Set Node (store data)
- Merge Node (combine data)

**AI:**
- Ollama (local AI)
- OpenAI (ChatGPT)
- Google AI

## Real Business Example

**Auto Inventory Check:**
```
New Order → Check Stock → AI Decision → Low Stock? → Email Supplier
```

**Nodes:**
1. Webhook (new order comes in)
2. HTTP Request (check inventory API)
3. Ollama AI (analyze if restock needed)
4. IF Node (stock low?)
5. Email (notify supplier)

## Pro Tips

✅ **Test each node separately first**  
✅ **Give nodes clear names**  
✅ **Start simple, then add complexity**  
✅ **Use templates for common patterns**  

## Common Workflow Patterns

### Pattern 1: Data Processing
```
Trigger → Get Data → Process → Save → Notify
```

### Pattern 2: Smart Alerts
```
Monitor → Analyze → Decision → Alert → Action
```

### Pattern 3: Multi-step Automation
```
Event → Validate → Process → Update → Report
```

## Getting Started Checklist

- [ ] Open n8n interface
- [ ] Create first simple workflow
- [ ] Test each node
- [ ] Connect 2-3 nodes together
- [ ] Try the chat → AI → email example
- [ ] Build one real business workflow

## Next Steps

1. **Week 1**: Master basic nodes
2. **Week 2**: Try HTTP requests and APIs
3. **Week 3**: Add AI and decision logic
4. **Week 4**: Build complete business automation

**Start with one simple workflow today. Build from there.**
