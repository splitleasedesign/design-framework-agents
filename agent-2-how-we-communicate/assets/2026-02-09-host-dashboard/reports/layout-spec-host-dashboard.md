# Layout Spec: Host Overview Dashboard
**Agent 2 -- How We Communicate Information**
**Date:** 2026-02-09
**Page:** Host Overview Dashboard (Split Lease)

---

## Layout Pattern Selections

### 1. Overall Page Structure

**Pattern:** Single-column content flow with max-width container
**Rationale:** Host dashboard is a scan-and-act page, not a browse page. Single-column ensures top-to-bottom scan order matches information priority. No sidebar needed -- all content is primary.

```
Container: max-width: 1200px; margin: 0 auto;
Padding:   clamp(16px, 4vw, 32px)
```

**Responsive behavior:**
- All viewports: Single-column flow, content fills container
- Container padding scales from 16px (320px) to 32px (800px+)
- No layout columns at any viewport (contrast with listing detail which has sidebar)

---

### 2. Header

**Pattern:** Flex row with logo left, nav right
**Based on:** RESPONSIVE-DESIGN-MODEL Pattern 17 (Priority+ Navigation)

```
Layout:    display: flex; justify-content: space-between; align-items: center;
Height:    clamp(56px, auto, 64px)
Padding:   clamp(12px, 2vw, 16px) clamp(16px, 4vw, 24px)
```

**Responsive behavior:**
| Viewport | Behavior |
|---|---|
| >= 768px | Logo left, nav links visible, avatar right |
| < 768px | Logo left, hamburger menu button right, nav links hidden in off-canvas menu |

**Touch targets:** Nav links get `min-height: 44px` with padding. Hamburger button: 44x44px.

---

### 3. Welcome Section

**Pattern:** Flex row with text left, buttons right; wraps on narrow
**Rationale:** Welcome is P2 (contextual, not data-rich). Buttons are infrequent-use actions. Row layout gives them space without pushing content down.

```
Layout:     display: flex; justify-content: space-between; align-items: flex-start;
            flex-wrap: wrap; gap: clamp(12px, 2vw, 16px);
Margin-bottom: clamp(24px, 4vw, 32px)
```

**Responsive behavior:**
| Viewport | Behavior |
|---|---|
| >= 600px | Text left, buttons right (same row) |
| < 600px | Text full-width, buttons wrap below full-width. Each button min-height: 44px |

**Typography:**
- h1: `clamp(22px, 3vw, 28px)`, weight 700
- Subtitle: 14px, color `#666`

---

### 4. KPI Stats Dashboard

**Pattern:** Auto-fill grid (RESPONSIVE-DESIGN-MODEL Pattern 2 + Pattern 12)
**Rationale:** 2 primary KPIs (earnings + proposals). Grid lets them sit side-by-side on desktop, stack on mobile. Auto-fill handles tablet gracefully.

```
Layout:     display: grid;
            grid-template-columns: repeat(auto-fill, minmax(min(100%, 280px), 1fr));
            gap: clamp(12px, 2vw, 20px);
Margin-bottom: clamp(24px, 4vw, 32px)
```

**Responsive behavior:**
| Viewport | Columns | Card behavior |
|---|---|---|
| >= 600px | 2 columns | Side by side, equal width |
| < 600px | 1 column | Full-width stacked |

**Stat card internals:**
- Padding: `clamp(16px, 3vw, 24px)`
- Metric value: `clamp(28px, 5vw, 40px)`, weight 700
- Label: 14px, color `#666`
- Change text: 13px
- Left border accent: 4px (success green for earnings, warning yellow for proposals)
- Border-radius: 12px
- Shadow: `0 4px 6px -1px rgba(0,0,0,0.1)`

---

### 5. Action Banner

**Pattern:** Full-width flex row with icon + text + CTA; wraps on narrow
**Rationale:** Urgent item needs full visual width to grab attention. On mobile, CTA wraps below text to maintain touch target size.

```
Layout:     display: flex; align-items: center; justify-content: space-between;
            flex-wrap: wrap; gap: clamp(12px, 2vw, 16px);
Padding:    clamp(12px, 2vw, 16px) clamp(16px, 3vw, 20px)
Margin-bottom: clamp(24px, 4vw, 32px)
Background: linear-gradient(135deg, #FFF8E1 0%, #FFF3CD 100%)
Border:     1px solid #FFC107
Radius:     12px
```

**Responsive behavior:**
| Viewport | Behavior |
|---|---|
| >= 600px | Icon + text left, CTA button right (same row) |
| < 600px | Content group full-width, CTA button full-width below. Button: width 100%, min-height 44px |

**Action icon:** 40px circle, `#FFC107` background, centered `!` glyph.
**CTA button:** Primary style, min-width 140px, min-height 44px on mobile.

---

### 6. Onboarding Section

**Pattern:** Horizontal steps on desktop, vertical list on mobile
**Based on:** RESPONSIVE-DESIGN-MODEL Pattern 10 (Column Drop) + custom stepper

```
Container:  background: linear-gradient(135deg, #31135D, #23083D);
            border-radius: 16px; padding: clamp(16px, 3vw, 24px);
            position: relative; color: white;
Margin-bottom: clamp(16px, 3vw, 24px)
```

**Steps container:**
```
Desktop:    display: flex; gap: 12px;             (horizontal)
Mobile:     display: grid; grid-template-columns: 1fr; gap: 8px;  (vertical stack)
```

**Responsive behavior:**
| Viewport | Behavior |
|---|---|
| >= 768px | Steps horizontal (5 across), flex: 1 each. Icons centered above labels. |
| < 768px | Steps vertical (stacked). Each step: flex row (icon left, label right). Full width. |

**Step card:**
- Background: `rgba(255,255,255,0.15)`, border-radius 8px
- Padding: `clamp(12px, 2vw, 16px)`
- Completed: `rgba(0,200,83,0.3)` background, green checkmark icon
- Touch target: min-height 44px on mobile

**Dismiss button:** Absolute positioned top-right, 32px circle (44px tap target with padding), `rgba(255,255,255,0.2)` bg.

**Next step hint:** Background `rgba(255,255,255,0.1)`, padding 12px 16px, border-radius 8px, 14px text.

---

### 7. Listings Grid

**Pattern:** Auto-fill grid (RESPONSIVE-DESIGN-MODEL Pattern 2)
**Based on:** Card min-width 320px for listing cards, stacking on narrow.

```
Section:    background: white; border-radius: 16px;
            padding: clamp(16px, 3vw, 24px);
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1);

Grid:       display: grid;
            grid-template-columns: repeat(auto-fill, minmax(min(100%, 300px), 1fr));
            gap: clamp(12px, 2vw, 20px);
```

**Responsive behavior:**
| Viewport | Columns | Card behavior |
|---|---|---|
| >= 1024px | 3 columns | Full card layout |
| 768-1023px | 2 columns | Full card layout |
| < 768px | 1 column | Full-width stacked cards |

---

### 8. Listing Card

**Pattern:** Vertical card (image top, content bottom) at all viewports
**Based on:** RESPONSIVE-DESIGN-MODEL Pattern 7 (Stack-on-Narrow) + Pattern 4 (Aspect-Ratio)

```
Container:  border: 1px solid #E0E0E0; border-radius: 12px; overflow: hidden;
            transition: box-shadow 0.2s, transform 0.2s;

Image:      width: 100%; aspect-ratio: 16/9; object-fit: cover;
            background: linear-gradient(135deg, #ECE8F7, #E0E0E0);

Content:    padding: clamp(12px, 2vw, 16px);
```

**Card internals:**
- **Status badge:** Absolute positioned on image, top-right. Pill shape (border-radius 20px), padding 4px 10px, 11px uppercase text with icon SVG.
- **Title:** `clamp(15px, 1.8vw, 16px)`, weight 600, max 2 lines with `-webkit-line-clamp: 2`.
- **Location:** 13px, color `#666`, margin-bottom 12px.
- **Mini-stats row:** Flex row, 3 equal columns, bordered top and bottom. Value: 18px weight 700 primary color. Label: 11px uppercase `#666`.
- **Actions row:** Flex row, 2 buttons, `flex: 1` each, gap 8px. Min-height 44px. Primary + Secondary styles.

**Hover:** `box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1); transform: translateY(-2px);`
**Hover disabled on touch:** `@media (hover: none) { .listing-card:hover { transform: none; box-shadow: none; } }`

---

## Breakpoint Strategy

Aligned with RESPONSIVE-DESIGN-MODEL Appendix A:

| Breakpoint | Device class | Key layout changes |
|---|---|---|
| 320px | Small phone floor | Single-column everything, compressed padding, 28px stat values |
| 375px | Standard phone | Same as 320 but more breathing room |
| 428px | Large phone | Same as 375 |
| 600px | Small tablet / landscape phone | Stats go 2-col, welcome buttons stay beside text, banner keeps row layout |
| 768px | Tablet portrait | Onboarding steps go horizontal, listing grid 2-col, nav links visible |
| 1024px | Tablet landscape | Listing grid 3-col |
| 1280px | Laptop | Max container widths apply |
| 1440px | Desktop | Design ceiling, all clamp() values at max |

**Fluid values handle most transitions.** Only 2 explicit media queries needed:
1. `@media (max-width: 767px)` -- Mobile adaptations (hamburger nav, vertical onboarding, banner wrap)
2. `@media (max-width: 599px)` -- Small mobile (welcome section stacks, action banner CTA full-width)

Everything else is handled by `clamp()`, `auto-fill`, and `flex-wrap`.

---

## Touch Target Compliance

| Element | Visual size | Tap target | Method |
|---|---|---|---|
| Nav links | 14px text | 44px height | `min-height: 44px; display: flex; align-items: center;` |
| Hamburger button | 24px icon | 44x44px | `width: 44px; height: 44px; padding: 10px;` |
| Create Listing btn | Auto | >= 44px | `min-height: 44px; padding: 12px 20px;` |
| Import Listing btn | Auto | >= 44px | `min-height: 44px; padding: 12px 20px;` |
| Review Proposals btn | Auto | >= 44px | `min-height: 44px;` |
| Dismiss onboarding (X) | 32px visual | 44px | Absolute area extends to 44px via padding |
| Onboarding steps | Full step card | >= 44px | `min-height: 44px;` |
| Manage button (card) | Auto | >= 44px | `min-height: 44px;` |
| Proposals button (card) | Auto | >= 44px | `min-height: 44px;` |
| See all stats link | 13px text | 44px | `min-height: 44px; display: inline-flex; align-items: center;` |

---

## Spacing Scale

All spacing uses the 4px base grid via clamp():

| Token | Value | Resolves at 320px | Resolves at 1440px |
|---|---|---|---|
| `--space-xs` | `clamp(4px, 0.5vw, 8px)` | 4px | 7.2px -> 8px |
| `--space-sm` | `clamp(8px, 1vw, 12px)` | 8px | 12px |
| `--space-md` | `clamp(12px, 2vw, 20px)` | 12px | 20px |
| `--space-lg` | `clamp(16px, 3vw, 24px)` | 16px | 24px |
| `--space-xl` | `clamp(24px, 4vw, 32px)` | 24px | 32px |
| `--space-2xl` | `clamp(32px, 6vw, 48px)` | 32px | 48px |

---

## Accessibility Notes

- **Color contrast:** All text meets WCAG AA (4.5:1 for body, 3:1 for large text).
- **Status badges:** Use icon + color + text (not color alone) per WCAG 1.4.1.
- **Focus indicators:** All interactive elements have visible focus ring (outline: 2px solid #31135D, offset 2px).
- **Reduced motion:** `@media (prefers-reduced-motion: reduce)` disables transitions and animations.
- **Semantic HTML:** header, main, nav, section, h1-h3, button elements used appropriately.
- **ARIA:** Dismiss button has `aria-label`. Status badges convey meaning via text, not just icon.
