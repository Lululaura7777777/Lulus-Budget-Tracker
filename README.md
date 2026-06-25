# Budget Tracker

A simple personal budget tracker that saves your data to Google Drive. Track monthly spending by category, view progress bars, and export your history to CSV.

**Features**
- Monthly budget by category with progress bars
- Transaction log with optional notes
- Editable category names and budget amounts
- Export all history to CSV
- Data saved automatically to your Google Drive

---

## Setup

### Step 1 — Download the file

Download `index.html` from this repository.

### Step 2 — Create a Google Cloud project

1. Go to [console.cloud.google.com](https://console.cloud.google.com) and sign in with your Google account
2. Click "Select a project" at the top → "New Project"
3. Give it any name (e.g. `Budget Tracker`) and click "Create"

### Step 3 — Enable the Google Drive API

1. In the left menu go to "APIs & Services" → "Library"
2. Search for "Google Drive API"
3. Click it → click "Enable"

### Step 4 — Get your API Key

1. Go to "APIs & Services" → "Credentials"
2. Click "+ Create Credentials" → "API Key"
3. Copy the key and save it somewhere

### Step 5 — Get your Client ID

1. On the same page click "+ Create Credentials" → "OAuth 2.0 Client ID"
2. If prompted to configure the OAuth consent screen first:
   - User Type: select "External"
   - App name: anything (e.g. `Budget Tracker`)
   - Support email: your email
   - Developer contact email: your email
   - Click "Save and Continue" through all steps
3. Back on Credentials, click "+ Create Credentials" → "OAuth 2.0 Client ID"
4. Application type: "Web application"
5. Under "Authorized JavaScript origins" click "Add URI" and enter `http://localhost`
6. Click "Create" and copy your Client ID

### Step 6 — Add your credentials to the file

Open `index.html` in any text editor and find these two lines near the top of the `<script>` section:

```js
const CLIENT_ID = 'YOUR_CLIENT_ID_HERE';
const API_KEY = 'YOUR_API_KEY_HERE';
```

Replace `YOUR_CLIENT_ID_HERE` with your Client ID and `YOUR_API_KEY_HERE` with your API Key. Save the file.

### Step 7 — Run the app

The file needs to be served locally (not just double-clicked) for Google sign-in to work. The easiest way is with VS Code:

1. Install [VS Code](https://code.visualstudio.com) if you don't have it
2. Install the **Live Server** extension (search in the Extensions panel)
3. Open `index.html` in VS Code
4. Click "Go Live" in the bottom right corner
5. Your browser will open the app at `http://127.0.0.1:5500`

If you see an "origin mismatch" error when signing in, go back to your OAuth Client ID in Google Cloud Console and add the exact URL shown in your browser (e.g. `http://127.0.0.1:5500`) to "Authorized JavaScript origins", then try again.

---

## Usage

- Click **+ Add expense** to log a new transaction — enter the amount, pick a category, and optionally add a note
- Use the **arrow buttons** to navigate between months
- Click **⚙ Budget settings** to customize category names and monthly budget amounts (defaults are reset-able)
- Click **↓ Export CSV** to download all your transaction history as a spreadsheet

Your data is saved automatically to a hidden app folder in your Google Drive after every change. It is private and only accessible by this app.

---

## Notes

- Data is tied to your Google account — signing in on a different device with the same account will load the same data
- Each person who uses this app needs their own Google Cloud credentials (Client ID + API Key) — do not share yours
- The app uses Google Drive's `appDataFolder` scope, which means it can only access files it creates itself, not the rest of your Drive
