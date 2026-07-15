# Icon and Logo Decisions

## Company Logos in Teardown Cards

### Why real logos instead of text/colour blocks?

Visual recognition matters. A hiring manager scanning 7 teardown cards will instantly recognise Blinkit's yellow, Duolingo's green, and Swiggy's blue. Text-only cards require reading; logo cards trigger instant recognition.

Additionally, using actual logos signals attention to detail — a PM who cares enough to embed the actual brand assets, not a placeholder.

### Source

All 7 company logos were uploaded by the user as image files and embedded as base64. They were not hotlinked from external URLs (which would break if the source changes).

### Logo + Background Combinations

| Product | Logo background | Reasoning |
|---|---|---|
| Blinkit | `#f0fce8` / `#f7c01a` | Brand yellow; Blinkit's identity |
| Inshorts | `#111` | Dark background matches the app's dark UI |
| Khan Academy | `#fff` | Clean white; KA's clean educational brand |
| Supercell | `#000` | Black; matches Supercell's dark premium branding |
| Playo | `#1eb954` | Playo's primary green (similar to Spotify green) |
| Swiggy Instamart | `#1a56ff` | Swiggy blue |
| Duolingo | `#fff` | White background makes the Duo owl pop |

---

## Contact Icons — Emoji to Real Logos

### The Decision

Original design used emoji for contact icons:
- ✉️ for email
- 💼 for LinkedIn
- 🐙 for GitHub
- 📱 for phone

User uploaded actual brand logos: `gmail_logo.jpg`, `linkedin_logo.jpg`, `github_logo.svg`.

**Why replace emoji with real logos:**
- Emoji render differently across operating systems (Apple vs Google vs Windows)
- Real logos have consistent, brand-accurate appearance everywhere
- Professional portfolios use actual logos — it matches industry standard (LinkedIn, GitHub themselves use their actual icons in "connect" buttons)

### What Was Replaced vs Kept

| Icon | Original | Final | Notes |
|---|---|---|---|
| Email | ✉️ | Gmail logo | Real logo uploaded |
| LinkedIn | 💼 | LinkedIn logo | Real logo uploaded |
| GitHub | 🐙 | GitHub logo | Real logo uploaded (SVG) |
| Phone | 📱 | 📱 (kept as emoji) | No phone logo uploaded |
| Location | 📍 | 📍 (kept as emoji) | No location icon uploaded |

### Implementation

Icons are embedded as base64 and rendered as `<img>` tags inside the icon container:

```html
<!-- Gmail in sidebar contact row -->
<div class="s-icon" style="background:#fff;padding:4px;">
  <img src="data:image/jpeg;base64,..." alt=""
       style="width:18px;height:18px;object-fit:cover;border-radius:3px;display:block;flex-shrink:0;">
</div>

<!-- LinkedIn in sidebar social buttons -->
<a href="..." class="s-social" title="LinkedIn" style="padding:3px;">
  <img src="data:image/jpeg;base64,..." alt=""
       style="width:26px;height:26px;object-fit:cover;border-radius:3px;">
</a>

<!-- GitHub in sidebar social buttons -->
<a href="..." class="s-social" title="GitHub" style="padding:4px;background:#fff;">
  <img src="data:image/svg+xml;base64,..." alt=""
       style="width:22px;height:22px;object-fit:cover;border-radius:3px;">
</a>
```

Note: GitHub SVG logo gets a `background:#fff` on its container because the SVG has a transparent background — it would be invisible on a dark surface without the white backing.

### Where Icons Appear

**Sidebar variant:**
- Sidebar contact rows (Gmail icon in the email row)
- Sidebar social buttons (LinkedIn + GitHub)
- Contact section cards (Gmail, LinkedIn, GitHub)

**Warm variant:**
- Contact section contact items (email, LinkedIn, GitHub rows)

**Dark variant:**
- Contact section contact items (same as warm)

---

## Resume Logo (warm + dark variants)

User uploaded `resume_logo.webp` — a small icon used on the "Download Resume" button in the warm and dark portfolios.

```html
<a href="RESUME_URI" download="..." class="nav-resume-btn">
  <span style="display:inline-flex;align-items:center;gap:6px;">
    <img src="data:image/webp;base64,..." alt=""
         style="width:16px;height:16px;object-fit:contain;background:#fff;padding:2px;border-radius:3px;">
    Resume
  </span>
</a>
```

This icon appears in the top nav of warm and dark portfolios. The sidebar portfolio uses plain text "📄 Resume" in the tab nav instead.

---

## Approach to Icons Not Yet Replaced

Phone (📱) and location (📍) remain as emoji because:
1. No brand icon exists for a generic phone number or location
2. Emoji are universally understood for these
3. The visual inconsistency is minor — phone and location are less prominent than email/LinkedIn/GitHub

If a specific phone icon is desired in the future, Font Awesome or similar icon library could be loaded, or a custom SVG could be embedded.
