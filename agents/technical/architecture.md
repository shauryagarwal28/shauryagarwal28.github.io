# Technical Architecture

## Stack

**No framework. No build step. No dependencies.**

Everything is vanilla HTML, CSS, and JavaScript. This was a deliberate decision — see `decisions/portfolio-variant-decisions.md` for rationale.

- **HTML5** — semantic structure
- **CSS3** — custom properties (CSS variables), Grid, Flexbox, animations
- **Vanilla JS** — tab switching, card expand/collapse, filter logic, scroll reset, fade-in animations
- **Google Fonts** — loaded via CDN link tag (no self-hosting)
- **Base64 assets** — all images (logos, icons, PDFs) embedded directly in HTML

---

## File Inventory

### Portfolio pages (GitHub repo root)

```
index.html                    ← PRIMARY (renamed from shaurya-pm-portfolio.html)
portfolio-dark.html           ← Dark variant
portfolio-sidebar.html        ← Sidebar/reference variant
```

### Teardown documents

```
blinkit-teardown.html
inshorts-teardown.html
khan-academy-teardown.html
playo-teardown.html
swiggy-teardown.html
duolingo-teardown.html
supercell-teardown.html       ← 11 sections, has embedded SVG diagrams
```

### Case studies

```
blinkit-case-study.html
inshorts-case-study.html
khan-academy-case-study.html
playo-case-study.html
swiggy-instamart-case-study.html
duolingo-case-study.html
```

### Assets

```
Shaurya_Agarwal_Resume.pdf    ← Also embedded as base64 in all portfolio files
Nextleap_Certificate.pdf      ← Also embedded as base64 in all portfolio files
README.md
docs/                         ← This knowledge base
```

---

## Asset Embedding System

All images and PDFs are embedded as base64 data URIs directly inside the HTML files. This means:

- **Zero external HTTP requests** for assets (only Google Fonts CDN)
- **No broken images** if assets are moved or renamed
- **Files are large** — each portfolio file is ~780KB–1.3MB due to embedded assets

### The Asset Pipeline

A Python script in `/tmp/assets.json` stores all base64-encoded assets:

```python
# Structure of /tmp/assets.json
{
  "logos": {
    "blinkit": "data:image/jpeg;base64,...",
    "inshorts": "data:image/png;base64,...",
    "khan_academy": "data:image/jpeg;base64,...",
    "supercell": "data:image/jpeg;base64,...",
    "playo": "data:image/png;base64,...",
    "swiggy_instamart": "data:image/jpeg;base64,...",
    "duolingo": "data:image/png;base64,..."
  },
  "icons": {
    "gmail": "data:image/jpeg;base64,...",
    "linkedin": "data:image/jpeg;base64,...",
    "github": "data:image/svg+xml;base64,..."
  },
  "cert": "data:application/pdf;base64,...",
  "resume": "data:application/pdf;base64,..."
}
```

When rebuilding any portfolio file, the Python script loads this JSON, builds the HTML as a string with placeholder tokens (e.g., `LOGO_BLINKIT`, `CERT_URI`, `RESUME_URI`), then replaces all tokens with the actual base64 strings before writing to file.

**Critical:** `/tmp/assets.json` is session-scoped — it lives only in the Claude computer use session. If starting a new session, all logos must be re-extracted from existing portfolio files using regex or re-uploaded.

---

## Re-extracting Assets from Existing Files

If `/tmp/assets.json` is lost, extract logos from an existing portfolio:

```python
import re, json, base64

with open('/mnt/user-data/outputs/shaurya-pm-portfolio.html', 'r') as f:
    content = f.read()

# Extract img tags with base64 src
imgs = re.findall(r'<img[^>]+src="(data:[^"]+)"[^>]+alt="([^"]+)"', content)
logo_map = {alt.replace(' logo','').lower().replace(' ','_'): uri for uri, alt in imgs}

# Re-encode PDFs from uploads
with open('/mnt/user-data/uploads/Nextleap_Certificate.pdf', 'rb') as f:
    cert_b64 = f"data:application/pdf;base64,{base64.b64encode(f.read()).decode()}"

with open('/mnt/user-data/uploads/Shaurya_Agarwal_Resume.pdf', 'rb') as f:
    resume_b64 = f"data:application/pdf;base64,{base64.b64encode(f.read()).decode()}"
```

---

## JavaScript Architecture

### Tab switching (sidebar variant)

```javascript
function show(id, btn) {
  // Hide all sections
  document.querySelectorAll(".section").forEach(s => s.classList.remove("active"));
  // Deactivate all nav buttons
  document.querySelectorAll(".tab-btn").forEach(n => n.classList.remove("active"));
  // Show target section
  document.getElementById(id).classList.add("active");
  btn.classList.add("active");
  // Reset scroll position
  document.querySelector(".content").scrollTop = 0;
  // Trigger staggered fade-in animations
  setTimeout(() => {
    document.querySelectorAll("#" + id + " .fade-in").forEach((el, i) => {
      setTimeout(() => el.classList.add("visible"), i * 70);
    });
  }, 40);
}
```

### Card expand/collapse (all variants)

```javascript
function toggleCase(btn) {
  const card = btn.closest(".case-card");
  const body = card.querySelector(".case-body");
  const arrow = btn.querySelector(".case-arrow");
  const isOpen = body.classList.contains("open");
  body.classList.toggle("open", !isOpen);
  arrow.classList.toggle("open", !isOpen);
  btn.childNodes[0].textContent = isOpen ? "Read case study " : "Close ";
}
```

### Filter system (all variants)

```javascript
function filterCases(cat, btn) {
  document.querySelectorAll(".filter-btn").forEach(b => b.classList.remove("active"));
  btn.classList.add("active");
  document.querySelectorAll(".case-card").forEach(c => {
    c.style.display = (cat === "all" || c.dataset.cat === cat) ? "" : "none";
  });
}
```

Filter categories map to `data-cat` attributes on `.case-card` elements:
- `feature` → Blinkit, Playo
- `strategy` → Inshorts, Khan Academy, Swiggy, Duolingo
- `company` → Supercell

---

## Scroll Behaviour

- Warm and dark variants: scroll-based sections (user scrolls down through the page)
- Sidebar variant: tab-switched sections (scroll resets to top on tab change via `document.querySelector(".content").scrollTop = 0`)

---

## Performance Considerations

| Issue | Current state | Future improvement |
|---|---|---|
| File size | ~780KB–1.3MB per HTML file | Consider external asset CDN for logos |
| Font loading | Synchronous Google Fonts | Could use `font-display: swap` |
| No minification | Raw readable CSS/JS | Could minify for production |
| No lazy loading | All content in DOM on load | Tab switching hides sections but doesn't unload them |

The current approach prioritises **simplicity and zero dependencies** over performance optimisation. For a portfolio with low traffic volume, this trade-off is correct.
