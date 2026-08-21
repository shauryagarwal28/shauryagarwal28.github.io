# Portfolio Project Log

This file is the single source of truth for what's been done, what's open, and how this project works. Read this first if picking the project back up after a break, a lost session, or a new login.

---

## Working Rules (set 2026-08-21, apply always)

1. Act as a professional portfolio builder / web developer - bring ideas, don't just execute literally.
2. Don't just agree - push back with reasoning and offer better options when a request has a weaker path baked in.
3. Confirm the plan before building anything.
4. Content tone: human, plain language, no complicated words, no em dash or en dash anywhere (hyphens only).
5. Keep this log updated after every session - what changed, what's still open.

---

## How This Project Is Organised

- **Working folder:** `~/portfolio` - cloned from the live repo `shauryagarwal28/shauryagarwal28.github.io`. Push to `main` to deploy.
- **Live site:** https://shauryagarwal28.github.io/
- **Three variants**, all self-contained HTML (no build step):
  - `index.html` - warm variant (default, editorial)
  - `portfolio type 2.html` - dark variant
  - `portfolio type 3.html` - sidebar variant (most detailed)
- **Knowledge base:** `agents/` folder - product strategy, content strategy, design decisions, nav history. Read before big content or design changes.
- **Source material:** `~/Downloads/Portfolio files/` holds teardown pages, logos, resume, cert. `~/Downloads/portfolio drafts/` is old/superseded, reference only.

---

## Task List

### Open
- [ ] Decide: sync Hero/About copy across all 3 variants to the CV's positioning line ("aspiring Product Manager...") - currently only `portfolio type 3.html` uses it, other two still say "product-minded professional"
- [ ] Decide: update Skills section to match CV (adds SAP FICO/TRM/ABAP, GCP, Node.js, React, more analytics tools)
- [ ] Decide: add CV's newer projects (Group Riding Companion App / Chalo, Secondary TAT dashboard) to the portfolio
- [ ] Missing case study pages for Playo, Swiggy Instamart, Duolingo (teardowns exist, case studies referenced in README don't)
- [ ] Push current uncommitted changes to GitHub (resume swap + experience section update) once confirmed

### Completed
- [x] 2026-08-21 - Found and cloned the real live repo (`shauryagarwal28/shauryagarwal28.github.io`); corrected a wrong URL in the KB docs (`shauryaagarwal.github.io` doesn't exist)
- [x] 2026-08-21 - Reconciled scattered Downloads copies: pulled the latest unpushed edits of all 3 variants into `~/portfolio`, archived older versions into `~/Downloads/portfolio drafts/`
- [x] 2026-08-21 - Replaced the downloadable resume (was silently serving a stale 5.9KB stub) with `Shaurya_Agarwal_CV.pdf` content, across all 3 variants + the repo's own `Shaurya_Agarwal_Resume.pdf`; deleted the stale `Shaurya_Agarwal_OLD_Resume.pdf`
- [x] 2026-08-21 - Updated Experience section (role titles + bullets) in all 3 variants to match the CV

---

## Update Log

### 2026-08-21
- Set up `~/portfolio` as the working directory, cloned from GitHub.
- Reconciled Downloads vs repo: latest variant files moved into `~/portfolio`, stale ones archived to `~/Downloads/portfolio drafts/` with disambiguating names.
- Fixed resume: portfolio download button was serving an old 5.9KB resume, not the current CV. Now serves `Shaurya_Agarwal_CV.pdf` content everywhere (embedded downloads + repo file).
- Updated Experience section text (role titles, bullet wording) in all 3 variants to match the CV instead of the older resume wording.
- Established 5 standing working rules (see top of this file) and this log itself, per user request.
- **Not yet pushed to GitHub** - changes are local only as of end of session.
