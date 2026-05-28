# 🇳🇵 Nepal Ko Crorepati

> **"Ko Banchha Crorepati?"** — A Nepali KBC-style quiz game with Solo & Multiplayer modes.

[![Live Demo](https://img.shields.io/badge/Play%20Now-GitHub%20Pages-gold?style=for-the-badge)](https://YOUR_USERNAME.github.io/nepal-ko-crorepati/)

---

## 📸 Features

- **100+ Questions** across 4 categories: 🧠 General Knowledge, 🎬 Nepali Movies, ⚽ Sports, 🏛️ Politics & Current Affairs
- **Solo Mode** — Classic KBC-style prize ladder up to Rs. 1 Crore
- **Multiplayer Mode** — Real-time rooms via Firebase (up to 10 players)
- **3 Lifelines** — 50:50, Phone a Friend, Audience Poll
- **Category & Difficulty Selection** — Play what you love
- **Beautiful UI** — Dark theme, gold accents, fully responsive

---

## 🚀 Deploying to GitHub Pages (Solo Mode — No Setup Needed)

Solo mode works **instantly** with no backend needed.

### Step 1 — Fork or Upload to GitHub

1. Go to [github.com](https://github.com) → **New Repository**
2. Name it `nepal-ko-crorepati` (or anything you like)
3. Upload `index.html` to the repo

### Step 2 — Enable GitHub Pages

1. In your repo → **Settings** → **Pages**
2. Under **Source**, select `Deploy from a branch`
3. Choose branch: `main`, folder: `/ (root)` → Click **Save**
4. Wait ~1 minute, then your game is live at:
   ```
   https://YOUR_USERNAME.github.io/nepal-ko-crorepati/
   ```

---

## 🔥 Setting Up Multiplayer (Firebase)

Multiplayer requires a **free Firebase Realtime Database**.

### Step 1 — Create a Firebase Project

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Click **Add project** → Name it (e.g., `nepal-crorepati`) → Continue
3. Disable Google Analytics (optional) → **Create project**

### Step 2 — Enable Realtime Database

1. In your Firebase project → **Build** → **Realtime Database**
2. Click **Create Database**
3. Choose a region (e.g., `asia-southeast1` for Nepal/Asia)
4. Start in **Test Mode** (for development) → **Enable**

### Step 3 — Set Database Rules (important!)

In the Realtime Database console → **Rules** tab, paste:

```json
{
  "rules": {
    "rooms": {
      "$roomId": {
        ".read": true,
        ".write": true
      }
    }
  }
}
```

Click **Publish**.

> ⚠️ For production, add authentication and stricter rules. The above is fine for personal/friend use.

### Step 4 — Get Your Firebase Config

1. In Firebase → **Project Settings** (⚙️ icon) → **Your apps**
2. Click **Add app** → **Web** (`</>`)
3. Register app → Copy the `firebaseConfig` object

### Step 5 — Paste Config in index.html

Open `index.html` and find this section near the top of the `<script>` block:

```javascript
const FIREBASE_CONFIG = {
  apiKey:            "YOUR_API_KEY",
  authDomain:        "YOUR_PROJECT.firebaseapp.com",
  databaseURL:       "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
  projectId:         "YOUR_PROJECT_ID",
  storageBucket:     "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId:             "YOUR_APP_ID"
};
```

Replace each `"YOUR_..."` value with your actual Firebase config values.

### Step 6 — Push & Play

Commit and push the updated `index.html` to GitHub. Your multiplayer is now live!

---

## 🎮 How to Play

| Mode | Description |
|------|-------------|
| **Solo** | Answer 15 questions, climb the prize ladder. Safe havens at Q5 (Rs. 10,000) and Q11 (Rs. 6,40,000). |
| **Multiplayer** | Host creates a room, shares the 6-digit code. All players answer simultaneously. Faster correct answers = more points. |

### Lifelines (Solo Only)
| Lifeline | What it does |
|----------|-------------|
| **50:50** | Removes 2 wrong answers |
| **Phone a Friend** | Get a (simulated) hint from a friend |
| **Audience Poll** | See how the audience would vote |

---

## 📁 File Structure

```
nepal-ko-crorepati/
└── index.html      ← The entire game (single file, no dependencies)
```

That's it — the whole game is one HTML file!

---

## 🛠️ Tech Stack

- Vanilla HTML/CSS/JavaScript (no frameworks)
- [Firebase Realtime Database](https://firebase.google.com/) for multiplayer
- [Google Fonts](https://fonts.google.com/) (Cinzel Decorative, Rajdhani)

---

## 📝 Adding Your Own Questions

In `index.html`, find the `const POOL = [...]` array. Add questions in this format:

```javascript
{
  cat: 'general',   // 'general' | 'movies' | 'sports' | 'politics'
  d: 2,             // difficulty: 1=Easy, 2=Medium, 3=Hard
  q: "Your question here?",
  opts: ["Option A", "Option B", "Option C", "Option D"],
  a: 1              // index of the correct answer (0-3)
},
```

---

## 🤝 Contributing

Pull requests welcome! Especially for:
- More questions (especially recent events)
- New categories (Music 🎵, History 📜, Food 🍛)
- Bug fixes

---

## ⚖️ License

MIT License — free to use, modify, and share.

---

Made with ❤️ for Nepal 🇳🇵
