# Portfolio Variant Decisions

## Why Three Variants?

### Decision rationale

Building multiple portfolio variants serves different audience needs and allows A/B testing in job applications:

| Variant | Best used for | Signal it sends |
|---|---|---|
| Warm (index.html) | Default / LinkedIn / warm outreach | Polished, editorial, human |
| Dark (portfolio-dark.html) | Tech-heavy companies, startup applications | Technical confidence, modern |
| Sidebar (portfolio-sidebar.html) | Detailed reference, when asked for a portfolio | Structured, professional, thorough |

### Why not just one?

One portfolio is a single bet. Three variants allows:
1. Sharing the one that fits the company culture
2. Using the sidebar as the "full reference" when someone wants to go deep
3. Testing which converts better over time (track via different UTM links if needed)

---

## Why Vanilla HTML/CSS/JS?

**Decision:** No React, no Next.js, no build tools.

**Alternatives considered:**
- React/Next.js — would allow component reuse but requires Node.js, build step, and hosting that supports SSR or static export
- Hugo/Jekyll — static site generators; adds complexity without meaningful benefit for a 3-page portfolio
- Webflow/Framer — no-code tools; limited control over exact HTML/CSS, harder to version control

**Why vanilla won:**
- Zero dependencies = zero maintenance burden
- Open any `.html` file in a browser and it works — no `npm install`, no build step
- GitHub Pages serves static files natively — no configuration needed
- Every file is fully self-contained (assets embedded as base64) — sharing a single file is enough
- Easier for Claude (or any developer) to edit with surgical str_replace operations

**Trade-off accepted:** Larger file sizes (~780KB–1.3MB) due to base64 embedding. For a portfolio with low traffic, this is acceptable.

---

## Why Base64 Asset Embedding?

**Decision:** All logos, icons, and PDFs are embedded as base64 data URIs inside the HTML.

**Alternatives considered:**
- External asset URLs (hotlinking from original sources) — breaks if source URLs change; not reliable long-term
- Separate `/assets/` directory in the repo — requires correct relative path management; if a file is moved, links break; adds upload complexity

**Why base64 won:**
- Single file = completely self-contained; can be emailed as an attachment or shared directly
- No broken images if the GitHub repo structure changes
- Zero HTTP requests for assets (only Google Fonts CDN needed)
- Simpler upload to GitHub (upload one file, not a file + its dependencies)

**Trade-off accepted:** File sizes are large. Each portfolio HTML file is ~780KB–1.3MB. Acceptable for a professional portfolio with very low traffic volume.

---

## Naming Decision: "Case Studies" vs "Teardowns"

**Timeline:**
- Original name: "Teardowns" (used in first 2 variants)
- User request: rename to "Case Studies" in sidebar variant tab nav
- Final state: Sidebar variant uses "Case Studies" as the tab label; section title is "Case Studies & Teardowns" to preserve both terms

**Why "Case Studies" in the nav:**
- More recognisable to hiring managers who aren't in the PM community
- "Teardown" is PM community jargon; "case study" is universally understood
- The actual content is a hybrid of both — it's a teardown done in a case study format

**Why both words in the section title:**
- "Case Studies & Teardowns" signals both the format (case study) and the depth (teardown)
- Preserves searchability if someone is looking for "PM teardowns"

---

## Why No Profile Photo?

**Decision:** Sidebar variant uses "SA" initials in a circle instead of a photo.

**Reason:** No photo was provided by the user. The initials placeholder is clean and professional. Adding a photo in the future is straightforward — replace the avatar div content with an `<img>` tag.

```html
<!-- Current -->
<div class="avatar">SA</div>

<!-- Future (if photo provided) -->
<div class="avatar" style="padding:0;">
  <img src="path/to/photo.jpg" style="width:100%;height:100%;object-fit:cover;border-radius:50%;">
</div>
```

---

## Resume Button Placement — Final State

This decision went through multiple iterations. See `decisions/nav-evolution.md` for full history.

**Final state:**
| Portfolio | Resume location |
|---|---|
| Warm (index.html) | Top nav (right end) + Contact section (near "Say hello" button) |
| Dark | Top nav (right end) + Contact section |
| Sidebar | Tab nav bar (top right, always visible) only — NOT in sidebar |

**Why tab nav, not sidebar, for sidebar variant:**
The sidebar holds contact details — email, phone, LinkedIn, GitHub, location. Adding resume there creates two types of information in one column: identity info (who I am, how to reach me) and deliverables (download my documents). The tab nav is a better home for a functional button like "Download Resume" because it's always visible regardless of which section is active.
