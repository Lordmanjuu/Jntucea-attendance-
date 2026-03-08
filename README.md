# attend. — JNTUACEA Attendance Portal

A clean, minimalist attendance tracker for JNTUACEA students.
Built on top of classattendance.in — no separate credentials needed.

---

## Files

```
attend-web/
├── app.py            ← Flask backend + API route
├── scraper.py        ← classattendance.in scraper
├── templates/
│   └── index.html    ← Minimalist frontend
├── requirements.txt
└── Procfile          ← For Render deployment
```

---

## Run Locally

```bash
pip install -r requirements.txt
python app.py
# Open http://localhost:5000
```

---

## 🚀 Host FREE on Render.com (Recommended)

### Step 1 — Push code to GitHub
1. Create a free account at github.com
2. Create a new repository (e.g. "jntua-attend")
3. Upload all files (drag & drop on GitHub website works fine)

### Step 2 — Deploy on Render
1. Go to https://render.com → Sign up free with GitHub
2. Click **"New +"** → **"Web Service"**
3. Connect your GitHub repo
4. Fill in settings:
   - **Name:** jntua-attend (anything you like)
   - **Runtime:** Python 3
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn app:app`
   - **Instance Type:** Free
5. Click **"Create Web Service"**
6. Wait ~2 minutes for deploy
7. Your site is live at: `https://jntua-attend.onrender.com`

> ⚠️ Free Render apps sleep after 15 min of inactivity.
> First load after sleep takes ~30 seconds. This is normal on the free tier.

---

## 🌐 Other Free Hosting Options

### Option B — Railway.app
1. railway.app → New Project → Deploy from GitHub
2. Select your repo
3. Add variable: PORT = 5000
4. Deploy — gets a free .railway.app domain

### Option C — Vercel (needs vercel.json)
Add this file as vercel.json:
```json
{
  "builds": [{ "src": "app.py", "use": "@vercel/python" }],
  "routes": [{ "src": "/(.*)", "dest": "app.py" }]
}
```
Then: `npm i -g vercel && vercel --prod`

---

## Notes
- Student credentials are used only to scrape data and are never stored anywhere
- The app talks directly to classattendance.in on behalf of the student
