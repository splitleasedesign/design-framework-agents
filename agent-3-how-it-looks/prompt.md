# Task: Host Success Stories — Visual Design System
Date: 2026-02-10
Priority: Pipeline Step 3 of 4
Run ID: run-20260210-130900

## Objective
Take Agent 2's wireframe HTML and apply the Split Lease production visual design system. Every color, font, shadow, radius, and icon must come from Style-guide.md. The page should look like it belongs in the Split Lease product — polished, professional, on-brand.

## Input
- **Agent 2's output:** `run-20260210-130900/step-2-communicates/host-success-stories.html`
- **Style guide:** `agent-3-how-it-looks/Style-guide.md` — READ THIS FIRST, it is authoritative
- **Reference tokens:** `agent-3-how-it-looks/assets/2026-02-09-host-dashboard/css/visual-system.css`
- **Previous pipeline output** (for visual consistency): `run-20260210-095033/step-4-feels/listing-dashboard.html`

## Context
- Marketing/social-proof page for Split Lease
- Must be visually consistent with the rest of the Split Lease product
- This is a public-facing conversion page — it needs to feel premium and trustworthy
- Visitors may be seeing Split Lease for the first time

## Style Guide Rules (non-negotiable)
These values come from Style-guide.md. Use them exactly:
- **Primary purple:** `#31135D`
- **Secondary purple (CTAs):** `rgb(109, 49, 194)`
- **Accent purple:** `rgb(140, 104, 238)`
- **Success color:** `#4B47CE` (NOT green)
- **Font:** Inter with system fallbacks
- **Font sizes:** Fixed production scale 11px–36px
- **Button radius:** `20px` (pill shape)
- **Card radius:** `12px`
- **Shadows:** Production values including purple-tinted shadows
- **Gradient header:** `linear-gradient(135deg, #31135D 0%, #5a2d8f 100%)`

## Process
1. **Read Agent 2's HTML** — understand the wireframe structure and hierarchy
2. **Read Style-guide.md** — load all production token values
3. **Add `:root` CSS variables** matching Style-guide.md exactly (copy from visual-system.css)
4. **Apply visual layer:**
   - Import Inter font from Google Fonts
   - Global header with gradient background
   - Card styling: 12px radius, production shadows, white background
   - CTA button: secondary-purple, pill shape, purple shadow on hover
   - Pull quote styling: larger text, italic or distinct treatment, purple accent
   - Host photo: circular with subtle border
   - Typography hierarchy using the production scale
   - Proper spacing using the spacing token scale
5. **Add Feather-style SVG icons** where appropriate (navigation, CTA arrow, quote marks)
6. **Accessibility:**
   - `focus-visible` outlines using secondary-purple
   - `prefers-reduced-motion` media query
   - All text meets WCAG AA contrast (4.5:1)
7. **Token discipline:**
   - ALL color values as CSS custom properties in `:root`
   - NO hardcoded hex values outside `:root`
   - ALL transitions use `var(--transition-*)` tokens
   - ALL radii use `var(--rounded-*)` tokens

## Eval Target (20 items)
All must pass:
- [ ] Primary purple is #31135D
- [ ] Secondary/CTA purple is rgb(109, 49, 194)
- [ ] Success color is #4B47CE (not green)
- [ ] Font family is Inter with system fallbacks
- [ ] Font sizes use the fixed production scale (11-36px)
- [ ] Button border-radius is 20px (pill) for CTAs
- [ ] Card border-radius is 12px
- [ ] Shadows match production values
- [ ] Gradient header uses production values
- [ ] ALL color values are CSS custom properties (no hardcoded hex outside :root)
- [ ] focus-visible with secondary-purple ring
- [ ] prefers-reduced-motion media query exists
- [ ] Icons are Feather-style SVGs, consistently sized
- [ ] Letter-spacing uses 0.5px for uppercase labels
- [ ] Transitions use production durations (0.1s/0.2s/0.3s)
- [ ] Border colors use CSS variables
- [ ] Interactive elements have min-height ≥44px on mobile
- [ ] Pull quote has distinct visual treatment (not same as body text)
- [ ] CTA section is visually prominent with gradient or strong contrast
- [ ] Page is visually consistent with the listing dashboard
- Max retries: 3

## Output
Save to: `run-20260210-130900/step-3-looks/host-success-stories.html`

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
