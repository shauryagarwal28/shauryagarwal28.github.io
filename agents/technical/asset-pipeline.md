# Asset Pipeline

## Overview

All visual assets (logos, icons, PDFs) are embedded as base64 data URIs inside the HTML files. No separate asset directory exists in the GitHub repo — everything is self-contained.

---

## Company Logos

### Source files (uploaded by user)

| Asset | Filename | Format | Size |
|---|---|---|---|
| Blinkit logo | blinkit_logo.jpg | JPEG | ~22KB base64 |
| Inshorts logo | inshorts_logo.png | PNG | ~22KB base64 |
| Khan Academy logo | khan_academy_logo.jpg | JPEG | ~38KB base64 |
| Supercell logo | supercell_logo.jpg | JPEG | ~42KB base64 |
| Playo logo | playo_logo.png | PNG | ~19KB base64 |
| Swiggy Instamart logo | swiggy_instamart_logo.jpg | JPEG | ~52KB base64 |
| Duolingo logo | duolingo_logo.png | PNG | ~22KB base64 |

### Where logos appear

All 7 logos appear in:
- Warm portfolio — teardown card headers (`.td-icon` div)
- Dark portfolio — teardown card headers
- Sidebar portfolio — case study card headers (`.case-logo` div)

### Logo rendering

```html
<!-- Warm/dark variant -->
<div class="td-icon" style="background:#f7c01a;">
  <img src="data:image/jpeg;base64,..." alt="Blinkit logo"
       style="width:44px;height:44px;object-fit:cover;border-radius:8px;">
</div>

<!-- Sidebar variant -->
<div class="case-logo" style="background:#f0fce8;">
  <img src="data:image/jpeg;base64,..." alt="Blinkit">
</div>
```

Logo background colours per product:

| Product | Background |
|---|---|
| Blinkit | `#f0fce8` (light green) or `#f7c01a` (yellow) |
| Inshorts | `#111` (dark, matches app) |
| Khan Academy | `#fff` (white, clean) |
| Supercell | `#000` (black) |
| Playo | `#1eb954` (Spotify green — matches Playo's brand) |
| Swiggy Instamart | `#1a56ff` (Swiggy blue) |
| Duolingo | `#fff` (white) |

---

## Contact Icons

### Source files (uploaded by user)

| Asset | Filename | Format | Usage |
|---|---|---|---|
| Gmail logo | gmail_logo.jpg | JPEG | Replaces ✉️ emoji |
| LinkedIn logo | linkedin_logo.jpg | JPEG | Replaces 💼 emoji |
| GitHub logo | github_logo.svg | SVG | Replaces 🐙 emoji |

### Icon rendering (sidebar variant)

```html
<!-- Gmail in sidebar contact row -->
<div class="s-icon" style="background:#fff;padding:4px;">
  <img src="data:image/jpeg;base64,..." alt=""
       style="width:18px;height:18px;object-fit:cover;border-radius:3px;">
</div>

<!-- LinkedIn in sidebar social buttons -->
<a href="..." class="s-social" style="padding:3px;">
  <img src="data:image/jpeg;base64,..." alt=""
       style="width:26px;height:26px;object-fit:cover;border-radius:3px;">
</a>

<!-- GitHub in sidebar social buttons -->
<a href="..." class="s-social" style="padding:4px;background:#fff;">
  <img src="data:image/svg+xml;base64,..." alt=""
       style="width:22px;height:22px;object-fit:cover;border-radius:3px;">
</a>
```

---

## PDFs

### Resume

- **File:** `Shaurya_Agarwal_Resume.pdf`
- **Embedded as:** `data:application/pdf;base64,...`
- **Used in:** Download links across all three portfolios

Resume button locations:
- Warm portfolio: top nav (`.nav-resume-btn`) + Contact section (`.say-hello` area)
- Dark portfolio: top nav + Contact section
- Sidebar portfolio: tab nav bar (`.tab-resume`, top right, always visible)

### Certificate

- **File:** `Nextleap_Certificate.pdf`
- **Embedded as:** `data:application/pdf;base64,...`
- **Used in:** Education section cert card only

Certificate appears in:
- Warm portfolio — Education section, styled education card with gold border
- Dark portfolio — Education section
- Sidebar portfolio — Experience tab → Education sub-section, `.nextleap-cert` card with `✦ CERTIFIED` badge

Certificate was intentionally removed from the sidebar (`.s-resume` link in sidebar removed). It lives only in the Experience/Education tab content.

---

## Rebuilding Assets from Scratch

If the session is lost, follow this sequence:

### Step 1: Re-extract company logos from existing portfolio

```python
import re, json

with open('/mnt/user-data/outputs/shaurya-pm-portfolio.html', 'r') as f:
    content = f.read()

imgs = re.findall(r'<img[^>]+src="(data:[^"]+)"[^>]+alt="([^"]+)"', content)
logo_map = {alt.replace(' logo','').lower().replace(' ','_'): uri for uri, alt in imgs}
# logo_map keys: blinkit, inshorts, khan_academy, supercell, playo, swiggy_instamart, duolingo
```

### Step 2: Re-encode contact icons from upload files

```python
import base64

def encode(path, mime):
    with open(path, 'rb') as f:
        return f"data:{mime};base64,{base64.b64encode(f.read()).decode()}"

icons = {
    'gmail':    encode('/mnt/user-data/uploads/gmail_logo.jpg',   'image/jpeg'),
    'linkedin': encode('/mnt/user-data/uploads/linkedin_logo.jpg','image/jpeg'),
    'github':   encode('/mnt/user-data/uploads/github_logo.svg',  'image/svg+xml'),
}
```

### Step 3: Re-encode PDFs

```python
cert   = encode('/mnt/user-data/uploads/Nextleap_Certificate.pdf', 'application/pdf')
resume = encode('/mnt/user-data/uploads/Shaurya_Agarwal_Resume.pdf', 'application/pdf')
```

### Step 4: Save to /tmp/assets.json

```python
assets = {
    "logos": logo_map,
    "icons": icons,
    "cert": cert,
    "resume": resume
}
with open('/tmp/assets.json', 'w') as f:
    json.dump(assets, f)
```

---

## Additional Icons (used in warm/dark variants)

These were also uploaded and embedded:

| Asset | Usage |
|---|---|
| `phone_logo.png` | Replaces 📱 emoji in contact section |
| `resume_logo.webp` | Icon on the "Download Resume" button |

These appear in warm and dark portfolios but not in the sidebar variant (which uses emoji for phone and text-only for resume button).
