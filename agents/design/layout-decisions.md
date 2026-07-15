# Layout Decisions

## The Three Layout Approaches

### Approach 1: Warm — Full-page scrolling (index.html)

**Structure:** Single-page, full-width, scrolling. Fixed nav at top.

```
[Fixed top nav: logo | links | CTA]
[Hero section — full viewport height]
[About section]
[Experience section]
[Education section]
[Teardowns section — 7 cards in grid]
[Skills section]
[Contact section]
```

**Why this layout:**
- Most familiar and comfortable for hiring managers
- Scrolling reveals content progressively — good storytelling pacing
- Each section has clear visual separation (alternating background colours)
- Easy to share individual sections via anchor links (`#teardowns`, `#contact`)

**Max-width:** Content constrained to ~1100px, centered.

---

### Approach 2: Dark — Full-page scrolling (portfolio-dark.html)

**Structure:** Same as warm — single-page scrolling, fixed nav.

Identical layout to warm, different colour palette. Built as a visual alternative, not a structural one.

**Why this exists:**
- Some hiring managers associate dark themes with technical competence
- Allows Shaurya to share whichever variant fits the specific company culture
- Demonstrates range without requiring different content

---

### Approach 3: Sidebar — Tab-switched panel (portfolio-sidebar.html)

**Structure:** Two-column layout. Sticky sidebar on the left, scrollable right panel with tab navigation at the top.

```
[Fixed sidebar (300px)]          [Right panel]
  - Avatar (SA initials)           [Tab nav: About | Experience | Case Studies | Skills | Contact | Resume →]
  - Name                           [-------------------------------------------]
  - Role                           [Active section content]
  - Availability badge             
  - Divider                        
  - Contact details (rows)         
  - LinkedIn + GitHub icons        
```

**Why this layout:**
- Modelled after rakeshks2k.github.io/portfolio/ (reference provided by user)
- Contact info is always visible in the sidebar — no scrolling to find it
- Tab switching feels modern and app-like
- Resume button is always visible in tab nav — highest visibility placement

**Key layout decisions within this variant:**

| Decision | Choice | Why |
|---|---|---|
| Nav tabs | Inside right panel, at the top | Matches reference portfolio; visible at all times |
| Resume button | In tab nav bar, right-aligned | Always visible; top-right is a natural CTA position |
| Certificate | Experience tab only, not sidebar | Sidebar is for contact info; cert is educational credential |
| Sidebar width | 300px | Matches reference portfolio proportions |
| Max outer width | 1140px | Wider than single-column variants to accommodate sidebar + content |
| Sidebar sticky | `position: sticky; top: 40px; height: calc(100vh - 40px)` | Sidebar stays in view while panel content scrolls |

---

## Layout Iteration History

### Iteration 1: Nav tabs at bottom of sidebar
**Problem:** Nav tabs pushed to bottom with `margin-top: auto`, which meant they were below the fold on most screens. User couldn't see navigation options without scrolling.

**Fix:** Moved tabs to top of sidebar, styled as a boxed nav with `border: 1px solid var(--border)` and active state with gold left-border accent.

### Iteration 2: Nav tabs in sidebar, sidebar layout
**Problem:** User shared screenshot of reference portfolio (rakeshks2k.github.io/portfolio/) — it has tabs at the TOP of the RIGHT PANEL, not in the sidebar at all. The sidebar only has contact info and social links.

**Fix:** Complete structural rebuild. Moved tabs to top of right panel as `.tab-nav`. Sidebar stripped to just: avatar, name, role, availability badge, contact details, social icons.

### Iteration 3: Sidebar had a centered column but no sidebar
**Problem:** Claude misread the reference screenshot and built a centered single-column layout with no sidebar at all.

**Fix:** User uploaded the screenshot. Rebuilt with actual two-column structure: `grid-template-columns: 300px 1fr`.

### Iteration 4: Resume in sidebar + tab nav
**Problem:** Resume download appeared both in the sidebar and in the tab nav bar, creating redundancy. User asked to remove it from sidebar and keep it only in the top tab nav.

**Fix:** Removed `<a class="s-resume">Download Resume</a>` from sidebar HTML. Tab nav resume button (`.tab-resume`) retained.

---

## The Reference Portfolio Analysis (rakeshks2k.github.io/portfolio/)

Key structural elements taken from the reference:

| Feature | How it's implemented |
|---|---|
| Sidebar with profile photo | Avatar with initials (SA) in a circle with accent border |
| Contact info in sidebar rows | `.s-row` elements with icon + label + value |
| Social icons at sidebar bottom | `.s-social` square buttons with LinkedIn + GitHub logos |
| Tab nav inside right panel | `.tab-nav` with border-bottom, active tab has accent underline |
| About Me as first tab | Section opens with bio, then expertise grid |
| Expertise cards in 2-col grid | `.exp-card` in `grid-template-columns: 1fr 1fr` |
| Case Studies with filter tabs | Category filter buttons above the card grid |

Key differences from reference:

| Feature | Reference | Our version |
|---|---|---|
| Profile photo | Actual photo | SA initials (photo not provided) |
| Certifications tab | Separate tab | Merged into Experience tab under Education |
| Contact form | Has a form | Has contact cards + email link |
| Case study format | List with external links | Expandable cards with inline summaries |
