# 🤖 OpenRouter API Setup Guide (हिंदी में)

## ✅ OpenRouter API Integration Complete!

Aapka Magverse AI ab 6 powerful AI models ke saath connect karne ke liye ready hai!

---

## 🎯 OpenRouter Kya Hai?

OpenRouter ek **single API** se multiple AI models tak access deta hai:
- ✅ GPT-4 Turbo (OpenAI) - Sabse powerful
- ✅ Claude 3 Opus (Anthropic) - Long conversations ke liye
- ✅ Gemini Pro (Google) - Fast aur cheap
- ✅ Llama 3 70B (Meta) - Open source
- ✅ Mistral Large - European AI
- ✅ Command R+ (Cohere) - Enterprise level

**Fayde:**
- 💰 Pay-as-you-go (jitna use karo utna pay karo)
- 🚀 6 models, 1 API key
- ⚡ Fast aur reliable
- 📊 Usage tracking
- 🆓 Free credits to start

---

## 📝 Step-by-Step Setup (5 minutes)

### Step 1: OpenRouter Account Banayein

1. **Website kholen:**
   ```
   https://openrouter.ai/
   ```

2. **"Sign In" par click karein** (top right corner)

3. **Signup karein:**
   - Google Account se (recommended)
   - GitHub Account se
   - Ya Email & Password se

4. **Account ban gaya!** ✅

---

### Step 2: API Key Le Lo

1. **Login ke baad, API Keys page par jao:**
   ```
   https://openrouter.ai/keys
   ```

2. **"Create Key" button par click karein**

3. **Name dein:**
   ```
   Name: Magverse AI
   ```

4. **"Create" par click karein**

5. **API key copy kar lein:**
   ```
   Format: sk-or-v1-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

6. **⚠️ IMPORTANT:** Is key ko safe jagah save karein! Dobara nahi dikhegi.

---

### Step 3: Free Credits Le Lein (Optional)

1. **OpenRouter free credits deta hai start karne ke liye**
   - Usually $1-5 free
   - Testing ke liye kaafi hai

2. **Agar aur credits chahiye:**
   - Jao: https://openrouter.ai/credits
   - "Add Credits" par click karein
   - Amount choose karein ($5, $10, $20)
   - Credit card se pay karein

3. **Price per message:**
   ```
   GPT-4 Turbo:    ~₹0.80 per message
   Claude 3 Opus:  ~₹1.25 per message
   Gemini Pro:     ~₹0.04 per message (Sabse sasta!)
   Llama 3:        ~₹0.06 per message
   Mistral Large:  ~₹0.65 per message
   Command R+:     ~₹0.25 per message
   ```

**Recommendation:** Testing ke liye Gemini Pro ya Llama 3 use karein - bahut saste hain!

---

### Step 4: API Key Project Mein Add Karein

#### Tarika 1: .env File Use Karein (Best!)

1. **Project root mein `.env` file banayein:**
   ```
   Magverse AI/
   ├── src/
   ├── public/
   ├── .env  ← Ye file banayein
   └── package.json
   ```

2. **`.env` file khol kar ye likhen:**
   ```env
   VITE_OPENROUTER_API_KEY=sk-or-v1-apni_asli_key_yahan_paste_karein
   ```

3. **`sk-or-v1-apni_asli_key_yahan_paste_karein` ko apni real API key se replace karein**

4. **File save karein** (Ctrl + S)

5. **✅ Done!**

#### Tarika 2: Seedha Code Mein (Testing ke liye)

1. **File kholen:** `src/services/aiService.js`

2. **Line 6 dhundo:**
   ```javascript
   const OPENROUTER_API_KEY = import.meta.env.VITE_OPENROUTER_API_KEY || 'sk-or-v1-YOUR_API_KEY_HERE';
   ```

3. **Replace karein:**
   ```javascript
   const OPENROUTER_API_KEY = 'sk-or-v1-apni_asli_key_yahan';
   ```

⚠️ **Note:** Production mein hamesha .env file use karein, seedha code mein nahi!

---

### Step 5: Dev Server Restart Karein

1. **Terminal mein current server band karein:**
   ```bash
   Ctrl + C dabayein
   ```

2. **Dubara start karein:**
   ```bash
   npm run dev
   ```

3. **Server restart ho gaya! Naye API key ke saath** ✅

---

## ✅ Check Karein Ki Kaam Kar Raha Hai

### Test 1: Console Check Karein
```
1. Browser mein app kholen (http://localhost:3000)
2. F12 dabayein (DevTools khulega)
3. Console tab par jao
4. "⚠️ Demo Mode" warning NAHI dikhna chahiye
```

### Test 2: Message Bhejo
```
1. App mein login karein
2. Chat page par jao
3. Koi bhi AI model select karein (e.g., GPT-4 Turbo)
4. Type karein: "Hello, kaise ho?"
5. Message send karein
6. ASLI AI response aayega! ✅
```

### Test 3: Console Logs Dekho
```
Ye dikhna chahiye:
🤖 Sending request to GPT-4 Turbo...
✅ Response received from GPT-4 Turbo

Ye NAHI dikhna chahiye:
⚠️ OpenRouter API key not configured
```

---

## 🎨 Kya Hoga Ab?

### Demo Mode (API Key se pehle):
```
User: "Hello AI!"
Response: "⚠️ Demo Mode Active
           OpenRouter API key configure nahi hai...
           [Setup instructions]"
```

### Real Mode (API Key ke baad):
```
User: "Hello AI!"
AI: "Hello! Main yahan help karne ke liye hoon. 
     Aap kaise madad chahte hain?"
     [Asli AI ka jawab]
```

---

## 📊 6 AI Models Ki Details

### 1. GPT-4 Turbo (OpenAI) 🔥
```
Best for: Complex problems, coding, creative writing
Price: ~₹0.80 per message
Speed: Medium
Quality: Best ⭐⭐⭐⭐⭐
```

### 2. Claude 3 Opus (Anthropic) 🎯
```
Best for: Long conversations, detailed analysis
Price: ~₹1.25 per message
Speed: Medium-Fast
Quality: Excellent ⭐⭐⭐⭐⭐
```

### 3. Gemini Pro (Google) ⚡
```
Best for: Fast responses, general tasks
Price: ~₹0.04 per message (SABSE SASTA!)
Speed: Bahut Fast
Quality: Good ⭐⭐⭐⭐
```

### 4. Llama 3 70B (Meta) 🦙
```
Best for: Open-source, general tasks
Price: ~₹0.06 per message (Bahut sasta)
Speed: Fast
Quality: Good ⭐⭐⭐⭐
```

### 5. Mistral Large 🇫🇷
```
Best for: Multilingual, European AI
Price: ~₹0.65 per message
Speed: Fast
Quality: Very Good ⭐⭐⭐⭐
```

### 6. Command R+ (Cohere) 💼
```
Best for: Enterprise, business tasks
Price: ~₹0.25 per message
Speed: Fast
Quality: Very Good ⭐⭐⭐⭐
```

---

## 💰 Cost Calculator

### 100 Messages bhejne ka kharcha:
```
GPT-4 Turbo:   100 × ₹0.80  = ₹80
Claude Opus:   100 × ₹1.25  = ₹125
Gemini Pro:    100 × ₹0.04  = ₹4    ← Sabse sasta!
Llama 3:       100 × ₹0.06  = ₹6
Mistral:       100 × ₹0.65  = ₹65
Command R+:    100 × ₹0.25  = ₹25
```

**Advice:** Testing ke liye **Gemini Pro** ya **Llama 3** use karein!

---

## 🐛 Problems & Solutions

### Problem: "Demo Mode Active" dikhayi de raha hai
**Solution:**
```
1. Check karein .env file project root mein hai
2. API key sahi hai (sk-or-v1- se shuru hoti hai)
3. Dev server restart karein (Ctrl+C, phir npm run dev)
4. Browser refresh karein (Ctrl+Shift+R)
```

### Problem: "Invalid API key" error
**Solution:**
```
1. OpenRouter dashboard par jao aur key verify karein
2. Puri key copy hui hai check karein
3. .env mein extra spaces nahi hone chahiye
4. Zarurat ho to nayi key generate karein
```

### Problem: "Insufficient credits" error
**Solution:**
```
1. https://openrouter.ai/credits par jao
2. Balance check karein
3. Credits add karein ($5-10 kaafi hai)
```

### Problem: AI se response nahi aa raha
**Solution:**
```
1. Internet connection check karein
2. Browser console mein errors dekho (F12)
3. API key configured hai confirm karein
4. Dusra AI model try karein
```

---

## 📈 Usage Monitor Kaise Karein

### Dashboard par jao:
```
1. Visit: https://openrouter.ai/activity
2. Dekho:
   - Total requests kitne hue
   - Har model ka cost
   - Kitne credits bache
   - Error logs
```

---

## 🎯 Quick Checklist

Setup complete hai agar:
- [ ] OpenRouter account ban gaya
- [ ] API key generate ho gayi
- [ ] API key `.env` file mein add ho gayi
- [ ] Dev server restart hua
- [ ] Test message bheja
- [ ] Real AI response aaya
- [ ] "Demo Mode" warning nahi aa rahi

---

## 🚀 All Set! Ab Kya Karein?

**Test karein:**
```
1. App kholen
2. Login karein
3. Chat page par jao
4. Koi model select karein
5. Message type karein
6. Real AI response dekho!
```

---

## 💡 Pro Tips

### Paise Bachane Ke Liye:
```
✅ Gemini Pro use karein (sabse sasta)
✅ Short messages bhejo
✅ Unnecessary chats avoid karein
✅ Usage dashboard regularly check karein
```

### Best Results Ke Liye:
```
✅ GPT-4 for complex tasks
✅ Claude for long conversations
✅ Gemini for quick answers
✅ Clear instructions dein AI ko
```

---

## 📁 Important Files

```
.env                        ← API key yahan
src/services/aiService.js   ← AI logic yahan
OPENROUTER_SETUP_GUIDE.md   ← English guide
OPENROUTER_SETUP_HINDI.md   ← Ye file
```

---

## 🎊 Summary

**Kya Hua:**
- ✅ AI service updated
- ✅ 6 models ready
- ✅ Environment variables support
- ✅ Better error handling
- ✅ Demo mode for testing

**Aapko Kya Karna Hai:**
1. OpenRouter par account banao (2 min)
2. API key copy karo (1 min)
3. `.env` file mein paste karo (1 min)
4. Server restart karo (1 min)
5. Test karo! (1 min)

**Total Time: 5 minutes**
**Cost: FREE (with free credits)**

---

## 📞 Help Chahiye?

- **OpenRouter Docs:** https://openrouter.ai/docs
- **Discord:** https://discord.gg/openrouter
- **Status:** https://status.openrouter.ai/

---

**Ab aapke AI models response denge! Enjoy!** 🤖🎉
