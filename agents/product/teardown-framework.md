# Teardown Framework

## The 10-Component Structure

Every teardown document follows this exact sequence. Deviating from this structure breaks the consistent PM thinking signal the portfolio is designed to send.

| # | Component | Purpose |
|---|---|---|
| 01 | Product Overview | Context — what the product is, scale, business model |
| 02 | Problem Statement | The specific problem being solved in this teardown |
| 03 | User Personas | Who the primary users are, prioritised by P0/P1 |
| 04 | User Journey Map | Current-state journey showing where things break |
| 05 | Pain Points | Structured pain point analysis with severity levels |
| 06 | Prioritising Pain Points | Which pains to solve first and why (framework applied) |
| 07 | Solutions | Multiple solution options mapped to the pain points |
| 08 | Prioritising Solutions | RICE or equivalent framework applied to solutions |
| 09 | MVP Solution with Design | What gets built first, with concrete design description and metrics |
| 10 | Go-to-Market Strategy | How the MVP rolls out, phases, north star metric, guardrails |

---

## Teardown Types

Not all teardowns use the same lens. Three types are used:

### 0-to-1 Feature Design
For Blinkit (Recipe-to-Cart) and Playo (Squad Mode). The user identifies a gap in the product and designs a new feature from scratch. Emphasis on discovery, user research, and MVP design.

### Strategy / Recommendation System
For Inshorts (Feed), Khan Academy (Engagement), Swiggy Instamart (Retention), Duolingo (Streak). The user analyses an existing system and recommends changes. Emphasis on metrics, competitive analysis, and GTM.

### Company Teardown
For Supercell. The user analyses the entire company strategy across a multi-year arc. 11 sections instead of 10. Includes SVG diagrams.

---

## Supercell Teardown — Special Format (11 sections)

Supercell has one additional section covering the three eras of company strategy:

- **Build era (2010–2016):** Launch Clash of Clans and Clash Royale, build the brand
- **Plateau era (2016–2022):** Struggle to launch new hits, buy time with existing titles
- **Reinvention era (2023–present):** Brawl Stars breaks out, Squad Busters attempted, new studio model

Two SVG diagrams are embedded directly in the HTML:
1. **Retention loops diagram** — shows the three-loop framework (daily habit, social obligation, progression milestone)
2. **Three-era timeline with revenue sparkline** — shows ARR across the three eras

---

## Visual Components in Teardown Documents

Each teardown uses a consistent set of CSS components:

| Class | Purpose |
|---|---|
| `.sn` | Section number (e.g., "01 — Product Overview") |
| `.st` | Section title (serif font) |
| `.snaps` | Stat snapshot grid (big numbers at top) |
| `.pg` | Persona grid |
| `.pc` | Persona card |
| `.ptag` | Priority tag (p0 = red, p1 = amber, p2 = grey) |
| `.js` | Journey step container |
| `.jstep` | Individual journey step (stage + content) |
| `.paing` | Pain point grid |
| `.painc` | Pain point card |
| `.sev` | Severity tag (sh = high red, sm = medium amber, sl = low grey) |
| `.tw` | Table wrapper |
| `.badge` | Priority badge in tables (bg = green P0, ba = amber P1) |
| `.solg` | Solutions grid |
| `.mg` | Metrics grid (from → to) |
| `.phases` | GTM phase container |
| `.ph` | Individual GTM phase card |
| `.pq` | Pull quote / PM insight block |

---

## North Star Metrics by Teardown

| Product | North Star | Current → Target |
|---|---|---|
| Blinkit | % orders that include a Recipe-to-Cart basket | 0% → 5% in 3 months |
| Inshorts | DAU/MAU ratio | 42% → 48%+ |
| Khan Academy | Very Active Learners as % of KAD-licensed students | 11% → 20% in 6 months |
| Supercell | YVAL (Yearly Very Active Learners) | 1.1M → 5M in 3 years |
| Playo | Sessions per user per month | ~4 → 7+ |
| Swiggy Instamart | Pantry reorder rate | — (new metric) |
| Duolingo | DAU/MAU (Proficiency Streak variant) | 27% (baseline) → differentiated |

---

## Linked Files

Each teardown links to a corresponding case study:

| Teardown | Case Study |
|---|---|
| blinkit-teardown.html | blinkit-case-study.html |
| inshorts-teardown.html | inshorts-case-study.html |
| khan-academy-teardown.html | khan-academy-case-study.html |
| supercell-teardown.html | (no case study — company teardown format) |
| playo-teardown.html | playo-case-study.html |
| swiggy-teardown.html | swiggy-instamart-case-study.html |
| duolingo-teardown.html | duolingo-case-study.html |
