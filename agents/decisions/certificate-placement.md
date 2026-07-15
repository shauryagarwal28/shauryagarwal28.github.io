# Certificate Placement

## The Nextleap PM Fellowship Certificate

The Nextleap PM Fellowship certificate is a key credential — it's the formal PM training that bridges the gap between BA experience and PM roles. Its placement in the portfolio directly affects how much hiring managers notice it.

---

## Placement History

### Initial state (warm + dark portfolios)

The certificate appeared in the Education section as a styled card, embedded as base64 with a download link. This is the appropriate location — it's an educational credential.

### Sidebar variant — First attempt (certificate in sidebar)

When the sidebar variant was first built, a certificate card was added to the sidebar:

```html
<!-- In sidebar -->
<div class="cert-card">
  <div class="cert-card-header">
    <div class="cert-icon-box">🏅</div>
    <div>
      <div class="cert-title">PM Fellowship</div>
      <div class="cert-issuer">Nextleap</div>
    </div>
  </div>
  <div class="cert-meta">Oct 4 - Dec 14, 2025 · Certified</div>
  <a href="CERT_URI" download="..." class="cert-dl">📄 Download Certificate</a>
</div>
```

**Reasoning at the time:** Make the certificate prominent on the sidebar so it's always visible.

**User feedback:** "Don't highlight the certificate on homepage, highlight it in its section."

**Problem identified:** The sidebar is the "identity" column — it should contain contact details and quick-reference info, not credentials. A certificate download button in the sidebar feels out of place and clutters the contact information. The certificate is content, not contact info.

### Sidebar variant — Final state (certificate in Experience section only)

**Fix:** Removed certificate card from sidebar entirely. The cert now lives only in the Experience → Education sub-section, as a styled `.cert-card` with:

- `border: 1.5px solid rgba(224,123,57,0.5)` — stronger accent border than standard edu cards
- `background: linear-gradient(...)` — subtle gold gradient background
- `✦ CERTIFIED` badge — `position: absolute; top: 12px; right: 12px;` — a small pill in the top-right corner
- `📄 Download Certificate` button — gold accent button at the bottom of the card

```html
<!-- In Experience tab → Education grid -->
<div class="cert-card">
  <div class="cert-badge">✦ CERTIFIED</div>
  <div class="edu-type">📋 Fellowship</div>
  <div class="edu-inst">Nextleap PM Fellowship</div>
  <div class="edu-deg">Product Management</div>
  <div class="edu-score">✓ Oct - Dec 2025</div>
  <div class="edu-desc">
    8-week intensive covering discovery, user research, ideation, wireframing, and PRD writing.
    Signed by Arindam Mukherjee, Co-founder and CEO, Nextleap.
  </div>
  <a href="CERT_URI" download="..." class="cert-dl">📄 Download Certificate</a>
</div>
```

---

## Final Placement — All Three Variants

| Portfolio | Certificate location |
|---|---|
| Warm (index.html) | Education section — styled card with gold border + download button |
| Dark (portfolio-dark.html) | Education section — styled card with gold border + download button |
| Sidebar (portfolio-sidebar.html) | Experience tab → Education grid — `.cert-card` with `✦ CERTIFIED` badge + download button |

**The certificate does NOT appear in:**
- Sidebar column (removed after user feedback)
- Hero section
- About section
- Contact section
- Nav bar

---

## Certificate Card Design Rationale

The cert card is visually distinct from other education cards because it carries more weight as a credential:

| Element | Standard edu card | Cert card |
|---|---|---|
| Border | `1px solid var(--border)` | `1.5px solid rgba(accent,0.5)` |
| Background | `var(--surface2)` | Gradient with accent |
| Badge | None | `✦ CERTIFIED` pill, top-right |
| CTA | None | `📄 Download Certificate` button |
| Score colour | Green | Same green |

This visual distinction signals to the viewer that this credential is different from a degree — it's a recent, specific, PM-focused qualification.
