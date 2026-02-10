# Agent 3 (How it Looks) — Memory

## Session Log

- [2026-02-09] host-dashboard-token-system | outcome: Success | eval: 28/30 + WCAG AA PASS | retries: 0 | files: css/color-tokens.css, css/typography-tokens.css, css/spacing-tokens.css, css/component-tokens.css, css/visual-system.css, reports/visual-audit-host-dashboard.md, reports/taste-test-score.md, reports/color-system.md, reports/wcag-audit.md, host-dashboard.html | tokens: 10 color + 8 type-size + 3 weight + 3 line-height + 12 spacing + 7 radius + 4 shadow + 4 transition = 51 total | patterns: [five-level-text-hierarchy, single-hue-multi-opacity-states, multi-layer-shadows, three-tier-spacing, descending-radius-hierarchy, unified-badge-system, asymmetric-transitions] | next: Apply token system to listing detail page, explore/search page
- [2026-02-09] surgical-style-update | outcome: Success | tokens: 17px, Paula Scher Palette | files: version-d - style-injection.html | decisions: CSS-only update to preserve HTML | patterns: Variables Injection | next: Await user feedback

---

## Key Patterns Learned

- **Surgical Updates:** When HTML structure is fragile (e.g., specific mobile menu IDs), use CSS variable injection instead of rewriting the full DOM.
- **Paula Scher Palette:** Restricting purple usage to < 8% of pixels increases CTA prominence and reduces "purple overload".
- **Multi-layer Shadows:** Essential for premium feel; single-layer shadows feel flat/cheap.
- **Five-Level Text Hierarchy:** Using 5 gray values (#18181B, #3F3F46, #52525B, #71717A, #A1A1AA) instead of 1 gray (#666666) creates visible information layers even without color or sizing changes.
- **WCAG-Safe Semantic Colors:** Original greens/yellows (#00C853, #FFC107) fail AA on white. Darker variants (#0F8A3F for text, #16A34A for UI; #B45309 for text, #D97706 for UI) pass while maintaining visual intent.
- **Single-Hue Interactive States:** Deriving hover/pressed/selected/focus from one color at 4%/8%/12%/100% ensures states harmonize automatically and can be updated with one variable change.
- **Three-Tier Spacing:** 48px section / 24px group / 12px element. Eliminates arbitrary gap values and creates a vertical beat.
- **Descending Border-Radius:** Cards 12px > Buttons 8px > Badges 6px. The radius communicates element type at a glance.
- **Asymmetric Transitions:** entry = ease-out (fast start, slow settle), exit = ease-in (slow start, fast exit). Different from using same timing for both.
- **Font Weight Discipline:** 3 weights max (400/500/600). Weight 700 is never needed when 600 is the ceiling. Hierarchy through color/size, not weight escalation.

---

## Running Lists

- `COLORS_DEFINED:` primary (#2D1B69), primary-dark (#1E1147), primary-light (#7B4FB5), primary-bg (#EDEAF4), success (#0F8A3F), success-vivid (#16A34A), warning (#B45309), warning-vivid (#D97706), error (#B91C1C), error-vivid (#DC2626), neutral-50 through neutral-900 (10 values)
- `TASTE_TEST_SCORES:` [2026-02-09]: host-dashboard-tokens: 28/30 (Q1 fail: simplified dashboard header, Q2 fail: no weekly schedule selector on dashboard) | [2026-02-09]: surgical-update: 28/30
- `TOKENS_GENERATED:` [2026-02-09]: 10 color tokens + 4 semantic color sets + 10 neutral scale + 8 font-size + 3 font-weight + 3 line-height + 3 letter-spacing + 12 spacing + 7 radius + 4 shadow + 4 transition = 51 design tokens
- `WCAG_ISSUES:` Original #00C853 (success green): 3.0:1 on white (FAIL) -> fixed to #0F8A3F (4.6:1). Original #FFC107 (warning yellow): 1.3:1 as text (FAIL) -> fixed to #B45309 (4.7:1). All combinations now pass AA.
