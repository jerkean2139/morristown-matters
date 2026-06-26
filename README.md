# Morristown Matters

The official website for **Morristown Matters** — local news, events, stories,
and the people who make Morristown, Indiana thrive. Includes the home page and
the **Derby Days** event page.

This is a plain static website (HTML, CSS, JavaScript, and images). There is no
build step and no server-side code, so it can be hosted almost anywhere.

```
.
├── index.html          # Home page
├── derby-days.html     # Derby Days event page
├── styles.css          # All site styling
├── script.js           # Mobile menu toggle
├── images/             # Photos, logo, and sponsor logos
├── netlify.toml        # Netlify hosting configuration
├── IMAGE-CREDITS.txt   # Which photos are stock vs. local
└── HOW-TO-PUT-THIS-ONLINE.txt  # Plain-English guide for non-developers
```

---

## Deploying

### Option A — Netlify (recommended)

This repo is already configured for Netlify via `netlify.toml`. Two ways to go
live:

**1. Connect this GitHub repo (continuous deploy — recommended)**

1. Log in at <https://app.netlify.com> and click **Add new site → Import an
   existing project**.
2. Choose **GitHub** and pick the `jerkean2139/morristown-matters` repository.
3. Netlify reads `netlify.toml` automatically:
   - Build command: *(none)*
   - Publish directory: `.` (the repo root)
4. Click **Deploy**. Every push to the connected branch redeploys the site.

**2. Drag-and-drop (no GitHub needed)**

Go to <https://app.netlify.com/drop> and drag the whole project folder onto the
page. See `HOW-TO-PUT-THIS-ONLINE.txt` for a step-by-step, non-technical walk
through (including how to point `morristownderbydays.com` at the new site).

#### Custom domain

In Netlify: **Domain management → Add a domain →** enter your real address and
follow the DNS instructions Netlify provides. HTTPS is provisioned
automatically. Full instructions are in `HOW-TO-PUT-THIS-ONLINE.txt` (Part 5).

#### Newsletter forms (wired to Netlify Forms)

All four newsletter sign-up forms (the bar + footer on both pages) are wired to
**Netlify Forms** — `method="POST"`, `data-netlify="true"`, a hidden
`form-name`, a honeypot field for spam, and a required `email` field. They all
post to a single form named **`newsletter`** and redirect to
`thank-you.html` on success.

This works automatically once the site is deployed to Netlify (Netlify detects
the forms at deploy time — no extra setup). To see submissions: **Netlify
dashboard → your site → Forms → `newsletter`**. You can add email
notifications there (**Forms → Settings → Form notifications**) so each
sign-up is emailed to you.

> Note: form handling only runs on **Netlify**. If the site is hosted somewhere
> else, the forms won't capture submissions.

### Option B — Wix

Wix is a hosted site builder and does **not** host an arbitrary folder of static
HTML the way Netlify does, so this exact codebase can't be "uploaded" to Wix as
files. You have two realistic paths if you want to stay on Wix:

1. **Use Wix only for the domain, host the site on Netlify.** If your domain
   `morristownderbydays.com` was purchased through Wix, keep it there and just
   point its DNS at the Netlify site (Netlify gives you the exact records to
   enter). This is the simplest way to get this design live while keeping Wix.
2. **Rebuild in the Wix Editor.** Recreate these pages using Wix's drag-and-drop
   editor (or embed sections via Wix's *Embed HTML* element). This is manual and
   does not use these files directly.

**Recommendation:** deploy on Netlify (Option A) and, if the domain lives at
Wix, just repoint the domain. You get this exact design live with automatic
HTTPS and free form handling.

---

## Local preview

Because it's static, just open `index.html` in a browser. To preview with a
local server (so relative paths and forms behave like production):

```bash
# Python 3
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Editing later

Edit the `.html`, `.css`, or `.js` files and replace photos in `images/`
(keep the same filenames to swap a photo in place). If connected to Netlify via
GitHub, push your changes and the site redeploys automatically. If using
drag-and-drop, re-drag the folder onto your site's **Deploys** page.
