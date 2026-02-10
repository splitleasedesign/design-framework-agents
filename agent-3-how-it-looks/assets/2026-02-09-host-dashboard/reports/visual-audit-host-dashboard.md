# Visual Audit: Host Overview Dashboard
**Date:** 2026-02-09
**Source:** `improved-host-overview-dashboard--don-norman.html`
**Auditor:** Agent 3 (How it Looks)

---

## 1. Colors Found (Catalog)

| Token in Original | Hex / Value | Where Used | Issue |
|---|---|---|---|
| `--color-primary` | `#31135D` | Header bg, primary buttons, proposal badge | Different from brand spec (#2D1B69) |
| `--color-primary-dark` | `#23083D` | Button hover | OK but not in spec |
| `--color-primary-light` | `#7B4FB5` | Avatar bg, mini-stat values | Purple on stat values = purple overload (Anti-Pattern #2) |
| `--color-primary-bg` | `#ECE8F7` | Button hover bg, listing image gradient | OK |
| `--color-success` | `#00C853` | Earnings bar, stat change, online badge text, onboarding step | Too vivid; fails WCAG on white (3.0:1) |
| `--color-success-bg` | `#E8F5E9` | Online badge bg, design note bg | OK |
| `--color-warning` | `#FFC107` | Proposals bar, action-banner border, action icon bg | Yellow; fails WCAG on white (1.3:1 for text) |
| `--color-warning-bg` | `#FFF8E1` | Action banner gradient start | OK |
| `--color-error` | `#D32F2F` | Declared but not used in mockup | OK |
| `--color-neutral-100` | `#F0F0F0` | Page background | Slightly warm gray |
| `--color-neutral-200` | `#E0E0E0` | Borders, dividers, offline badge bg | OK |
| `--color-neutral-600` | `#666666` | Secondary text (descriptions, metadata) | Only 1 gray for all secondary text = flat hierarchy |
| `--color-neutral-900` | `#1A1A1A` | Headings, stat values, body text | OK |
| `--color-white` | `#FFFFFF` | Card backgrounds | OK |
| Hardcoded `#FFF3CD` | `#FFF3CD` | Action banner gradient end | Not tokenized |
| Hardcoded `white` | keyword | Multiple locations | Not tokenized as var() |
| Hardcoded `rgba(255,255,255,0.2)` | — | Onboarding step bg, dismiss btn | Not tokenized |
| Hardcoded `rgba(0,200,83,0.3)` | — | Completed step bg | Not tokenized |

### Issues Found:
1. **#00C853 (success green)** fails WCAG AA on white background: 3.0:1 ratio (needs 4.5:1).
2. **#FFC107 (warning yellow)** is never used as text color, but the action-icon `!` is on yellow bg — needs checking.
3. **#666666** is used for ALL secondary text — timestamps, locations, descriptions, stat labels. No 5-level hierarchy.
4. **Purple on mini-stat values** — prices display in `--color-primary` (#31135D). Should be near-black per taste model.
5. **Multiple hardcoded color values** not referenced through tokens: `white`, `#FFF3CD`, `rgba(...)` values.

---

## 2. Font Sizes Found

| Size | Where Used | Token Equivalent |
|---|---|---|
| `40px` | Stat value (.stat-value) | --font-size-3xl |
| `28px` | Welcome heading (h1) | --font-size-2xl |
| `20px` | Logo, action icon | --font-size-xl |
| `18px` | Section title, onboarding title, mini-stat value, dismiss btn, step icon | --font-size-xl |
| `16px` | Listing title | --font-size-lg |
| `14px` | Header nav, welcome subtext, stat label, action text, progress text, next-step hint, btn, listings count | --font-size-base / --font-size-md |
| `13px` | See-all link, stat change, action subtext, step label, listing location, listing btn, listing actions | --font-size-sm |
| `12px` | Proposal badge, design note | --font-size-xs |
| `11px` | Listing status, mini-stat label | --font-size-xs |

### Issues Found:
1. **8 distinct font sizes** — not on a consistent mathematical scale.
2. **18px used for 4 different purposes** (section title, onboarding title, mini-stat value, step icon) — these should differentiate.
3. **No clamp() usage** — sizes are fixed px, no fluid scaling.
4. **No letter-spacing** on 28px or 40px headings. Large headings look loose.
5. **Line-height 1.5 globally** — headings at 28px/40px have excessive line-height.

---

## 3. Font Weights Found

| Weight | Where Used |
|---|---|
| `700` | Logo, welcome h1, stat value, section title, mini-stat value, listing title |
| `600` | Avatar, btn, listing status, proposal badge, onboarding title |
| `500` | Step label |
| Unset (400) | Body text, labels, metadata |

### Issues Found:
1. **4 weights used** (400, 500, 600, 700) — taste model spec is 3 (400, 500, 600). Weight 700 should be 600.

---

## 4. Spacing Values Found

| Value | Where Used |
|---|---|
| `4px` | Margin-bottom (h1→p, stat-value→change, listing-title→location) |
| `8px` | Logo gap, btn gap, listing-actions gap, step-icon margin-bottom, onboarding-step radius |
| `10px` | Listing-status padding, listing-actions btn padding |
| `12px` | Action-buttons gap, stat-header mb, onboarding steps gap, listing-location mb, mini-stats padding, listing-actions btn padding, mini-stats mb, next-step-hint padding, listing-content gap, listing-status top/right |
| `16px` | Header padding-y, content padding, onboarding steps padding, onboarding header mb, steps mb |
| `20px` | Stats grid gap, btn padding-x, action-banner padding-x, listings grid gap, section-header mb |
| `24px` | Header padding-x, main padding-x, stat-card padding, onboarding padding, section padding, onboarding margin-bottom, section margin-bottom, header-nav gap |
| `32px` | Main padding-top, welcome-section mb, stats-dashboard mb, action-banner mb |
| `40px` | Design note padding, design note margin-top |

### Issues Found:
1. **10px appears** — not a multiple of 4. Needs to be 8px or 12px.
2. **No 48px section spacing** — sections use 32px (should be 48px per three-tier system).
3. **Spacing is mostly good** (4/8/12/16/20/24/32/40) but inconsistent with the prescribed three-tier system.
4. **20px appears frequently** — should be eliminated or mapped to a token.

---

## 5. Border Radius Values Found

| Value | Where Used |
|---|---|
| `50%` | Avatar, action icon, dismiss btn, step icon, spinner |
| `20px` | Listing status pill |
| `16px` | `--radius-lg` — onboarding section |
| `12px` | `--radius-md` — stat card, action banner, listing card |
| `10px` | Proposal badge |
| `8px` | Btn, onboarding step, next-step-hint |

### Issues Found:
1. **Descending hierarchy partially present** but inconsistent: cards use 12px, buttons use 8px (good), but listing status pill uses 20px and badges use 10px.
2. **Proposal badge at 10px** — should use badge radius (6px per spec).
3. **Listing status at 20px** — should use --radius-full (9999px) for pill shape or 6px for badge.

---

## 6. Shadows Found

| Value | Where Used |
|---|---|
| `0 4px 6px -1px rgba(0,0,0,0.1)` | `--shadow-md` — stat cards, sections |
| `0 10px 15px -3px rgba(0,0,0,0.1)` | `--shadow-lg` — listing card hover |

### Issues Found:
1. **Single-layer shadows** — both are 1 layer. Premium needs 2-3 layers per shadow (Anti-Pattern #3).
2. **Shadow-md is too strong** — 0.1 opacity is heavy; premium uses 0.03-0.06.
3. **No shadow-sm** defined for cards at rest.
4. **No inset shadow** for form inputs.
5. **Listing card uses border AND hover shadow** — exceeds 2-treatment max on hover.

---

## 7. Transitions Found

| Value | Where Used |
|---|---|
| `all 0.2s` | Buttons, listing card, onboarding step |

### Issues Found:
1. **All transitions use same value** (`all 0.2s`) — no asymmetric timing.
2. **No easing function specified** (defaults to `ease`, should be `ease-out` for entry).
3. **`transition: all`** transitions everything including layout — should be specific properties.

---

## Summary of Critical Issues

| Priority | Issue | Taste Test Questions Affected |
|---|---|---|
| P0 | Success green (#00C853) fails WCAG AA on white: 3.0:1 | Q18, Q6 |
| P0 | Only 1 gray for all secondary text (no 5-level hierarchy) | Q14 |
| P0 | Purple on mini-stat values (purple overload) | Q6, Q22 |
| P1 | Single-layer shadows (cheap feel) | Q23 |
| P1 | 4 font weights instead of 3 | Q13 |
| P1 | No letter-spacing on large headings | Q16 |
| P1 | Heading line-height same as body (1.5) | Q15 |
| P2 | Multiple hardcoded colors not tokenized | — |
| P2 | 10px spacing (not multiple of 4) | Q7 |
| P2 | No 48px section breaks | Q9 |
| P2 | No tabular numerals on prices/metrics | Q17 |
