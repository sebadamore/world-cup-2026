# ⚽ FIFA World Cup 2026 — Match Scheduler

A fully client-side web app to browse all **104 official FIFA World Cup 2026 fixtures** and add them directly to your Google Calendar using the official **Google Calendar JavaScript API (GAPI + GIS)**.

![World Cup 2026 Match Scheduler](./preview.png)

---

## ✨ Features

- **📅 All 104 Matches** — Group Stage (Groups A–L), Round of 32, Round of 16, Quarterfinals, Semifinals, Third Place, and Final
- **🔗 Google Calendar API** — Direct OAuth2 integration using GAPI + Google Identity Services (GIS) — the official Google JS quickstart pattern
- **👥 Public Calendar Subscribe** — Share one public calendar with friends via the in-app Subscribe button (no OAuth required for them)
- **🔓 3 Calendar Options** — Via API (direct insert), browser link (no auth needed), or `.ics` download
- **💾 Save & Batch Add** — Save multiple matches, then batch-add all to Google Calendar at once
- **📁 .ics Export** — Download single or all saved matches for Apple Calendar / Outlook
- **🔍 Filter & Search** — By stage, group (A–L), team name, venue, or city
- **🌙 Dark/Light Mode** — Respects system preference, manual toggle
- **📱 Fully Responsive** — Works on mobile and desktop
- **📋 API Log** — Step-by-step log of every GAPI / GIS / OAuth call

---

## 🚀 Quick Start

### Option 1: Open directly in browser
```bash
# No build tools needed — just open the file
open "World_Cup_2026_App.html"
```
> ⚠️ For Google Calendar API OAuth2 to work, you must serve from a local HTTP server (not `file://`).

### Option 2: Serve locally (recommended)
```bash
npx http-server . -p 8080 --cors
# Then open: http://localhost:8080/
```

### Option 3: Deploy to GitHub Pages
Push to a repo → Settings → Pages → Deploy from branch `main` → root `/`.

---

## 🔧 Google Calendar API Setup (Step-by-Step)

The app walks you through this in-app, but here's the full guide:

### Step 1 — Create a Google Cloud Project
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Click **New Project** → give it a name

### Step 2 — Enable Google Calendar API
1. Go to **APIs & Services** → **Library**
2. Search for `Google Calendar API` → **Enable**

### Step 3 — Configure OAuth Consent Screen
1. **APIs & Services** → **OAuth consent screen**
2. Set **User Type** to `External` (or `Internal` for personal use)
3. Fill in App Name, support email
4. Add scope: `https://www.googleapis.com/auth/calendar`

### Step 4 — Create OAuth 2.0 Client ID
1. **APIs & Services** → **Credentials** → **Create Credentials** → **OAuth Client ID**
2. Application type: **Web application**
3. Under **Authorized JavaScript Origins**, add:
   - `http://localhost:8080` (for local dev)
   - Your production domain (for deployment)
4. Click **Create** → Copy the **Client ID**

### Step 5 — Create an API Key
1. **Credentials** → **Create Credentials** → **API Key**
2. (Optional) Restrict to **Google Calendar API**
3. Copy the **API Key**

### Step 6 — Enter credentials in the app
Paste the Client ID and API Key into the setup card at the top of the app, then click **Load & Authorize**.

---

## 🔒 How Auth Works

This app uses the **official Google Calendar API JavaScript Quickstart** pattern:

```
GAPI (apis.google.com/js/api.js)          → Loads the Calendar client + discovery doc
GIS  (accounts.google.com/gsi/client)     → OAuth2 token request via popup
tokenClient.requestAccessToken()           → Triggers Google account picker
gapi.client.calendar.events.insert()      → Creates event in user's primary calendar
```

**No credentials are ever stored or transmitted** — everything stays in your browser session.

---

## 📦 Tech Stack

| Tech | Purpose |
|------|---------|
| Plain HTML/CSS/JS | Zero dependencies, zero build step |
| [Google GAPI](https://developers.google.com/api-client-library/javascript) | Calendar API client |
| [Google Identity Services](https://developers.google.com/identity/oauth2/web) | OAuth2 token flow |
| [Lucide Icons](https://lucide.dev) | UI icons (CDN) |
| [Inter Font](https://fonts.google.com/specimen/Inter) | UI typography |
| [Bebas Neue](https://fonts.google.com/specimen/Bebas+Neue) | Display headings |

---

## 📅 Tournament Data

| Stage | Matches | Dates |
|-------|---------|-------|
| Group Stage (A–L) | 72 | June 11–27, 2026 |
| Round of 32 | 16 | June 28–July 3, 2026 |
| Round of 16 | 8 | July 4–7, 2026 |
| Quarterfinals | 4 | July 9–11, 2026 |
| Semifinals | 2 | July 14–15, 2026 |
| Third Place | 1 | July 18, 2026 |
| **Final** | **1** | **July 19, 2026** |
| **Total** | **104** | |

Hosts: 🇺🇸 USA · 🇨🇦 Canada · 🇲🇽 Mexico  
All times shown in Eastern Time (ET).

---

## 📂 Project Structure

```
world-cup-2026/
├── index.html                    # Vercel/GitHub Pages entrypoint
├── World_Cup_2026_App.html       # Main app (single-file)
└── World Cup Games App README.md
```

---

## 🌐 Deploy

### Share a public calendar with friends
Set a public calendar ID in `World_Cup_2026_App.html`:

```js
const OFFICIAL_CALENDAR_ID = 'your_calendar_id@group.calendar.google.com';
```

Or pass it via URL (no code changes required):

```text
https://world-cup-2026-one.vercel.app/?cal=your_calendar_id@group.calendar.google.com
```

The top-bar **Subscribe** button will open Google Calendar and let users subscribe to that public calendar.

### GitHub Pages
```bash
git init
git add .
git commit -m "feat: initial World Cup 2026 match scheduler"
git remote add origin https://github.com/YOUR_USERNAME/world-cup-2026.git
git push -u origin main
```
Then: **Settings** → **Pages** → Source: `main` branch, root `/`

Remember to add your GitHub Pages URL (e.g. `https://username.github.io`) to **Authorized JavaScript Origins** in Google Cloud Console.

---

## 📝 License

MIT — free to use, modify, and distribute.
