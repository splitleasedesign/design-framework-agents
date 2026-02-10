# Agent 3 — Visual Design Validation (Re-check)

**File under review:** `pipeline-run-001/step-4-feels/listing-dashboard.html`
**Reference:** `agent-3-how-it-looks/Style-guide.md`
**Validator:** Agent 3 — "How it Looks"
**Date:** 2026-02-10

---

| # | Check | Result | Notes |
|---|-------|--------|-------|
| 1 | Primary purple is `#31135D` (or `var(--primary-purple)`) | **PASS** | `:root` declares `--primary-purple: #31135D;` (line 27). All usage in CSS references `var(--primary-purple)` (e.g., status-header title line 228, pricing-summary line 1031). Matches Style-guide.md exactly. |
| 2 | Secondary/CTA purple is `rgb(109, 49, 194)` (or `var(--secondary-purple)`) | **PASS** | `:root` declares `--secondary-purple: rgb(109, 49, 194);` (line 30). Used via variable throughout for buttons, links, borders, focus rings. Matches Style-guide.md. |
| 3 | Accent purple is `rgb(140, 104, 238)` (or `var(--accent-purple)`) | **PASS** | `:root` declares `--accent-purple: rgb(140, 104, 238);` (line 31). Used via `var(--accent-purple)` in hover states (e.g., link hover line 98, btn-primary:hover line 310, btn-edit:hover line 834). Matches Style-guide.md. |
| 4 | Success color is `#4B47CE` (NOT green) | **PASS** | `--success-green: #4B47CE;` and `--success-teal: #4B47CE;` (lines 36-37). Both map to the purple-blue `#4B47CE`, not an actual green. Matches Style-guide.md exactly: `--success-green: #4B47CE`. |
| 5 | Font family is Inter with system fallbacks | **PASS** | `--font-inter: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;` (line 81). Applied via `var(--font-inter)` on `body` (line 88) and `button` (line 101). Google Fonts preconnect + import on lines 7-9. Exact match with Style-guide.md. |
| 6 | Font sizes use the fixed production scale (11-36px) | **PASS** | All font-size declarations use values within the production scale: 11px, 12px, 13px, 14px, 16px, 18px, 20px. These correspond to `--text-xs` through `--text-xl` in the Style-guide. No out-of-range values found. Note: the CSS uses raw `px` values rather than the CSS variable names (e.g., `font-size: 14px` instead of `font-size: var(--text-base)`), but the values themselves are all within the defined scale. |
| 7 | Font weights use 4 levels: 400, 500, 600, 700 | **PASS** | All `font-weight` declarations across the file use exactly 400, 500, 600, or 700. No other weights (e.g., 300, 800, 900) are present. Google Fonts import loads `wght@400;500;600;700` (line 9). Matches Style-guide.md's four weight levels. |
| 8 | Button border-radius uses pill (20px) for primary/secondary buttons | **PASS** | Default `button` uses `border-radius: var(--rounded-pill)` (line 107). `.btn-primary` uses `border-radius: var(--rounded-pill)` (line 305). `.btn-secondary-outline` inherits the default button pill radius. `.btn-edit` uses `border-radius: var(--rounded-pill)` (line 825). `.btn-sidebar` uses `border-radius: var(--rounded-pill)` (line 676). `--rounded-pill: 20px` (line 74). All correct. |
| 9 | Card border-radius uses 12px (`--rounded-xl`) | **PASS** | `.status-header` uses `border-radius: var(--rounded-xl)` (line 209). `.completion-tracker` uses `var(--rounded-xl)` (line 401). `.summary-card` uses `var(--rounded-xl)` (line 578). `.section-group` uses `var(--rounded-xl)` (line 700). `.sidebar-promo` uses `var(--rounded-xl)` (line 640). `--rounded-xl: 12px` (line 73). All cards consistently use the correct token. |
| 10 | Shadows match production values (not AI-invented multi-layer) | **FAIL** | The `:root` shadow variables match the Style-guide exactly (`--shadow-sm`, `--shadow-md`, `--shadow-lg`, `--shadow-purple-md`, `--shadow-purple-lg`). However, `.btn-primary` on line 306 uses a hardcoded inline shadow `box-shadow: 0 2px 4px rgba(109, 49, 194, 0.25);` which does not correspond to any production shadow variable. The Style-guide defines `--shadow-purple-sm: 0 2px 4px rgba(49, 19, 93, 0.2)` — similar structure but different rgba values. This is an AI-invented shadow not present in the style guide's token list. |
| 11 | Gradient uses production values (135deg, #31135D to #5a2d8f) | **PASS** | `--gradient-purple-primary: linear-gradient(135deg, #31135D 0%, #5a2d8f 100%);` (line 61). Applied to `.global-header` via `var(--gradient-purple-primary)` (line 126). Matches Style-guide.md exactly. |
| 12 | All color values use CSS custom properties (no hardcoded hex outside `:root`) | **FAIL** | Several hardcoded color values appear outside `:root`: (a) `button:hover` uses `border-color: #d1d5db` (line 117) — not a defined variable. (b) `color: #fff` appears in multiple places outside `:root` (lines 138, 145, 166, 301, 313, 345, 551, 678) — should use `var(--bg-white)` or a `--white` variable. (c) `.btn-primary` uses a hardcoded `box-shadow: 0 2px 4px rgba(109, 49, 194, 0.25)` (line 306). (d) SVG logo stroke uses `stroke="#fff"` (line 1215). While `#fff` is arguably a universal constant, the `#d1d5db` border-color and the inline shadow are clear violations of the "no hardcoded hex outside :root" rule. |
| 13 | Focus states use `focus-visible` with secondary-purple ring | **PASS** | Global `:focus-visible` rule at line 1128-1131: `outline: 2px solid var(--secondary-purple); outline-offset: 2px;`. Button-specific `button:focus-visible` at lines 119-122 also uses `outline: 2px solid var(--secondary-purple); outline-offset: 2px;`. Matches Style-guide.md's accessibility requirements exactly. |
| 14 | `prefers-reduced-motion` media query exists | **PASS** | Present at lines 1133-1144. Applies `animation-duration: 0.01ms !important`, `animation-iteration-count: 1 !important`, `transition-duration: 0.01ms !important` to all elements. Also specifically disables the progress bar shimmer animation. Matches Style-guide.md's recommended pattern. |
| 15 | Icons are consistently sized (Feather-style SVG) | **PASS** | All inline SVGs use the Feather icon pattern: `viewBox="0 0 24 24"`, `fill="none"`, `stroke="currentColor"`, `stroke-width="2"`, `stroke-linecap="round"`, `stroke-linejoin="round"`. Sizes follow a consistent hierarchy: 12px (badge icons), 14px (action/edit icons, inline small), 16px (section labels, navigation, sidebar), 18px (section titles, card headers). One exception: the logo SVG (28x28) uses a custom viewBox but this is expected for a logo mark. Badge SVGs use `stroke-width="2.5"` for optical weight at small size, which is a reasonable Feather adaptation. |
| 16 | Letter-spacing uses 0.5px for uppercase labels | **FAIL** | Most uppercase labels correctly use `letter-spacing: 0.5px` (`.status-badge` line 262, `.summary-card__title` line 589, `.summary-card__section-title` line 625, `.section-card__badge` line 771, `.data-table th` line 937). However, `.section-group__label` on line 714 uses `letter-spacing: 1px` instead of 0.5px. The Style-guide specifies `--letter-spacing-small: 0.5px` for "slightly expanded" and `--letter-spacing-medium: 0.05em` for "uppercase labels". The 1px value does not appear in the Style-guide's letter-spacing tokens at all. Additionally, `.global-header__logo` uses `letter-spacing: -0.3px` (line 141) which is also not a defined token, though negative tracking on a logo wordmark is a common typographic practice. |
| 17 | Line heights use 1.2 (tight) and 1.5 (normal) appropriately | **PASS** | `body` uses `line-height: 1.5` (line 90) for default text. `.status-header__title` uses `line-height: 1.2` (line 229) for the heading. `.status-header__subtitle` uses `line-height: 1.5` (line 238). `.completion-tracker__hint` uses `line-height: 1.5` (line 441). `.section-card__content` uses `line-height: 1.6` (line 796), which maps to `--line-height-relaxed` in the Style-guide. `.empty-state__hint` uses `line-height: 1.6` (line 864). All values map to defined Style-guide tokens (1.2 = tight, 1.5 = normal, 1.6 = relaxed). |
| 18 | Border colors use `var(--border-color)` or `var(--border-light)` | **FAIL** | Most borders correctly use `var(--border-color)` or `var(--border-light)`. However, `button:hover` on line 117 uses the hardcoded `border-color: #d1d5db` which is not a defined CSS variable. This should use one of the border variables from the Style-guide. All other border-color instances use CSS custom properties correctly. |
| 19 | Interactive elements have min-height >= 44px on mobile (touch targets) | **PASS** | The `@media (max-width: 600px)` block (lines 1147-1202) sets `min-height: 44px` on: `.global-header__nav a` (line 1183), `.breadcrumb a` (line 1188), `.btn-edit` (line 1191), `.disclosure__trigger` (line 1194), `.sidebar-promo .btn-sidebar` (line 1197), `.calendar-controls button` (line 1200). The primary/secondary action buttons in `.status-header__actions` get `flex: 1` with `justify-content: center`, and their default padding (10px 24px for btn-primary, 8px 16px for default button) provides adequate height. Note: The Style-guide recommends 48px min touch targets (`--input-height-lg: 48px`), while the implementation uses 44px (WCAG 2.1 AA minimum). This is acceptable per WCAG standards but does not match the Style-guide's stricter 48px recommendation. Passing as 44px meets the checklist requirement. |
| 20 | Transitions use the production durations (0.1s/0.2s/0.3s) | **FAIL** | Most transitions correctly use `var(--transition-fast)` (0.1s), `var(--transition-base)` (0.2s), or `var(--transition-slow)` (0.3s). However, `.progress-bar__fill` on line 463 uses a hardcoded `transition: width 0.4s ease;`. While 0.4s exists as `--transition-slower` in the Style-guide, the code does not reference the CSS variable — it uses a raw `0.4s` value. For strict compliance with the token system, this should be `var(--transition-slower)`. All other transitions in the file correctly use CSS custom property references. |

---

## Summary of Failures

### FAIL #10 — Hardcoded shadow on `.btn-primary`
- **Line 306:** `box-shadow: 0 2px 4px rgba(109, 49, 194, 0.25);`
- **Issue:** This shadow value is not defined in the Style-guide's shadow tokens. The closest match is `--shadow-purple-sm: 0 2px 4px rgba(49, 19, 93, 0.2)` which uses a different rgba color and opacity.
- **Fix:** Define a new token or use `var(--shadow-purple-sm)`.

### FAIL #12 — Hardcoded hex values outside `:root`
- **Line 117:** `border-color: #d1d5db` — not a CSS variable.
- **Lines 138, 145, 166, 301, 313, 345, 551, 678:** `color: #fff` — should use `var(--bg-white)` or define a `--white` variable.
- **Line 306:** Inline `box-shadow` with hardcoded rgba.
- **Fix:** Replace all with CSS custom property references.

### FAIL #16 — Inconsistent letter-spacing
- **Line 714:** `.section-group__label` uses `letter-spacing: 1px` instead of the Style-guide's 0.5px token.
- **Fix:** Change to `letter-spacing: 0.5px` or `var(--letter-spacing-small)`.

### FAIL #18 — Hardcoded border color
- **Line 117:** `button:hover` uses `border-color: #d1d5db` instead of a CSS variable.
- **Fix:** Replace with a defined border variable or add `#d1d5db` to `:root`.

### FAIL #20 — Hardcoded transition duration
- **Line 463:** `.progress-bar__fill` uses `transition: width 0.4s ease` instead of `var(--transition-slower)`.
- **Fix:** Replace `0.4s` with `var(--transition-slower)`.

---

**Score: 15/20**

**Verdict: FAIL**

The page demonstrates strong overall adherence to the Split Lease design system. The core color palette, typography scale, border-radius tokens, gradient values, focus states, reduced-motion support, icon consistency, and mobile touch targets are all correctly implemented. The five failures are all related to token discipline — hardcoded values that should reference CSS custom properties — rather than fundamental design system violations. These are straightforward to remediate.

---

*Validated by Agent 3 — "How it Looks" | 2026-02-10*
