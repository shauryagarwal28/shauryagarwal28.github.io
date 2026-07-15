# Shaurya Agarwal — PM Portfolio: Knowledge Base

> Complete documentation of every product, design, and technical decision made during the build of this PM portfolio. This is the living source of truth for all future changes.

**Live site:** [shauryaagarwal.github.io](https://shauryaagarwal.github.io)

---

## Directory Structure

```
docs/
├── README.md                          ← You are here. Master index.
│
├── product/
│   ├── portfolio-strategy.md          ← Why this portfolio exists, goals, target audience
│   ├── content-strategy.md            ← Copy decisions, tone, what goes where
│   └── teardown-framework.md          ← The 10-component framework used across all teardowns
│
├── technical/
│   ├── architecture.md                ← File structure, how the three variants relate
│   ├── asset-pipeline.md              ← Base64 embedding system, /tmp/assets.json
│   └── deployment.md                  ← GitHub Pages setup, file naming, upload order
│
├── design/
│   ├── design-system.md               ← CSS variables, typography, color palettes per variant
│   ├── layout-decisions.md            ← Why sidebar vs full-page vs warm; layout comparisons
│   └── component-library.md           ← Reusable patterns: cards, tags, timelines, nav
│
├── decisions/
│   ├── portfolio-variant-decisions.md ← When and why each variant was created
│   ├── nav-evolution.md               ← History of nav tab placement decisions
│   ├── certificate-placement.md       ← Where cert lives and why it moved
│   └── icon-logo-decisions.md         ← Real logos vs emoji, what was replaced and when
│
└── content/
    ├── bio-copy.md                    ← Approved bio text, key stats, copy rules
    ├── experience-bullets.md          ← All work experience bullets, sources, metrics
    └── teardown-summaries.md          ← One-paragraph summary of each teardown
```

---

## Quick Reference

### Three Portfolio Files

| File | Purpose | Theme |
|---|---|---|
| `index.html` (rename from `shaurya-pm-portfolio.html`) | Primary portfolio | Warm cream — Playfair + Inter |
| `portfolio-dark.html` | Dark techy variant | Dark with teal accent |
| `portfolio-sidebar.html` | Reference-style variant | Dark with orange accent, sidebar layout |

### Key Assets (all embedded as base64 in `/tmp/assets.json`)
- 7 company logos: blinkit, inshorts, khan_academy, supercell, playo, swiggy_instamart, duolingo
- 3 contact icons: gmail, linkedin, github
- Certificate: Nextleap_Certificate.pdf
- Resume: Shaurya_Agarwal_Resume.pdf

### Content Stats
- 7 teardown documents (10 components each)
- 6 case study files
- 3 portfolio variants
- 1 README

---

## Last Updated
July 2026 — after final nav, cert, logo, and Resume button fixes across all three variants.
