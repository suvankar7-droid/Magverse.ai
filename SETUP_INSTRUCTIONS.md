# 🚀 Magverse AI - Setup Instructions

## Quick Start Guide

### Step 1: Install Dependencies

Open your terminal in this folder and run:

```bash
npm install
```

**If you encounter PowerShell execution policy errors**, run this first:
```bash
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Or use Command Prompt instead of PowerShell.

### Step 2: Configure OpenRouter API Key

1. Get your free API key from [OpenRouter](https://openrouter.ai/keys)
2. Open the file: `src/services/aiService.js`
3. Find this line:
   ```javascript
   const OPENROUTER_API_KEY = 'sk-or-v1-YOUR_API_KEY_HERE';
   ```
4. Replace `'sk-or-v1-YOUR_API_KEY_HERE'` with your actual API key

### Step 3: Start the Development Server

```bash
npm run dev
```

The app will open at `http://localhost:3000`

### Step 4: Test the Application

1. Click "Login" and enter your name and email
2. You'll get 5 free credits
3. Select AI models from the sidebar
4. Start chatting!

## ⚠️ Important Notes

- The app runs in **demo mode** without an API key (simulated responses)
- To get **real AI responses**, you must add your OpenRouter API key
- Free plan: 5 chats/day
- Pro plan: Demo payment (no real charges)

## 🎨 Features to Test

✅ Login/Logout
✅ Free plan credits (5 per day)
✅ Chat with multiple AI models
✅ Model selection in sidebar
✅ Chat history
✅ Upgrade to Pro (demo)
✅ Credit limit warning
✅ Responsive design (try mobile view)

## Need Help?

Check the main `README.md` for detailed documentation.

---

**Happy Coding! 🎉**
