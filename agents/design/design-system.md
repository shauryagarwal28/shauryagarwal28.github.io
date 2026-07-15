# Design System

## Three Variants — Three Palettes

Each portfolio variant has its own complete design system defined via CSS custom properties (`:root` variables). They share structural patterns but are visually distinct.

---

## Variant 1: Warm (index.html / shaurya-pm-portfolio.html)

**Character:** Editorial, premium, human. Feels like a well-designed magazine profile.

### CSS Variables

```css
:root {
  --cream:        #faf7f2;   /* page background */
  --cream2:       #f3ede3;   /* alternate section background */
  --brown:        #2c1f0e;   /* primary text */
  --brown-soft:   #5c4a30;   /* secondary text */
  --brown-muted:  #9c8468;   /* muted/metadata text */
  --rust:         #c94a1f;   /* accent — CTA buttons, eyebrows, highlights */
  --sage:         #4a7c59;   /* used sparingly for tags */
  --sky:          #2a5fa5;   /* used for recommendation-type tags */
  --border:       rgba(44,31,14,0.10);
  --white:        #ffffff;
  --font-serif:   'Playfair Display', Georgia, serif;
  --font-body:    'Inter', sans-serif;
  --font-mono:    'JetBrains Mono', monospace;
  --ease:         0.25s cubic-bezier(0.4,0,0.2,1);
}
```

### Typography

| Role | Font | Weight | Size |
|---|---|---|---|
| Hero h1 | Playfair Display | 400 | clamp(3rem, 6vw, 5rem) |
| Section titles | Playfair Display | 400 | clamp(2rem, 4vw, 3rem) |
| Body copy | Inter | 300–400 | 15–16px |
| Labels/eyebrows | JetBrains Mono | 500 | 11–12px |
| Nav links | Inter | 500 | 14px |

### Teardown Tag Colours

| Tag | Class | Colour |
|---|---|---|
| 0-to-1 Feature | `.tag-rust` | `#c94a1f` (rust) |
| Recommendation System | `.tag-sky` | `#2a5fa5` (sky) |
| Growth & AI | `.tag-sage` | `#4a7c59` (sage) |
| Company Teardown | `.tag-brown` | `#5c4a30` (brown-soft) |
| Retention | `.tag-amber` | amber tone |

---

## Variant 2: Dark (portfolio-dark.html)

**Character:** Technical, modern, high-contrast. Feels like a well-designed developer portfolio.

### CSS Variables

```css
:root {
  --bg:      #0f0f0f;                  /* page background */
  --surface: #1a1a1a;                  /* card/nav background */
  --surface2:#242424;                  /* nested card/chip background */
  --border:  rgba(255,255,255,0.08);
  --text:    #f0f0f0;                  /* primary text */
  --text2:   #999;                     /* secondary text */
  --text3:   #666;                     /* muted/metadata */
  --accent:  #c8a96e;                  /* gold accent */
  --accent2: #e8c98e;                  /* lighter gold for italic titles */
  --green:   #4ade80;                  /* availability badge */
  --font:    "Inter", sans-serif;
  --serif:   "Playfair Display", Georgia, serif;
  --r:       12px;                     /* border-radius */
  --ease:    0.25s cubic-bezier(0.4,0,0.2,1);
}
```

### Typography

| Role | Font | Weight | Size |
|---|---|---|---|
| Section titles | Playfair Display | 400 | clamp(1.8rem, 4vw, 2.6rem) |
| Body copy | Inter | 400 | 15px |
| Labels | Inter monospace | 500 | 11px |

---

## Variant 3: Sidebar (portfolio-sidebar.html)

**Character:** Structured, professional, reference-portfolio style. Modelled after rakeshks2k.github.io/portfolio/.

### CSS Variables

```css
:root {
  --bg:       #111111;
  --surface:  #1c1c1c;
  --surface2: #252525;
  --surface3: #2e2e2e;
  --border:   rgba(255,255,255,0.07);
  --text:     #efefef;
  --text2:    #aaa;
  --text3:    #666;
  --accent:   #e07b39;                 /* orange — key difference from dark variant */
  --accentl:  rgba(224,123,57,0.12);  /* light orange for backgrounds */
  --green:    #4ade80;
  --font:     "Inter", sans-serif;
  --serif:    "Playfair Display", Georgia, serif;
  --r:        10px;
  --ease:     0.22s cubic-bezier(0.4,0,0.2,1);
}
```

### Accent Colour Decision

The sidebar variant uses **orange (#e07b39)** instead of the dark variant's **gold (#c8a96e)**. This is intentional — the two dark variants must be visually distinct so they feel like different design choices, not like the same template with minor tweaks.

Orange also reads better on the sidebar's lighter surface colour (#1c1c1c vs #1a1a1a) and matches the reference portfolio's energy.

---

## Shared Design Patterns

### Availability Badge (all three variants)

```html
<div class="avail">
  <span class="avail-dot"></span>
  Open to opportunities
</div>
```

```css
.avail-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 6px var(--green);
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50%       { opacity: 0.4; transform: scale(0.8); }
}
```

### Fade-in Animation (all three variants)

Elements with `.fade-in` class start invisible and slide up into view when `.visible` is added via JavaScript:

```css
.fade-in {
  opacity: 0;
  transform: translateY(14px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

Staggered: each `.fade-in` element in a section gets a delay of `index * 70ms`.

### Border Radius Convention

- Warm: `20px` for cards, `100px` for pills/buttons
- Dark: `12px` for cards (`--r`), `100px` for pills
- Sidebar: `10px` for cards (`--r`), `100px` for pills

---

## Responsive Breakpoints

| Breakpoint | Behaviour |
|---|---|
| `max-width: 900px` | Sidebar collapses to stacked layout (sidebar above, panel below) |
| `max-width: 700px` | Content padding reduces; some grids collapse to 1 column |
| `max-width: 600px` | Contact grid goes 1 column |
| `max-width: 540px` | Expertise grid goes 1 column |

---

## Google Fonts

### Warm variant

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Inter:wght@300;400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

### Dark and sidebar variants

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
```

The warm variant additionally loads JetBrains Mono for the monospace eyebrow labels. The dark and sidebar variants use `monospace` as a generic fallback instead of loading a specific mono font.
