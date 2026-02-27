# Nexus Partners — Website (Initial Launch Version)

Static HTML site deployable on GitHub + Netlify.

## Folder Structure

```
nexus-partners-launch/
├── index.html              ← All page copy — edit text here
├── css/styles.css          ← Colors, fonts, layout
├── js/main.js              ← Navigation, animations, form
├── images/
│   ├── hero-bg.jpg
│   ├── about.jpg
│   ├── services-business.jpg
│   ├── services-digital.jpg
│   ├── services-org.jpg
│   ├── contact-bg.jpg
│   ├── logo.svg
│   ├── favicon.png
│   └── logos/              ← Full brand kit (LinkedIn, letterhead, etc.)
├── netlify.toml            ← Netlify config (no edits needed)
└── README.md
```

## Launch Version — What Changed

This is the initial launch version of the site. The following are
intentionally excluded pending future activation:

- Work / Case Studies section (removed from page and navigation)
- Case study modals (ADT, Sony, Hallmark)
- "View Our Work" hero CTA button

The full version with all case studies is preserved in `nexus-partners-v3.html`
for future use. To reintroduce case studies, merge from that file.

## Stats (this version)
- $152M Value Created for Clients
- >90% NPS & CSAT Scores

## Editing Copy
Open `index.html`. Each section has a `===` comment banner labeling what to edit.

## Editing Brand Colors
Open `css/styles.css` and edit the `:root` block at the very top.

## Preview & Deployment Workflow

### Step 1 — Enable GitHub Pages (live preview, no DNS needed)
1. Go to **Settings → Pages** in this repository.
2. Under *Source*, choose **GitHub Actions**.
3. Push any commit to `main` — the `Deploy to GitHub Pages` workflow runs automatically.
4. Your preview URL will be:
   `https://<your-github-username>.github.io/<repository-name>/`
   (e.g. `https://myron-nexuspartners.github.io/NP-redesign-2/`)
5. Share that URL to review the live site before touching any DNS records.

### Step 2 — Connect Netlify
1. Log in to [Netlify](https://app.netlify.com) → **Add new site → Import an existing project**.
2. Choose **GitHub** and select this repository (`NP-redesign-2`).
3. Netlify settings (already in `netlify.toml` — no changes needed):
   - **Branch to deploy:** `main`
   - **Publish directory:** `.`
   - **Build command:** *(leave blank)*
4. Click **Deploy site**. Netlify will assign a free `*.netlify.app` preview URL.
5. Verify everything looks correct at the Netlify preview URL before proceeding.

### Step 3 — Activate the Contact Form
Add `name="contact" data-netlify="true"` to the `<form>` tag in `index.html`:
```html
<form id="contactForm" name="contact" data-netlify="true" novalidate>
```
Push the change — Netlify detects the attribute automatically.

### Step 4 — DNS Migration (custom domain)
Only after verifying the Netlify preview:
1. In Netlify: **Domain settings → Add custom domain** → enter your domain.
2. Netlify will show you the DNS records to add (typically an `A` record or `CNAME`).
3. In your DNS registrar/provider, update the records Netlify specifies.
4. Enable **Force HTTPS** in Netlify once DNS propagates (usually < 1 hour).
5. Your old host's DNS can be removed once the Netlify cert is issued and the site is live.

---
