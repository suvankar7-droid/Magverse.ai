# 🤖 OpenRouter API Setup Guide

## ✅ OpenRouter API Integration Complete!

Your Magverse AI is now ready to connect with 6 powerful AI models through OpenRouter!

---

## 🎯 What is OpenRouter?

OpenRouter provides **unified access** to multiple AI models through a single API:
- ✅ GPT-4 Turbo (OpenAI)
- ✅ Claude 3 Opus (Anthropic)
- ✅ Gemini Pro (Google)
- ✅ Llama 3 70B (Meta)
- ✅ Mistral Large (Mistral AI)
- ✅ Command R+ (Cohere)

**Benefits:**
- 💰 Pay-as-you-go pricing
- 🚀 No need for multiple API keys
- ⚡ Fast and reliable
- 📊 Usage tracking
- 🆓 Free credits to start

---

## 📝 Step-by-Step Setup (5 minutes)

### Step 1: Create OpenRouter Account

1. **Visit OpenRouter:**
   ```
   https://openrouter.ai/
   ```

2. **Click "Sign In" (top right)**

3. **Sign up with:**
   - Google Account (recommended)
   - GitHub Account
   - Email & Password

4. **Account created!** ✅

---

### Step 2: Get Your API Key

1. **After login, go to API Keys page:**
   ```
   https://openrouter.ai/keys
   ```

2. **Click "Create Key" button**

3. **Give it a name:**
   ```
   Name: Magverse AI
   ```

4. **Click "Create"**

5. **Copy your API key:**
   ```
   Format: sk-or-v1-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

6. **⚠️ IMPORTANT:** Save this key safely! You won't see it again.

---

### Step 3: Add Free Credits (Optional but Recommended)

1. **OpenRouter gives free credits to start**
   - Usually $1-5 in free credits
   - Enough for testing

2. **To add more credits:**
   - Go to: https://openrouter.ai/credits
   - Click "Add Credits"
   - Choose amount ($5, $10, $20, etc.)
   - Pay with credit card

3. **Usage costs:**
   ```
   GPT-4 Turbo:    ~$0.01 per message
   Claude 3 Opus:  ~$0.015 per message
   Gemini Pro:     ~$0.0005 per message (cheapest!)
   Llama 3:        ~$0.0007 per message
   Mistral Large:  ~$0.008 per message
   Command R+:     ~$0.003 per message
   ```

---

### Step 4: Add API Key to Your Project

#### Method 1: Using .env File (Recommended)

1. **Create `.env` file in project root:**
   ```
   Project Root
   ├── src/
   ├── public/
   ├── .env  ← Create this file here
   └── package.json
   ```

2. **Open `.env` file and add:**
   ```env
   VITE_OPENROUTER_API_KEY=sk-or-v1-your_actual_key_here
   ```

3. **Replace `sk-or-v1-your_actual_key_here` with your real API key**

4. **Save the file**

5. **⚠️ IMPORTANT:** Add `.env` to `.gitignore` (already done):
   ```
   .env
   .env.local
   ```

#### Method 2: Direct in Code (Not Recommended for Production)

1. **Open:** `src/services/aiService.js`

2. **Find line 6:**
   ```javascript
   const OPENROUTER_API_KEY = import.meta.env.VITE_OPENROUTER_API_KEY || 'sk-or-v1-YOUR_API_KEY_HERE';
   ```

3. **Replace with:**
   ```javascript
   const OPENROUTER_API_KEY = 'sk-or-v1-your_actual_key_here';
   ```

---

### Step 5: Restart Dev Server

1. **Stop current server:**
   ```bash
   Press Ctrl + C in terminal
   ```

2. **Start again:**
   ```bash
   npm run dev
   ```

3. **Server will reload with new API key**

---

## ✅ Verify Setup

### Test 1: Check Console
```
1. Open browser (http://localhost:3000)
2. Open DevTools (F12)
3. Go to Console tab
4. Should NOT see: "⚠️ Demo Mode" warning
```

### Test 2: Send a Message
```
1. Login to your app
2. Go to chat page
3. Select any AI model (e.g., GPT-4 Turbo)
4. Type: "Hello, how are you?"
5. Send message
6. Should get REAL AI response! ✅
```

### Test 3: Check Console Logs
```
You should see:
🤖 Sending request to GPT-4 Turbo...
✅ Response received from GPT-4 Turbo

NOT:
⚠️ OpenRouter API key not configured
```

---

## 🎨 What Happens Now?

### Demo Mode (Before API Key):
```
User sends: "Hello AI!"
Response: "⚠️ Demo Mode Active
           OpenRouter API key not configured...
           [Instructions to add key]"
```

### Real Mode (After API Key):
```
User sends: "Hello AI!"
AI Response: "Hello! I'm here to help. How can I assist you today?"
             [Real AI-generated response]
```

---

## 📊 Available AI Models

### 1. GPT-4 Turbo (OpenAI)
```
Model ID: openai/gpt-4-turbo
Best for: Complex reasoning, coding, creative writing
Cost: ~$0.01 per message
Speed: Medium
```

### 2. Claude 3 Opus (Anthropic)
```
Model ID: anthropic/claude-3-opus
Best for: Long conversations, analysis, safety
Cost: ~$0.015 per message
Speed: Medium-Fast
```

### 3. Gemini Pro (Google)
```
Model ID: google/gemini-pro
Best for: General tasks, fast responses
Cost: ~$0.0005 per message (CHEAPEST!)
Speed: Very Fast
```

### 4. Llama 3 70B (Meta)
```
Model ID: meta-llama/llama-3-70b
Best for: Open-source alternative, general tasks
Cost: ~$0.0007 per message
Speed: Fast
```

### 5. Mistral Large
```
Model ID: mistralai/mistral-large
Best for: European AI, multilingual
Cost: ~$0.008 per message
Speed: Fast
```

### 6. Command R+ (Cohere)
```
Model ID: cohere/command-r-plus
Best for: Enterprise tasks, RAG
Cost: ~$0.003 per message
Speed: Fast
```

---

## 💰 Cost Estimation

### For 100 Messages:
```
GPT-4 Turbo:   100 × $0.01  = $1.00
Claude Opus:   100 × $0.015 = $1.50
Gemini Pro:    100 × $0.0005 = $0.05  ← Cheapest!
Llama 3:       100 × $0.0007 = $0.07
Mistral:       100 × $0.008 = $0.80
Command R+:    100 × $0.003 = $0.30
```

**Recommendation:** Start with Gemini Pro or Llama 3 for testing!

---

## 🔒 Security Best Practices

### DO:
- ✅ Use `.env` file for API keys
- ✅ Add `.env` to `.gitignore`
- ✅ Never commit API keys to git
- ✅ Rotate keys regularly
- ✅ Monitor usage on OpenRouter dashboard

### DON'T:
- ❌ Share API keys publicly
- ❌ Commit `.env` to GitHub
- ❌ Hardcode keys in source code
- ❌ Use same key across multiple projects

---

## 🐛 Troubleshooting

### Issue: "Demo Mode Active" message
**Solution:**
```
1. Check .env file exists in project root
2. Check API key is correct (starts with sk-or-v1-)
3. Restart dev server (Ctrl+C, then npm run dev)
4. Clear browser cache (Ctrl+Shift+R)
```

### Issue: "Invalid API key" error
**Solution:**
```
1. Verify API key on OpenRouter dashboard
2. Make sure key is copied completely
3. Check for extra spaces in .env file
4. Regenerate key if needed
```

### Issue: "Insufficient credits" error
**Solution:**
```
1. Go to https://openrouter.ai/credits
2. Check your balance
3. Add credits if needed ($5-10 recommended)
```

### Issue: "Rate limit exceeded"
**Solution:**
```
1. Wait 1-2 minutes
2. Try again
3. Consider upgrading OpenRouter plan
```

### Issue: No response from AI
**Solution:**
```
1. Check internet connection
2. Check browser console for errors
3. Verify API key is configured
4. Try different AI model
```

---

## 📈 Monitor Usage

### Check Usage Dashboard:
```
1. Go to: https://openrouter.ai/activity
2. See:
   - Total requests
   - Cost per model
   - Credits remaining
   - Error logs
```

---

## 🎯 Quick Start Checklist

Setup complete when:
- [ ] OpenRouter account created
- [ ] API key generated
- [ ] API key added to `.env` file
- [ ] `.env` added to `.gitignore`
- [ ] Dev server restarted
- [ ] Test message sent successfully
- [ ] Real AI response received
- [ ] No "Demo Mode" warning

---

## 🚀 You're All Set!

Your Magverse AI is now connected to 6 powerful AI models!

**Test it:**
1. Open your app
2. Login
3. Go to chat
4. Select any model
5. Start chatting!

**Enjoy the power of multiple AI models in one platform!** 🎉

---

## 📞 Need Help?

- **OpenRouter Docs:** https://openrouter.ai/docs
- **OpenRouter Discord:** https://discord.gg/openrouter
- **API Status:** https://status.openrouter.ai/

---

**Total Setup Time: ~5 minutes**
**Cost to Start: FREE (with free credits)**
**Models Available: 6**

**Happy Chatting!** 🤖✨
