# Deployment Guide

## Hosting

**GitHub Pages** at [shauryaagarwal.github.io](https://shauryaagarwal.github.io)

Repository: `shauryagarwal28.github.io` (the username.github.io convention auto-deploys from main branch root)

---

## File Naming Rules

GitHub Pages serves `index.html` as the root URL. The primary warm portfolio file must be renamed on upload:

| Local filename | GitHub filename | Live URL |
|---|---|---|
| `shaurya-pm-portfolio.html` | `index.html` | shauryaagarwal.github.io |
| `portfolio-dark.html` | `portfolio-dark.html` | shauryaagarwal.github.io/portfolio-dark.html |
| `portfolio-sidebar.html` | `portfolio-sidebar.html` | shauryaagarwal.github.io/portfolio-sidebar.html |

All teardown and case study files keep their existing names. All internal links in the portfolio files already use these filenames (e.g., `blinkit-teardown.html`).

---

## Complete Upload Checklist

### Files to REPLACE (already exist in repo)

- [ ] `index.html` — replace with new `shaurya-pm-portfolio.html`
- [ ] `portfolio-dark.html` — replace with updated version
- [ ] `Shaurya_Agarwal_Resume.pdf` — only if resume was updated

### Files to ADD (new, not yet in repo)

- [ ] `portfolio-sidebar.html`
- [ ] `blinkit-teardown.html`
- [ ] `inshorts-teardown.html`
- [ ] `khan-academy-teardown.html`
- [ ] `playo-teardown.html`
- [ ] `swiggy-teardown.html`
- [ ] `duolingo-teardown.html`
- [ ] `supercell-teardown.html`
- [ ] `Nextleap_Certificate.pdf`
- [ ] `README.md`
- [ ] `docs/` directory (this knowledge base)

### Files UNCHANGED (already in repo, no action needed)

- `blinkit-case-study.html`
- `inshorts-case-study.html`
- `khan-academy-case-study.html`
- `playo-case-study.html`
- `swiggy-instamart-case-study.html`
- `duolingo-case-study.html`

---

## Upload Method (Recommended)

GitHub's web interface supports drag-and-drop upload of multiple files:

1. Go to `github.com/shauryagarwal28/shauryagarwal28.github.io`
2. Click **Add file → Upload files**
3. Drag all HTML, PDF, and MD files at once
4. For `index.html`: upload `shaurya-pm-portfolio.html`, then rename via the file editor (or upload with the correct name directly)
5. For `README.md`: use **Add file → Create new file**, name it `README.md`, paste content
6. Commit with message: `Add teardowns, sidebar portfolio, and knowledge base`

---

## Internal Links — Critical Check

All internal links in portfolio files use **relative paths**. This means they work correctly only if all files are in the **same directory** (the repo root).

If any file is placed in a subdirectory, all teardown links will break.

**Do not** create subdirectories like `/teardowns/` or `/case-studies/` — everything stays flat in the root.

---

## Deployment Timeline

- **Push to main branch** → GitHub Pages rebuilds automatically within ~30 seconds
- **Cache** — GitHub Pages CDN may cache for a few minutes; hard refresh (Ctrl+Shift+R) to see changes
- **Custom domain** — not configured. The live URL is the default `username.github.io` format.

---

## Verifying the Deployment

After upload, verify these URLs work:

- `shauryaagarwal.github.io` — warm portfolio loads
- `shauryaagarwal.github.io/portfolio-dark.html` — dark variant loads
- `shauryaagarwal.github.io/portfolio-sidebar.html` — sidebar variant loads
- `shauryaagarwal.github.io/blinkit-teardown.html` — teardown loads
- Resume download works (click the Resume button in any portfolio)
- Certificate download works (click in Education section)
- All company logos render (not broken image icons)
- LinkedIn, GitHub, Gmail icons render in contact section

---

## LinkedIn Featured Section

After deployment, take a screenshot of `shauryaagarwal.github.io` and upload it as the thumbnail for the Featured link on the LinkedIn profile. Use the URL `https://shauryaagarwal.github.io` as the link target.
