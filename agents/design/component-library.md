# Component Library

## Reusable Patterns

All three portfolio variants share these component patterns with minor visual variations per design system.

---

## Navigation

### Top Nav (warm + dark variants)

```html
<nav>
  <a href="#" class="nav-logo">Shaurya Agarwal</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#teardowns">Work</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="RESUME_URI" download="..." class="nav-resume-btn">📄 Resume</a>
  <a href="#contact" class="nav-cta">Say hello ✉</a>
</nav>
```

**Behaviour:** Fixed at top, `backdrop-filter: blur(12px)` frosted glass effect, hides scroll position.

### Tab Nav (sidebar variant)

```html
<nav class="tab-nav">
  <button class="tab-btn active" onclick="show('about', this)">About</button>
  <button class="tab-btn" onclick="show('experience', this)">Experience</button>
  <button class="tab-btn" onclick="show('casestudies', this)">Case Studies</button>
  <button class="tab-btn" onclick="show('skills', this)">Skills</button>
  <button class="tab-btn" onclick="show('contact', this)">Contact</button>
  <a href="RESUME_URI" download="..." class="tab-resume">📄 Resume</a>
</nav>
```

**Active state:** `border-bottom: 2px solid var(--accent)` on active tab. Resume button is `margin-left: auto` to push it to the right edge.

---

## Section Headers

### Warm variant

```html
<div class="section-eyebrow">My work</div>
<h2 class="section-title">Product teardowns &<br><em>case studies</em></h2>
```

Eyebrow: JetBrains Mono, 11px, uppercase, rust colour, with a horizontal line before it.
Title: Playfair Display, large, italic em for accent colour.

### Dark / Sidebar variants

```html
<div class="sec-eyebrow">Product thinking in action</div>
<h2 class="sec-title">Case Studies &<br><em>Teardowns</em></h2>
<div class="sec-line"></div>
```

Eyebrow: 11px monospace, uppercase, accent colour.
Title: Playfair Display.
Line: 36–40px wide, 2px tall, accent colour, rounded.

---

## Teardown / Case Study Cards

### Card structure (sidebar variant)

```html
<div class="case-card" data-cat="feature">
  <div class="case-header">
    <div class="case-logo" style="background:#f0fce8;">
      <img src="LOGO_BLINKIT" alt="Blinkit">
    </div>
    <div class="case-meta">
      <span class="case-tag tag-orange">0-to-1 Feature</span>
      <div class="case-title">Blinkit: Recipe-to-Cart</div>
      <div class="case-sub">Bridging content and commerce in quick grocery delivery</div>
    </div>
  </div>
  <button class="case-toggle" onclick="toggleCase(this)">
    Read case study <span class="case-arrow">↓</span>
  </button>
  <div class="case-body">
    <!-- expanded content: problem, solution, metrics, link -->
    <a href="blinkit-teardown.html" target="_blank" class="view-link">View full teardown →</a>
  </div>
</div>
```

**Filter attribute:** `data-cat` values: `feature`, `strategy`, `company`

**Toggle behaviour:** Arrow rotates 180° on open. Button text changes from "Read case study" to "Close".

### Category Tag Colours (sidebar variant)

| Tag class | Colour | Products |
|---|---|---|
| `.tag-orange` | `#ff6b35` (orange) | Blinkit |
| `.tag-blue` | `#6495ed` (cornflower) | Inshorts |
| `.tag-teal` | `#4ecdc4` (teal) | Khan Academy |
| `.tag-amber` | `#c8a96e` (gold) | Supercell, Swiggy |
| `.tag-green` | `#4ade80` (green) | Playo |
| `.tag-purple` | `#a78bfa` (violet) | Duolingo |

---

## Metrics Pills

```html
<div class="metrics-row">
  <div class="metric-pill">
    <div class="ml">AOV uplift</div>
    <div class="mv">1x → 1.8x</div>
  </div>
  <div class="metric-pill">
    <div class="ml">Items/order</div>
    <div class="mv">5-7 → 12+</div>
  </div>
</div>
```

The `ml` (metric label) class is small monospace uppercase. The `mv` (metric value) class is larger, medium weight, accent coloured in dark/sidebar; brown in warm.

---

## Timeline (Experience section)

### Sidebar variant

```html
<div class="timeline">
  <div class="tl-item">
    <div class="tl-dot"></div>
    <div>
      <div class="tl-period">Jul 2023 - Dec 2025</div>
      <div class="tl-company">Signify (Philips Lighting) · Bangalore</div>
      <div class="tl-role">Business Analyst / SAP Consultant</div>
      <ul class="tl-bullets">
        <li>Led end-to-end implementation of the Corporate Card product...</li>
      </ul>
    </div>
  </div>
</div>
```

The `.timeline` container has `position: relative` with a `::before` pseudo-element creating a vertical line (`left: 7px, width: 1px, background: var(--border)`). Each `.tl-dot` is a circle on the line.

### Warm variant

Uses a different timeline style with numbered dots and grid layout:
```html
<div class="exp-card">
  <div class="exp-period">Jul 2023 - Dec 2025</div>
  <div class="exp-company">Signify (Philips Lighting)</div>
  <div class="exp-role">Business Analyst / SAP Consultant</div>
  <ul class="exp-list">...</ul>
</div>
```

---

## Education Cards

### Standard education card

```html
<div class="edu-card featured">
  <div class="edu-type">🎓 Undergraduate</div>
  <div class="edu-inst">SRM Institute of Science and Technology</div>
  <div class="edu-deg">B.Tech in Computer Science</div>
  <div class="edu-score">CGPA 8.7 / 10</div>
  <div class="edu-desc">...</div>
  <div class="edu-period">2019 - 2023</div>
</div>
```

`edu-score` uses green background pill: `rgba(74,222,128,0.08)` with green text.

### Nextleap certification card (sidebar variant)

```html
<div class="cert-card">
  <div class="cert-badge">✦ CERTIFIED</div>
  <div class="edu-type">📋 Fellowship</div>
  <div class="edu-inst">Nextleap PM Fellowship</div>
  <div class="edu-deg">Product Management</div>
  <div class="edu-score">✓ Oct - Dec 2025</div>
  <div class="edu-desc">8-week intensive...</div>
  <a href="CERT_URI" download="..." class="cert-dl">📄 Download Certificate</a>
</div>
```

The `.cert-badge` is `position: absolute; top: 12px; right: 12px;` — a small pill in the top-right corner of the card. The card has a gold gradient background and stronger border (`1.5px solid rgba(200,169,110,0.5)`).

---

## Skill Groups

```html
<div class="skills-grid">
  <div class="skill-group">
    <div class="skill-label">Product & Strategy</div>
    <div class="chip-wrap">
      <span class="chip">Product Lifecycle</span>
      <span class="chip">Roadmap Dev</span>
      <span class="chip">RICE</span>
      <!-- ... -->
    </div>
  </div>
</div>
```

Four groups: Product & Strategy, Analytics & Data, Delivery, Technical.

---

## Contact Section

### Contact cards (sidebar variant)

```html
<div class="contact-grid">
  <a href="mailto:..." class="contact-card">
    <div class="cc-icon"><img src="GMAIL_LOGO" ...></div>
    <div>
      <div class="cc-lbl">Email</div>
      <div class="cc-val">shauryagarwal28@gmail.com</div>
    </div>
  </a>
</div>
```

### Availability box + CTA

```html
<div class="avail-box">
  <div class="avail">...</div>
  <h3>Ready to contribute from Day 1</h3>
  <p>...</p>
  <span class="reply">⚡ I usually reply within a day</span>
  <a href="mailto:..." class="say-hello">Say hello →</a>
</div>
```

---

## Filter System

```html
<div class="filter-row">
  <button class="filter-btn active" onclick="filterCases('all', this)">All</button>
  <button class="filter-btn" onclick="filterCases('feature', this)">0-to-1 Feature</button>
  <button class="filter-btn" onclick="filterCases('strategy', this)">Strategy</button>
  <button class="filter-btn" onclick="filterCases('company', this)">Company</button>
</div>
```

Active filter: `background: var(--accent); border-color: var(--accent); color: #fff` (or dark bg).
Inactive: transparent background, muted text.
