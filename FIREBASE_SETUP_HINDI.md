# Firebase Setup Guide (हिंदी में)

## 🎯 Firebase में क्या Setup करना है?

Magverse AI के लिए आपको Firebase में ये चीज़ें setup करनी होंगी:

---

## 📝 Step 1: Firebase Project बनाएं

1. **Firebase Console खोलें**
   - यहाँ जाएं: https://console.firebase.google.com/
   - "Add Project" या "Create a project" पर click करें

2. **Project Configure करें**
   - Project का नाम दें: `Magverse AI`
   - Google Analytics enable करें (optional)
   - "Create Project" पर click करें

3. **Web App Register करें**
   - Web icon (</>) पर click करें
   - App का nickname: `Magverse AI Web`
   - "Register app" पर click करें

4. **Firebase Config Copy करें**
   - आपको ऐसा config मिलेगा:
   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXX",
     authDomain: "magverse-ai.firebaseapp.com",
     projectId: "magverse-ai",
     // ... बाकी details
   };
   ```
   - **इसे save करें** - बाद में ज़रूरत पड़ेगी!

---

## 🔥 Step 2: Firestore Database Enable करें

1. **Firebase Console में "Firestore Database" में जाएं**
   - "Create database" पर click करें

2. **Production Mode चुनें**
   - "Start in production mode" select करें
   - "Next" पर click करें

3. **Location चुनें**
   - नज़दीकी region चुनें (India के लिए: `asia-south1`)
   - "Enable" पर click करें

---

## 🔐 Step 3: Authentication Enable करें

1. **"Authentication" में जाएं**
   - "Get started" पर click करें

2. **ये Sign-in Methods Enable करें:**

   ### Email/Password
   - "Email/Password" पर click करें
   - Toggle को enable करें
   - "Save" करें

   ### Google Sign-in (Recommended)
   - "Google" पर click करें
   - Toggle को enable करें
   - Support email select करें
   - "Save" करें

   ### Anonymous (Guest के लिए)
   - "Anonymous" पर click करें
   - Toggle को enable करें
   - "Save" करें

---

## 📊 Step 4: Database Structure बनाएं

Firestore में ये collections बनाएं:

### Collection: `users` (Users की जानकारी)
```
users/
  └── {userId}/
      ├── email: string (यूज़र का email)
      ├── name: string (यूज़र का नाम)
      ├── isGuest: boolean (guest है या नहीं)
      ├── isPro: boolean (pro member है या नहीं)
      ├── credits: number (बाकी credits)
      ├── dailyReset: string (daily reset का date)
      ├── createdAt: timestamp
      └── updatedAt: timestamp
```

### Collection: `chats` (Chat History)
```
chats/
  └── {chatId}/
      ├── userId: string (किस user की chat है)
      ├── title: string (chat का title)
      ├── messages: array (सभी messages)
      ├── createdAt: timestamp
      └── updatedAt: timestamp
```

### Collection: `transactions` (Payments)
```
transactions/
  └── {transactionId}/
      ├── userId: string
      ├── type: string (upgrade/credit_purchase)
      ├── amount: number (कितने पैसे)
      ├── plan: string (pro/free)
      ├── status: string (success/pending/failed)
      └── timestamp: timestamp
```

---

## 🔒 Step 5: Security Rules Setup करें

Firestore Console में "Rules" tab में जाएं और ये rules add करें:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    
    // Users collection - सिर्फ खुद का data देख/edit कर सकते हैं
    match /users/{userId} {
      allow read, create, update: if request.auth.uid == userId;
      allow delete: if false; // कोई delete नहीं कर सकता
    }
    
    // Chats collection - सिर्फ अपनी chats देख/edit कर सकते हैं
    match /chats/{chatId} {
      allow read, create, update, delete: if request.auth != null 
        && resource.data.userId == request.auth.uid;
    }
    
    // Transactions - सिर्फ read कर सकते हैं
    match /transactions/{transactionId} {
      allow read: if request.auth != null 
        && resource.data.userId == request.auth.uid;
      allow create, update, delete: if false;
    }
  }
}
```

**"Publish" पर click करके save करें।**

---

## 💻 Step 6: Firebase Install करें

Terminal में ये command run करें:

```bash
npm install firebase
```

---

## ⚙️ Step 7: Configuration File Update करें

1. **File खोलें:** `src/firebase/config.js`

2. **अपना Firebase config paste करें:**
   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY_HERE",  // ← यहाँ अपनी API key डालें
     authDomain: "your-project.firebaseapp.com",
     projectId: "your-project-id",
     storageBucket: "your-project.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:xxxxx"
   };
   ```

3. **File save करें**

---

## ✅ Firebase Setup Checklist

- [ ] Firebase Project बनाया
- [ ] Web App register किया
- [ ] Firestore Database enable किया
- [ ] Authentication enable किया (Email, Google, Anonymous)
- [ ] Security Rules setup किए
- [ ] Firebase SDK install किया (`npm install firebase`)
- [ ] Config file में credentials डाले

---

## 🎉 Firebase में क्या Store होगा?

### User Data
- ✅ Email और नाम
- ✅ Guest/Pro status
- ✅ Credits count
- ✅ Daily reset का time

### Chat Data
- ✅ सभी chat messages
- ✅ AI models की responses
- ✅ Chat history

### Payment Data
- ✅ Pro plan upgrades
- ✅ Payment status
- ✅ Transaction history

---

## 🔄 localStorage vs Firebase

**पहले (localStorage):**
- सिर्फ एक device में data
- Browser clear करने पर data खो जाता था
- दूसरे device में access नहीं

**अब (Firebase):**
- ✅ सभी devices में sync
- ✅ Data safe और secure
- ✅ Real-time updates
- ✅ Automatic backup

---

## 🚀 Setup के बाद क्या करें?

1. ✅ ऊपर के सभी steps complete करें
2. ✅ Firebase config copy करके `src/firebase/config.js` में paste करें
3. ✅ `npm install firebase` command run करें
4. ✅ App को test करें

---

## ❓ मदद चाहिए?

अगर कोई problem आए:
- Firebase Console में errors check करें
- Security rules सही हैं check करें
- Browser console में errors देखें
- Internet connection check करें

---

**Firebase setup complete होने के बाद आपका Magverse AI पूरी तरह ready हो जाएगा!** 🎊
