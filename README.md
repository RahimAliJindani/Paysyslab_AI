# PaysysLabs AI Tools — Website

Live marketing and demo site for PaysysLabs AI Work Tools (ANZ market).  
Five static HTML pages, zero build tools, deployable to Vercel in under 5 minutes.

---

## Pages

| File | URL (after deploy) | Purpose |
|---|---|---|
| `paysyslabs-ai.html` | `/` | Main landing page — hero, all tools overview, capabilities tabs, testimonials, book a demo form |
| `talk2data-page.html` | `/talk2data` | Talk2Data product page — plain-English database queries |
| `expert-report-page.html` | `/expert-report` | Expert Report Writing product page — document-to-report automation |
| `mailbox-agent-page.html` | `/mailbox-agent` | Email Action Agent product page — M365 inbox → Slack digest |
| `calendar-agent-page.html` | `/calendar-agent` | Calendar Assistant product page — WhatsApp → Outlook booking |

---

## File Structure

```
/
├── paysyslabs-ai.html          ← Main landing page (entry point)
├── talk2data-page.html         ← Talk2Data product page
├── expert-report-page.html     ← Expert Report Writing product page
├── mailbox-agent-page.html     ← Email Action Agent product page
├── calendar-agent-page.html    ← Calendar Assistant product page
├── vercel.json                 ← Vercel routing (maps / to main page + clean URLs)
├── README.md                   ← This file
│
├── Paysys_Logo_White.png       ← Nav logo (required — add manually)
├── Talk to Data.mp4            ← Demo video (required — add manually)
├── Expert Report Writing.mp4   ← Demo video (required — add manually)
├── Email actions.mp4           ← Demo video (required — add manually)
└── Calendar Agent.mp4          ← Demo video (required — add manually)
```

> **Note:** The four MP4 files and the PNG logo are NOT included in the GitHub repo (too large / binary assets). Upload them separately via GitHub's web UI or store them on a CDN. See deployment steps below.

---

## Link Architecture

```
paysyslabs-ai.html  (main landing page)
│
├── Demo Cards section
│   ├── → talk2data-page.html
│   ├── → calendar-agent-page.html
│   ├── → mailbox-agent-page.html
│   └── → expert-report-page.html
│
└── Capabilities Tabs (inline panel swap — no page load)
    ├── Talk2Data tab     → #talk2data panel
    ├── Expert Reports tab → #report-writer panel
    ├── Email Agent tab   → #mailbox panel
    └── Calendar Agent tab → #calendar panel

Each product page
├── ← All tools  →  paysyslabs-ai.html#demos
├── Watch demo   →  #demo-video (in-page scroll)
└── Book a demo  →  #book-demo / #gateSection / #pocForm (in-page scroll)
```

---

## External Dependencies (CDN — no install needed)

| Resource | Used for |
|---|---|
| Google Fonts — DM Sans + DM Serif Display | Typography across all pages |
| Tabler Icons v3.19 (jsDelivr CDN) | All icons across all pages |
| Formspree `xbdejwbg` | Book a demo form submissions |
| Google Analytics `G-XXXXXXXXXX` | Replace with your GA4 ID |
| LinkedIn Insight Tag `XXXXXXX` | Replace with your LinkedIn Partner ID |

---

## Deployment

See the [Deployment Guide](#deployment-guide) section below for full step-by-step instructions.

Quick version:
1. Push this repo to GitHub
2. Import to Vercel → Framework: Other → Deploy
3. Live in ~30 seconds at `your-project.vercel.app`

---

## Updating Pages

Edit any `.html` file → commit to GitHub → Vercel redeploys automatically in ~30 seconds.

No build step. No CLI. No framework. Just HTML.

---

## Deployment Guide

### Prerequisites
- GitHub account — [github.com](https://github.com)
- Vercel account — [vercel.com](https://vercel.com) (sign up with GitHub)

---

### Step 1 — Create the GitHub Repository

1. Go to [github.com](https://github.com)
2. Click **+** (top right) → **New repository**
3. Fill in:
   - **Repository name:** `paysyslabs-ai-website`
   - **Visibility:** Private
   - **Initialize:** leave all checkboxes unchecked
4. Click **Create repository**

You now have an empty repo.

---

### Step 2 — Upload the HTML Files and vercel.json

1. On your new repo page, click **uploading an existing file**
2. Drag and drop these files from your computer:
   - `paysyslabs-ai.html`
   - `talk2data-page.html`
   - `expert-report-page.html`
   - `mailbox-agent-page.html`
   - `calendar-agent-page.html`
   - `vercel.json`
   - `README.md`
3. In the **Commit changes** box at the bottom, type: `Initial upload — HTML pages and Vercel config`
4. Click **Commit changes**

Wait for the upload progress bar to complete.

---

### Step 3 — Upload the Logo

1. On your repo page, click **Add file** → **Upload files**
2. Drag and drop: `Paysys_Logo_White.png`
3. Commit message: `Add logo`
4. Click **Commit changes**

---

### Step 4 — Upload the Video Files

> GitHub has a 25MB file size limit on web uploads. If your MP4 files are under 25MB each, upload them here. If they are larger, see the **Large Videos** note below.

1. Click **Add file** → **Upload files**
2. Drag and drop all four MP4 files:
   - `Talk to Data.mp4`
   - `Expert Report Writing.mp4`
   - `Email actions.mp4`
   - `Calendar Agent.mp4`
3. Commit message: `Add demo videos`
4. Click **Commit changes**

> **Large Videos (over 25MB):** GitHub's web uploader blocks files over 25MB. Options:
> - Use [Git LFS](https://git-lfs.com) via the GitHub Desktop app or terminal
> - Host videos on Cloudflare R2, AWS S3, or Bunny CDN and update the `src` in each HTML file to point to those URLs instead

---

### Step 5 — Deploy on Vercel

1. Go to [vercel.com](https://vercel.com) → click **Add New Project**
2. Under **Import Git Repository**, click **Connect to GitHub** if not already connected
3. Find `paysyslabs-ai-website` in the list → click **Import**
4. On the **Configure Project** screen:
   - **Framework Preset:** Other
   - **Root Directory:** leave as `/`
   - **Build Command:** leave blank
   - **Output Directory:** leave blank
5. Click **Deploy**

Vercel deploys in about 30 seconds and gives you a URL like:
`https://paysyslabs-ai-website.vercel.app`

The `vercel.json` file automatically makes `/` open your main landing page.

---

### Step 6 — Test Every Page

Open your Vercel URL and check each of these:

| Test | Expected result |
|---|---|
| Visit `/` | Main landing page loads |
| Click "Talk2Data" demo card | Goes to Talk2Data page |
| Click "Expert Report Writing" demo card | Goes to Expert Report page |
| Click "Email Action Agent" demo card | Goes to Email Agent page |
| Click "Calendar Assistant" demo card | Goes to Calendar page |
| Click `← All tools` on any product page | Returns to main page, scrolled to demo section |
| Click capability tabs on main page | Panel switches without page reload |
| Click "Watch the demo" on any product page | Scrolls to video section |
| Click "Book a demo" on any product page | Scrolls to form section |
| Submit the demo form | Formspree handles submission |
| Logo appears in nav | PNG loaded correctly |
| Videos play | MP4 files loaded correctly |

---

### Step 7 — Add a Custom Domain (Optional)

1. In Vercel → your project → **Settings** → **Domains**
2. Type your domain e.g. `ai.paysyslabs.com` → click **Add**
3. Vercel shows a DNS record:
   - **Type:** CNAME
   - **Name:** `ai`
   - **Value:** `cname.vercel-dns.com`
4. Add this record in your DNS provider (Cloudflare, GoDaddy, Route53, etc.)
5. Wait 5–30 minutes for DNS to propagate
6. Vercel automatically provisions an SSL certificate

---

### Updating After Deploy

Every time you edit a file:

1. Go to your GitHub repo
2. Click the file you want to edit
3. Click the **pencil icon** (Edit this file)
4. Make your changes
5. Click **Commit changes**

Vercel detects the commit and redeploys automatically — live within ~30 seconds.

---

## Analytics Setup

Replace the placeholder IDs in each HTML file before deploying:

**Google Analytics:**
Find `G-XXXXXXXXXX` in every HTML file and replace with your GA4 Measurement ID.
(Settings → Data Streams → your stream → Measurement ID in GA4)

**LinkedIn Insight Tag:**
Find `XXXXXXX` in every HTML file and replace with your LinkedIn Partner ID.
(LinkedIn Campaign Manager → Account Assets → Insight Tag)

---

## Form Submissions

All "Book a Demo" forms submit to Formspree endpoint `xbdejwbg`.  
Submissions go to the email address registered on that Formspree account.  
No backend or server required.

---

## Support

**Email:** ai@paysyslabs.com  
**Website:** [paysyslabs.com](https://paysyslabs.com)
