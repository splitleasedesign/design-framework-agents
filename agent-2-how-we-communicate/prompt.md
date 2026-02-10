# Task: Host Dashboard Layout & Responsive Specs
Date: 2026-02-09
Token Budget: 2M

## Input
You are designing the **Host Overview Dashboard** layout for Split Lease, a NYC rental platform.

### Reference Material
- Existing mockup: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\runs\run-002--2026-01-30\html\improved-host-overview-dashboard--don-norman.html`
- Real listing content: `C:\Users\igor\OneDrive\Desktop\long-running processes\Site Current State\listing-dashboard-text.md`
- Calibration: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\agents\orchestrator\prompts\RESPONSIVE-DESIGN-MODEL.md`
- Responsive screenshots: `C:\Users\igor\OneDrive\Desktop\long-running processes\Site Current State\mockup - Claude\responsive-screenshots\` (before/ and after-final/ folders, look for `*listing-dashboard*` files)

### Dashboard Content Inventory
The host dashboard must display:
1. **Header** — Logo, nav (Host Overview, Messages), avatar
2. **Welcome** — Host name, date context, action buttons (Create Listing, Import)
3. **KPI Stats** — Earnings this month (+% change), Proposals needing action, Occupancy rate
4. **Action Banner** — Urgent items: proposals waiting, incomplete listings
5. **Onboarding Progress** — 5 steps: Create Listing, Add Photos, Set Pricing, House Manual, Go Live (dismissible)
6. **Listings Grid** — Per listing: photo, title, location, status (online/offline), mini-stats (earnings, occupancy, proposals), action buttons (Manage, Proposals)

Host has 1-5 listings. The dashboard is their command center — checked 2-3x/week on desktop (70%) and mobile (30%).

## Process
Execute the Spec-Driven Refactor compound action:

1. **Information inventory** — List every piece of data the dashboard shows
2. **Priority ranking:**
   - P0 (scan first): Proposals needing action, earnings this month
   - P1 (secondary): Listing status, onboarding progress
   - P2 (tertiary): Welcome message, occupancy %, referral banner
3. **Hierarchy map** — Assign visual weight: size, position, contrast for each element
4. **Layout pattern selection:**
   - Stats: 2-column grid (desktop), stack (mobile)
   - Listings: auto-fill grid with minmax(320px, 1fr)
   - Onboarding: horizontal steps (desktop), vertical list (mobile)
   - Action banner: full-width with icon + text + CTA
5. **Generate responsive CSS** using clamp(), auto-fill, container queries:
   - Container padding: `clamp(16px, 4vw, 32px)`
   - Stats grid: `repeat(auto-fill, minmax(min(100%, 280px), 1fr))`
   - Listings grid: `repeat(auto-fill, minmax(min(100%, 320px), 1fr))`
   - Heading: `clamp(22px, 3vw, 28px)`
   - Body text: `clamp(13px, 1.5vw, 15px)`
6. **Apply CSS to produce an HTML file** — Write a complete `host-dashboard.html`
7. **Score against Responsive Taste Test** (self-evaluate at 320, 375, 428, 768, 1024, 1280, 1440px)

## Eval Target
Responsive Taste Test >= 27/30, plus:
- [ ] No horizontal scroll at any viewport
- [ ] Stats cards stack on mobile (<768px), side-by-side on desktop
- [ ] Listing cards stack on mobile, 2-col on tablet, 3-col on desktop
- [ ] Onboarding steps: horizontal on desktop, vertical/scrollable on mobile
- [ ] Action banner: full-width, text wraps cleanly on mobile
- [ ] All touch targets >= 44px on mobile
- [ ] Typography scales fluidly (no overflow, no tiny text)
- [ ] Information hierarchy preserved at every viewport
- Max retries: 3

## Output
Save to: `assets/2026-02-09-host-dashboard/`
Expected files:
- `reports/hierarchy-map-host-dashboard.md` — Information priority ranking
- `reports/layout-spec-host-dashboard.md` — Pattern choices + responsive behavior
- `css/responsive-tokens.css` — CSS custom properties (clamp values)
- `css/host-dashboard.css` — Complete responsive stylesheet
- `host-dashboard.html` — Complete working HTML page with responsive layout

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
