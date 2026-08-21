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
- [ ] Decide: update Skills section to match CV (adds SAP FICO/TRM/ABAP, GCP, Node.js, React, more analytics tools). Note: Skills chips in all 3 variants list "React Native" - Chalo is Flutter-only, worth checking if that chip is accurate for anything else or should go
- [ ] Missing case study pages for Playo, Swiggy Instamart, Duolingo (teardowns exist, case studies referenced in README don't)
- [ ] Chalo: real highway PTT test and physical-device verification still pending (tracked in the app's own repo, not this one)

### Completed
- [x] 2026-08-21 - Found and cloned the real live repo (`shauryagarwal28/shauryagarwal28.github.io`); corrected a wrong URL in the KB docs (`shauryaagarwal.github.io` doesn't exist)
- [x] 2026-08-21 - Reconciled scattered Downloads copies: pulled the latest unpushed edits of all 3 variants into `~/portfolio`, archived older versions into `~/Downloads/portfolio drafts/`
- [x] 2026-08-21 - Replaced the downloadable resume (was silently serving a stale 5.9KB stub) with `Shaurya_Agarwal_CV.pdf` content, across all 3 variants + the repo's own `Shaurya_Agarwal_Resume.pdf`; deleted the stale `Shaurya_Agarwal_OLD_Resume.pdf`
- [x] 2026-08-21 - Updated Experience section (role titles + bullets) in all 3 variants to match the CV
- [x] 2026-08-21 - Removed all em dashes (11 total across the 3 files) per content tone rule
- [x] 2026-08-21 - Committed and pushed to GitHub (`25cdb03`), live site rebuilding
- [x] 2026-08-21 - Fixed wrong LinkedIn URL (was `linkedin.com/in/shauryaagarwal`, now `https://www.linkedin.com/in/shauryaagarwal28/`) - hrefs and display text, across all 3 variants + README + content-strategy.md. Pushed (`82d3c66`), verified live.
- [x] 2026-08-21 - Fixed missing GitHub contributions: today's commits had an unverified local email (`shaurya@Shauryas-MacBook-Air.local`) not linked to the GitHub account, so they weren't counting on the profile graph. Set correct repo git config (`52820402+shauryagarwal28@users.noreply.github.com`), rewrote the affected commits' author info, force-pushed. Verified via GitHub API that all commits now show `author_login: shauryagarwal28`.
- [x] 2026-08-21 - Built `chalo-case-study.html`, a dedicated case study page for Chalo (previously squeezed into a one-card summary). Sections: problem, product decisions, what's actually built (honest status table), a real engineering problem solved (Android/Agora namespace collision, explained in plain language), current status and what's next, link to code. Includes 3 real screenshots captured live from the iOS simulator (splash, home, live ride map + PTT), resized/compressed to ~164KB total.
- [x] 2026-08-21 - Synced `chalo-app-public` GitHub repo (was a month stale) to current app state via a clean single-commit snapshot (code only, no internal docs/history exposed, no secrets - verified via `git archive` on tracked files only). `chalo-app` (private) untouched.
- [x] 2026-08-21 - Fixed the Chalo Work-section card in all 3 variants: it was using CSS classes that don't exist in each file's stylesheet (broken rendering, worst in `index.html` - no card border, no tag colour, unstyled labels). Rebuilt using each variant's real, working card pattern (verified class-by-class against the other 7 teardown cards). Also fixed: stale "Pre-Development"/"Full PRD, moving into UI design" status text (now "27/27 screens built"), wrong "React Native / Flutter" platform text (app is Flutter-only), added "(working title)" framing since the name isn't final, added a link to the new case study page. `portfolio type 2.html`'s Chalo card was also sitting structurally outside its grid/section entirely - moved inside.
- [x] 2026-08-21 - Fixed broken "View/Read full case study" links (404s) across all 3 variants. `index.html` and `portfolio type 2.html` linked to `-case-study.html` names that never existed for 5 teardowns (blinkit, inshorts, playo, duolingo, swiggy) - real files use `-teardown.html`. `portfolio type 3.html` had the opposite problem for Khan Academy. Fixed hrefs to match real filenames, no content files renamed. Pushed (`f8de13e`).
- [x] 2026-08-21 - Simplified the Signify Experience role title from "Business Analyst / Data Engineer / SAP FICO Analyst" to just "Business Analyst" across all 3 variants, per user request. SAP/data-engineering detail stays fully described in the bullets below it. Pushed (`1d4f695`).
- [x] 2026-08-21 - Added description, homepage link, and topics (flutter, mobile-app, google-maps) to `chalo-app-public`'s GitHub About section - it was completely empty, just showing the bare repo name.
- [x] 2026-08-21 - Moved Chalo to first position in the Work/Case Studies list in all 3 variants (was last, after the 7 teardowns). Updated `agents/product/content-strategy.md`'s documented card order to match. Also fixed a related bug found in `portfolio type 3.html`: Chalo was tagged `data-cat="personal"`, which has no matching filter tab (only All/0-to-1 Feature/Strategy/Company exist) - it would vanish under the "0-to-1 Feature" filter, the one it actually belongs to. Retagged to `data-cat="feature"`.

---

## Update Log

### 2026-08-21
- Set up `~/portfolio` as the working directory, cloned from GitHub.
- Reconciled Downloads vs repo: latest variant files moved into `~/portfolio`, stale ones archived to `~/Downloads/portfolio drafts/` with disambiguating names.
- Fixed resume: portfolio download button was serving an old 5.9KB resume, not the current CV. Now serves `Shaurya_Agarwal_CV.pdf` content everywhere (embedded downloads + repo file).
- Updated Experience section text (role titles, bullet wording) in all 3 variants to match the CV instead of the older resume wording.
- Established 5 standing working rules (see top of this file) and this log itself, per user request.
- Removed all em dashes (11 total) across the 3 variants per the content tone rule.
- Fixed the LinkedIn URL (hrefs + display text) across all 3 variants, README, and content-strategy.md.
- Fixed a git identity issue that was hiding today's commits from the GitHub contribution graph; rewrote affected commits and force-pushed.
- All changes pushed to GitHub and verified live at each step (final commit as of this entry: `b56d274`).
