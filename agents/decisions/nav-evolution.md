# Nav Evolution

## History of Navigation Decisions

### Phase 1: Warm + Dark portfolios — Scroll-based nav

Both the warm and dark portfolios use a traditional fixed top nav bar with anchor links that scroll to sections. This was the original design and was never iterated on — it works well for single-page scrolling portfolios.

```
[Logo] [About] [Experience] [Work] [Skills] [Contact] [Say hello ✉]
```

Later, a Resume button was added to the right end:

```
[Logo] [About] [Experience] [Work] [Skills] [Contact] [📄 Resume] [Say hello ✉]
```

**Status:** Stable. No further changes planned.

---

### Phase 2: Sidebar portfolio — Initial attempt (tabs at bottom of sidebar)

When the sidebar variant was first built, the navigation was placed at the bottom of the sidebar using `margin-top: auto` to push it down.

**Problem:** The nav appeared below the fold on most screens. Users scrolling the sidebar to find navigation would see contact info first, then have to scroll down to find the nav.

**User feedback:** "The nav tabs are in the bottom corner, make it more visible and on the upper side like it's in the reference portfolio."

**Fix:** Moved nav to the top of the sidebar, immediately below the availability badge. Styled as a boxed component with `border: 1px solid var(--border)` and active state with `border-left: 3px solid var(--accent)`.

---

### Phase 3: Sidebar variant — Tabs in sidebar (still wrong)

After moving the nav to the top of the sidebar, it matched the request "upper side" — but not the reference portfolio structure.

**Problem:** The reference portfolio (rakeshks2k.github.io/portfolio/) doesn't have tabs in the sidebar at all. The sidebar contains only identity/contact info. The tabs are inside the right panel, at the very top.

**User action:** Shared a screenshot of the reference portfolio.

**Analysis of screenshot:**
- Left side: Sidebar with photo, name, role pill, email, phone, birthday, location, social icons
- Right side: Panel with tab nav AT THE TOP (About, Experience, Case Studies, Certifications, Contact), and content below the tabs

**Fix:** Complete structural rebuild. Removed all nav from sidebar. Added `.tab-nav` as the first element inside `.panel` (the right-side content area). Tab nav spans the full width of the panel with a `border-bottom`.

---

### Phase 4: Sidebar variant — Resume in tab nav

**Decision:** Resume button added as last item in tab nav, `margin-left: auto` to push it to the right edge.

```
[About] [Experience] [Case Studies] [Skills] [Contact]        [📄 Resume]
```

This gives the Resume button permanent visibility regardless of which tab is active — better than burying it in the Contact section.

**User feedback:** "Give me a 'Resume' button on top of the page"

**Implementation:** Added `.tab-resume` class to the link element, with specific CSS to separate it from the tab buttons visually (solid background vs transparent).

---

### Phase 5: Remove Resume from sidebar

**User feedback:** "Remove the resume from the sidebar and let it be on the top"

**Context:** At this point, the Resume link existed in BOTH the sidebar (as `.s-resume`) AND the tab nav. User wanted it only in the tab nav.

**Fix:** Removed `<a class="s-resume">Download Resume</a>` from the sidebar HTML. The `.s-resume` CSS class remains defined but is no longer used.

---

## Final Nav State Summary

### Warm (index.html)
```
Fixed top bar: [Logo] ← [About] [Experience] [Work] [Skills] [Contact] → [📄 Resume] [Say hello ✉]
```

### Dark (portfolio-dark.html)
```
Fixed top bar: [Logo] ← [About] [Experience] [Work] [Skills] [Contact] → [📄 Resume] [Say hello ✉]
```

### Sidebar (portfolio-sidebar.html)
```
Sidebar: [Avatar] [Name] [Role] [● Open to opportunities]
         [Divider]
         [✉ email] [📱 phone] [📍 location]
         [Divider]
         [💼 LinkedIn] [🐙 GitHub]

Tab nav inside right panel:
[About] [Experience] [Case Studies] [Skills] [Contact]     [📄 Resume]
                                                         ↑ margin-left:auto
```
