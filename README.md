# Static Website Starter (Beginner-Friendly)

This is a simple, production-ready static site (HTML + CSS) designed to deploy on **Cloudflare Pages** and point to your **Namecheap** domain.

## 1) Edit content
- Open `index.html` and replace:
  - `YourStartup`, the headline, subtext, and email (`hello@yourdomain.com`).
- Optional: tweak styles in `styles.css`.

## 2) Put it on GitHub (no terminal required)
1. Go to https://github.com/new → create a repo (public or private).
2. Click **"uploading an existing file"** and drag the files from this folder.
3. Commit the changes.

## 3) Deploy on Cloudflare Pages
1. Cloudflare dashboard → **Workers & Pages** → **Create project** → **Connect to Git**.
2. Select your repo.
3. Build settings:
   - Framework preset: **None**
   - Build command: leave **empty**
   - Output directory: **/** (root)

Cloudflare will assign a `*.pages.dev` preview domain. Your site is live.

## 4) Attach your Namecheap domain
If you want `www.yourdomain.com` as the main site (recommended when keeping DNS at Namecheap):

**On Cloudflare Pages → Custom domains**
- Add `www.yourdomain.com`. Copy the **CNAME target** it shows (looks like `your-project.pages.dev`).

**On Namecheap (Domain List → Manage → Advanced DNS → Host Records)**
- Add a **CNAME** record:
  - Host: `www`
  - Value: `<your-project>.pages.dev`
  - TTL: automatic
- Add a **URL Redirect Record** (301):
  - Host: `@`
  - Value: `https://www.yourdomain.com/`
  - TTL: automatic

Give DNS a few minutes to propagate.

> If you want the apex (`yourdomain.com`) to serve directly from Cloudflare Pages without a redirect, move your DNS to Cloudflare (change nameservers in Namecheap to the ones Cloudflare provides). Then add both `yourdomain.com` and `www.yourdomain.com` in Pages.

## 5) Optional enhancements
- **Analytics**: use Cloudflare Web Analytics or any snippet (Plausible, GA).
- **Contact**: leave the mailto link in the header or add a Netlify/Forms alternative later.
- **SEO basics**: set a descriptive `<title>`, `<meta name="description">`, and add social share images in `/public`.

## 6) Make updates
Edit files → commit to GitHub → Cloudflare auto‑deploys new versions (with rollback).

---

**You own your domain and content. No vendor lock‑in.** This static setup is fast, cheap, and scalable.
