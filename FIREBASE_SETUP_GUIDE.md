# Firebase Setup Guide for Magverse AI

## 📋 Overview
This guide will help you integrate Firebase into Magverse AI for:
- **Authentication** - User login/signup
- **Firestore Database** - Store user data, chat history, credits
- **Real-time sync** - Sync data across devices

---

## 🚀 Step 1: Create Firebase Project

1. **Go to Firebase Console**
   - Visit: https://console.firebase.google.com/
   - Click "Add Project" or "Create a project"

2. **Configure Project**
   - Project Name: `Magverse AI`
   - Enable Google Analytics (optional)
   - Click "Create Project"

3. **Register Web App**
   - Click on "Web" icon (</>) to add Firebase to web app
   - App nickname: `Magverse AI Web`
   - ✅ Check "Also set up Firebase Hosting" (optional)
   - Click "Register app"

4. **Copy Firebase Config**
   - You'll get a config object like this:
   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXX",
     authDomain: "magverse-ai.firebaseapp.com",
     projectId: "magverse-ai",
     storageBucket: "magverse-ai.appspot.com",
     messagingSenderId: "123456789012",
     appId: "1:123456789012:web:xxxxxxxxxxxxx"
   };
   ```
   - **Save this config** - you'll need it later!

---

## 🔥 Step 2: Enable Firestore Database

1. **In Firebase Console, go to "Firestore Database"**
   - Click "Create database"

2. **Choose Production Mode**
   - Select "Start in production mode"
   - Click "Next"

3. **Choose Location**
   - Select closest region (e.g., `asia-south1` for India)
   - Click "Enable"

4. **Wait for database to be created** (takes ~30 seconds)

---

## 🔐 Step 3: Enable Authentication

1. **Go to "Authentication" in Firebase Console**
   - Click "Get started"

2. **Enable Sign-in Methods:**

   ### Email/Password
   - Click on "Email/Password"
   - Enable the toggle
   - Click "Save"

   ### Google Sign-in (Recommended)
   - Click on "Google"
   - Enable the toggle
   - Select support email
   - Click "Save"

   ### Anonymous (For Guest Mode)
   - Click on "Anonymous"
   - Enable the toggle
   - Click "Save"

---

## 📊 Step 4: Firestore Database Structure

Create these collections in Firestore:

### Collection: `users`
```
users/
  └── {userId}/
      ├── email: string
      ├── name: string
      ├── isGuest: boolean
      ├── isPro: boolean
      ├── credits: number
      ├── dailyReset: string (date)
      ├── createdAt: timestamp
      └── updatedAt: timestamp
```

### Collection: `chats`
```
chats/
  └── {chatId}/
      ├── userId: string
      ├── title: string
      ├── messages: array
      │   └── {
      │       id: string,
      │       role: string (user/assistant),
      │       content: string,
      │       model: string,
      │       timestamp: string
      │   }
      ├── createdAt: timestamp
      └── updatedAt: timestamp
```

### Collection: `transactions`
```
transactions/
  └── {transactionId}/
      ├── userId: string
      ├── type: string (upgrade/credit_purchase)
      ├── amount: number
      ├── plan: string (pro/free)
      ├── status: string (success/pending/failed)
      └── timestamp: timestamp
```

---

## 🔒 Step 5: Security Rules

In Firestore Console, go to "Rules" tab and add these security rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    
    // Helper function to check if user is authenticated
    function isSignedIn() {
      return request.auth != null;
    }
    
    // Helper function to check if user owns the document
    function isOwner(userId) {
      return request.auth.uid == userId;
    }
    
    // Users collection
    match /users/{userId} {
      // Users can read their own data
      allow read: if isSignedIn() && isOwner(userId);
      
      // Users can create their own profile
      allow create: if isSignedIn() && isOwner(userId);
      
      // Users can update their own profile
      allow update: if isSignedIn() && isOwner(userId);
      
      // No one can delete
      allow delete: if false;
    }
    
    // Chats collection
    match /chats/{chatId} {
      // Users can read their own chats
      allow read: if isSignedIn() && resource.data.userId == request.auth.uid;
      
      // Users can create chats
      allow create: if isSignedIn() && request.resource.data.userId == request.auth.uid;
      
      // Users can update their own chats
      allow update: if isSignedIn() && resource.data.userId == request.auth.uid;
      
      // Users can delete their own chats
      allow delete: if isSignedIn() && resource.data.userId == request.auth.uid;
    }
    
    // Transactions collection
    match /transactions/{transactionId} {
      // Users can read their own transactions
      allow read: if isSignedIn() && resource.data.userId == request.auth.uid;
      
      // Only admins can create transactions (in real app, this would be server-side)
      allow create: if false;
      
      // No updates or deletes
      allow update, delete: if false;
    }
  }
}
```

**Click "Publish" to save the rules.**

---

## 💻 Step 6: Install Firebase SDK

In your project terminal, run:

```bash
npm install firebase
```

---

## 📁 Step 7: Create Firebase Configuration Files

These files will be created in the next steps:

1. `src/firebase/config.js` - Firebase initialization
2. `src/firebase/auth.js` - Authentication functions
3. `src/firebase/firestore.js` - Database operations
4. `src/context/FirebaseContext.jsx` - Firebase context provider

---

## 🎯 Data That Will Be Stored

### User Data
- ✅ Email and name
- ✅ Guest/Pro status
- ✅ Credits count
- ✅ Daily reset timestamp
- ✅ Account creation date

### Chat Data
- ✅ Chat messages (user + AI)
- ✅ Selected AI models
- ✅ Timestamps
- ✅ Chat titles

### Transaction Data
- ✅ Pro plan upgrades
- ✅ Payment status
- ✅ Purchase history

---

## 🔄 What Replaces localStorage

**Before (localStorage):**
- `magverse_user`
- `magverse_credits`
- `magverse_isPro`
- `magverse_chatHistory`
- `magverse_dailyReset`

**After (Firebase):**
- All data synced in real-time
- Works across multiple devices
- Secure and backed up
- No data loss on browser clear

---

## ⚙️ Next Steps

After setting up Firebase Console:

1. ✅ Complete Steps 1-5 above
2. ✅ Copy your Firebase config
3. ✅ Install Firebase SDK (`npm install firebase`)
4. ✅ I'll create the integration files for you

---

## 📞 Need Help?

If you encounter issues:
- Check Firebase Console for errors
- Verify your security rules
- Ensure billing is enabled (for production)
- Check browser console for errors

---

**Once you complete these steps, I'll integrate Firebase into your Magverse AI application!** 🚀
