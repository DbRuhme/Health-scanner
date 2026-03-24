# Health Scanner

A mobile-friendly barcode scanner that auto-looks up product nutrition info and saves purchases directly to your Google Sheet. Phase 1 of a personal health & cooking app.

---

## Features

- **Camera barcode scanning** - point at any product, it detects automatically
- **Auto product lookup** - pulls name, brand, calories, protein, carbs & fat from Open Food Facts (free, no API key)
- **One-tap save to Google Sheet** - writes directly to your Purchases tab
- **Manual barcode entry** - type it in if camera isn't available
- **Session history** - recent scans with price and time
- **Saves credentials locally** - set up once, works every time
- **Add to Home Screen** - works like a native app on iPhone & Android

---

## Getting Started

### Step 1 - Host the file

**Option A - Netlify Drop (30 seconds)**
1. Go to netlify.com/drop
2. Drag `barcode_scanner.html` onto the page
3. You get a live URL instantly

**Option B - GitHub Pages (permanent)**
1. Upload `barcode_scanner.html` renamed to `index.html` to this repo
2. Go to Settings > Pages > enable from main branch
3. Your URL: https://dbruhme.github.io/Health-scanner

---

### Step 2 - Get a Google OAuth Token

1. Go to developers.google.com/oauthplayground
2. Find **Google Sheets API v4**, check scope: `https://www.googleapis.com/auth/spreadsheets`
3. Click **Authorize APIs** and sign in with Google
4. Click **Exchange authorization code for tokens**
5. Copy the **Access token**

Note: Tokens expire after ~1 hour. See Long-lived tokens section below.

---

### Step 3 - Connect your Google Sheet

Your sheet needs a tab named **Purchases** with columns:
Date, Store, Item Name, Brand, Barcode, Category, Qty, Unit, Price ($), Calories, Protein (g), Carbs (g), Fat (g), Expiry Date, Notes

Your Sheet ID is in your Google Sheets URL:
https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID_HERE/edit

If you used the Health & Cooking App Master Tracker setup script, this tab is already created.

---

### Step 4 - Open on your phone

1. Open your hosted URL in Chrome or Safari
2. Tap Share > Add to Home Screen
3. It appears as an app icon on your home screen
4. Open it, paste your Sheet ID and OAuth token, tap Connect

---

## How to Use

1. Tap **Start Scanner** - your camera opens
2. Point at a product barcode - phone vibrates on detection
3. Product info fills in automatically (name, brand, nutrition)
4. Add store, price, and quantity
5. Tap **Save to Google Sheet**

---

## What Gets Saved

| Field | Source |
|---|---|
| Date | Auto - today's date |
| Store | You enter |
| Item Name | Open Food Facts |
| Brand | Open Food Facts |
| Barcode | Scanned |
| Category | Auto-guessed |
| Qty | You enter (default 1) |
| Price | You enter |
| Calories | Open Food Facts (per 100g) |
| Protein | Open Food Facts (per 100g) |
| Carbs | Open Food Facts (per 100g) |
| Fat | Open Food Facts (per 100g) |
| Expiry Date | You enter (optional) |

---

## Long-lived Tokens

OAuth Playground tokens expire after ~1 hour. For a permanent setup:
1. Go to console.cloud.google.com
2. Create a project > Enable Google Sheets API
3. Create OAuth 2.0 credentials (Web application type)
4. Add your hosted URL as an authorized origin

A future version will handle token refresh automatically.

---

## Project Roadmap

| Phase | What Gets Built | Status |
|---|---|---|
| Phase 1 | Barcode scanner to Google Sheet | Done |
| Phase 2 | Pantry inventory, expiry tracking, nutrition logs | Next |
| Phase 3 | AI recipe suggestions from pantry (Claude API) | Planned |
| Phase 4 | Spending analytics, health trend dashboards | Planned |

---

## Tech Stack

- Vanilla HTML/CSS/JS - no build step, works anywhere
- QuaggaJS - barcode detection via camera
- Open Food Facts API - free product database, millions of items
- Google Sheets API v4 - direct write to your spreadsheet

---

## License

MIT - use it, fork it, build on it.
