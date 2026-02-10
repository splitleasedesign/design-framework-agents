# Task: Host Dashboard Visual Token System
Date: 2026-02-09
Token Budget: 2M

## Input
You are designing the **visual token system** for the Split Lease Host Dashboard.

### Reference Material
- Existing mockup: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\runs\run-002--2026-01-30\html\improved-host-overview-dashboard--don-norman.html`
- Calibration: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\agents\orchestrator\prompts\DESIGN-TASTE-MODEL.md`

### Current Visual State (from the mockup)
The existing mockup uses these values — audit them:
- Primary: `#31135D` (deep purple), Light: `#7B4FB5`, BG: `#ECE8F7`
- Success: `#00C853`, Warning: `#FFC107`, Error: `#D32F2F`
- Neutrals: `#F0F0F0`, `#E0E0E0`, `#666666`, `#1A1A1A`
- Body font: system stack (-apple-system, BlinkMacSystemFont, Segoe UI, Roboto)
- Font sizes: 11px, 13px, 14px, 16px, 18px, 20px, 28px, 40px (inconsistent scale)
- Spacing: 4px, 8px, 12px, 16px, 20px, 24px, 32px, 40px
- Radius: 8px, 12px, 16px, 20px, 50%
- Shadows: `0 4px 6px -1px rgba(0,0,0,0.1)`, `0 10px 15px -3px rgba(0,0,0,0.1)`

### Dashboard Components to Token
- Header (purple background, white text, nav links)
- Stats cards (white, left color bar, large number, label, subtext)
- Action banner (warning gradient background, icon, text, CTA button)
- Onboarding section (purple gradient, white text, step cards, progress)
- Listing cards (white, image area, status badge, title, stats row, action buttons)
- Buttons (primary purple, secondary outline, badge pills)
- Typography hierarchy (h1 welcome, h2 section title, h3 listing title, body, caption, label)

## Process
Execute the TDD Sandbox compound action:

1. **Visual audit** — Catalog every color, font-size, spacing, radius, and shadow in the existing mockup
2. **Run 30-question Taste Test** — Score the current mockup, identify failures
3. **Generate token system:**
   - **Color tokens:** `--color-primary` through `--color-primary-bg`, `--color-success/warning/error` + backgrounds, neutral scale (50-900), surface colors
   - **Typography tokens:** `--font-size-xs` (11px) through `--font-size-3xl` (clamp(28px, 3vw, 36px)), `--font-weight-regular/medium/semibold/bold`, `--line-height-tight/normal/relaxed`
   - **Spacing tokens:** `--space-1` (4px) through `--space-12` (48px), based on 4px scale
   - **Radius tokens:** `--radius-sm` (6px), `--radius-md` (10px), `--radius-lg` (14px), `--radius-xl` (20px), `--radius-full` (9999px)
   - **Shadow tokens:** `--shadow-sm`, `--shadow-md`, `--shadow-lg` with consistent blur/spread
   - **Transition tokens:** `--transition-fast` (150ms), `--transition-normal` (200ms), `--transition-slow` (300ms)
4. **Write CSS file** with all tokens as `:root` custom properties
5. **Apply tokens** — Rewrite the mockup HTML replacing all hardcoded values with `var(--token-name)`
6. **Check WCAG AA:** Verify contrast ratios for every text-on-background combination

## Eval Target
Design Taste Test >= 27/30 AND WCAG AA pass:
- [ ] All colors from defined palette with usage rules
- [ ] Typography uses consistent scale (no arbitrary sizes)
- [ ] Spacing follows 4px scale (no arbitrary values)
- [ ] WCAG AA: 4.5:1 text, 3:1 UI elements
- [ ] Every color combination documented with contrast ratio
- [ ] Focus indicators on all interactive elements
- [ ] Consistent radius and shadow usage
- [ ] All values specific (hex, px, rem) — nothing vague
- Max retries: 3

## Output
Save to: `assets/2026-02-09-host-dashboard/`
Expected files:
- `css/color-tokens.css` — --color-* custom properties with usage comments
- `css/typography-tokens.css` — --font-size-*, --font-weight-*, --line-height-*
- `css/spacing-tokens.css` — --space-* scale
- `css/component-tokens.css` — --radius-*, --shadow-*, --transition-*
- `css/visual-system.css` — All tokens combined
- `reports/visual-audit-host-dashboard.md` — Current state catalog
- `reports/taste-test-score.md` — XX/30 with pass/fail per question
- `reports/color-system.md` — Palette + usage rules + contrast ratios
- `reports/wcag-audit.md` — Contrast ratios for all text/background combos
- `host-dashboard.html` — Complete HTML with all hardcoded values replaced by var() tokens

## When Done
Update memory.md with: outcome | files produced | eval score | tokens generated | patterns learned
