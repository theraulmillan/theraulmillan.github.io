# Website Project — the.raulmillan.com

**URL:** https://the.raulmillan.com  
**GitHub repo:** https://github.com/theraulmillan/theraulmillan.github.io  
**Theme:** Beautiful Jekyll  
**Local folder:** ~/Developer/cowork/personal/website  
**Last updated:** 2026-05-01

---

## Current Status: ✅ Live

The site is fully deployed and running on GitHub Pages with a custom domain, automatic HTTPS, and a GitHub Actions build pipeline that triggers on every push to `master`.

---

## What Was Done

### Infrastructure
- Fixed git remote — was pointing to the original Freelancer theme repo (`jeromelachaud/freelancer-theme`), now correctly points to `theraulmillan/theraulmillan.github.io`
- Created `CNAME` file for custom domain `the.raulmillan.com`
- Added `.github/workflows/jekyll.yml` — GitHub Actions build and deploy pipeline using `actions/jekyll-build-pages` (avoids apt/Launchpad issues)
- Removed `ci.yml` — pre-existing Beautiful Jekyll CI workflow that was failing on every push due to Launchpad network timeouts
- Resolved git branch divergence between local Freelancer theme commits and remote Beautiful Jekyll commits
- Updated `Gemfile` to use explicit gem versions compatible with Ruby 3.x (removed `gemspec` reference to old Freelancer gemspec)

### Theme Migration
- The remote repo was already using **Beautiful Jekyll**, not the old Freelancer theme
- Fixed `_layouts/default.html` which still contained the Freelancer HTML layout causing build failures
- Replaced `_config.yml` with a proper Beautiful Jekyll configuration

### Content & Personalization
- Updated `_config.yml` with real info: name, description, social links (LinkedIn, GitHub, Instagram), Panama timezone, correct URL
- Updated `index.html` with English title and subtitle
- Created `about.md` with professional bio
- Translated all **22 blog posts** from Spanish to English (posts dating back to 2009)
- Translated `bio.md`, `conferences.md`, and `events.md` from Spanish to English
- Added `blog.md` to make the Blog nav link work correctly
- Updated navbar to include an **About dropdown** with: About, Bio, Speaking, Events

### Profile & Branding
- Updated profile photo to `IMG_6063.jpeg`
- Copied profile photo to `assets/img/profile.jpeg` (path referenced by Beautiful Jekyll)
- Generated dark navy (`#2c3e50`) shield favicon from scratch using Python PIL
- Added favicon link tags to `_includes/head.html`

---

## How the Site Works

**Jekyll build cycle:**
1. Push any change to `master`
2. GitHub Actions triggers the `jekyll.yml` workflow
3. `actions/jekyll-build-pages` builds the static site (no Ruby install needed)
4. Output is deployed to GitHub Pages CDN
5. Site is live at `the.raulmillan.com` in ~1–2 minutes

**Key files:**

| File | Purpose |
|---|---|
| `_config.yml` | Site-wide settings: title, social links, navbar, colors, plugins |
| `index.html` | Homepage — uses `layout: home`, shows blog post list |
| `about.md` | About page |
| `bio.md` | Extended bio with affiliations and links |
| `conferences.md` | Speaking engagements history |
| `events.md` | Events attended |
| `blog.md` | Blog listing page |
| `_posts/YYYY-MM-DD-title.md` | Blog posts — filename date controls ordering |
| `_includes/head.html` | HTML `<head>` — favicon link is here |
| `assets/img/profile.jpeg` | Profile photo (used as navbar avatar) |
| `assets/img/favicon.ico` | Dark navy shield favicon |
| `.github/workflows/jekyll.yml` | GitHub Actions deploy pipeline |

---

## Writing a New Blog Post

Create a file in `_posts/` named `YYYY-MM-DD-your-title.md`:

```markdown
---
layout: post
title: Your Post Title
subtitle: Optional subtitle
tags: [cybersecurity, zero-trust]
---

Your content here in Markdown.
```

Then:
```bash
git add _posts/your-file.md
git commit -m "New post: Your Post Title"
git push
```

---

## Remaining / Ideas

- [ ] Change site title and homepage subtitle (currently `_config.yml` `title` and `index.html` subtitle)
- [ ] Review and update older posts (2009–2018) — content may be outdated
- [ ] Add cover images to blog posts for visual appeal
- [ ] Set up Formspree contact form (hooks already in Beautiful Jekyll)
- [ ] Add Google Analytics (`gtag` field in `_config.yml`)
- [ ] Consider adding a dedicated "Services" or "Consulting" page
- [ ] Review `bio.md` vs `about.md` — content overlaps; may want to consolidate or differentiate
- [ ] Update `conferences.md` and `events.md` with any 2021–2026 activity

---

## Useful Commands

```bash
# Navigate to site folder
cd ~/Developer/cowork/personal/website

# Push a change
git add .
git commit -m "Your message"
git push

# Check deployment status
# → https://github.com/theraulmillan/theraulmillan.github.io/actions
```
