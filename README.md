# 💜 Vishnu Priya's Expense Tracker

A personal expense tracker with a BTS-themed UI — built with vanilla HTML/CSS/JS and Firebase Firestore for real-time cloud storage. Hosted on Vercel.

---

## 🗂 Project Structure

```
vp-tracker/
├── index.html          ← Full app (HTML + CSS + JS in one file)
├── firestore.rules     ← Firebase security rules
├── vercel.json         ← Vercel deployment config
├── .gitignore
└── README.md
```

---

## 🚀 Step-by-Step Setup

### STEP 1 — Create a Firebase Project

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"** → give it a name (e.g. `vp-tracker`) → Continue
3. Disable Google Analytics if you don't need it → **Create project**

### STEP 2 — Enable Firestore

1. In Firebase Console → left sidebar → **Firestore Database**
2. Click **"Create database"**
3. Choose **"Start in test mode"** (you can secure it later)
4. Select your region (e.g. `asia-south1` for India) → **Enable**

### STEP 3 — Register a Web App & Get Config

1. In Firebase Console → Project Overview → click the **`</>`** (Web) icon
2. Give it a nickname (e.g. `vp-tracker-web`) → **Register app**
3. You'll see a config block like this — **copy all the values**:

```js
const firebaseConfig = {
  apiKey:            "AIza...",
  authDomain:        "your-project.firebaseapp.com",
  projectId:         "your-project",
  storageBucket:     "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId:             "1:123:web:abc123"
};
```

### STEP 4 — Paste Config into index.html

Open `index.html` and find this section near the bottom (inside the `<script type="module">`):

```js
const firebaseConfig = {
  apiKey:            window._ENV_FIREBASE_API_KEY            || "REPLACE_WITH_YOUR_API_KEY",
  authDomain:        window._ENV_FIREBASE_AUTH_DOMAIN        || "REPLACE_WITH_YOUR_AUTH_DOMAIN",
  ...
```

Replace each `"REPLACE_WITH_YOUR_..."` string with your actual Firebase values.

> ✅ That's it for Firebase! The app will now save all data to the cloud.

---

### STEP 5 — Push to GitHub

```bash
# 1. Create a new repo on github.com first (name it: vp-tracker)

# 2. In your terminal, inside the project folder:
git init
git add .
git commit -m "💜 Initial commit - VP Expense Tracker"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/vp-tracker.git
git push -u origin main
```

---

### STEP 6 — Deploy on Vercel

1. Go to [https://vercel.com](https://vercel.com) → Sign in with GitHub
2. Click **"Add New Project"**
3. Import your `vp-tracker` repository
4. Vercel auto-detects the `vercel.json` — just click **"Deploy"**
5. Done! Your app is live at `https://vp-tracker.vercel.app` (or similar)

> 🔄 Every time you push to `main`, Vercel auto-deploys the latest version.

---

## 🔒 Security (Important!)

The `firestore.rules` file currently allows all reads and writes (test mode).

Once the app is only for Vishnu Priya, you should:
1. Add **Firebase Authentication** (Google Sign-In is easiest)
2. Update `firestore.rules` to only allow authenticated users:

```
allow read, write: if request.auth != null;
```

To deploy the rules:
```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login and deploy rules
firebase login
firebase init firestore   # select your project
firebase deploy --only firestore:rules
```

---

## ✨ Features

- 💜 BTS-themed splash screen with floating emoji animation
- 🏦 Multiple accounts (Bank, UPI, Cash, etc.)
- 💚 Income & 🔴 Expense tracking
- 👤 Sender & Receiver tracking per transaction
- 📂 Categories (Music & Merch, Food, BTS Fund, etc.)
- 🔴 Real-time sync via Firebase Firestore
- 🟢 Sync status indicator in header
- 📱 Fully responsive (mobile-friendly)

---

## 🛠 Tech Stack

| Layer    | Tech                        |
|----------|-----------------------------|
| Frontend | HTML + CSS + Vanilla JS     |
| Database | Firebase Firestore          |
| Hosting  | Vercel                      |
| Repo     | GitHub                      |

---

Made with 💜 for Vishnu Priya
