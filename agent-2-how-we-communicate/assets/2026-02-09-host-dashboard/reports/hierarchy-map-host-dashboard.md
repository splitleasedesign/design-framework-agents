# Hierarchy Map: Host Overview Dashboard
**Agent 2 -- How We Communicate Information**
**Date:** 2026-02-09
**Page:** Host Overview Dashboard (Split Lease)

---

## Information Inventory

Every piece of data the Host Overview Dashboard must communicate, enumerated:

| # | Data Element | Type | Source |
|---|---|---|---|
| 1 | Split Lease logo | Brand identity | Static |
| 2 | Navigation links (Host Overview, Messages) | Wayfinding | Static |
| 3 | Host avatar + initial | Identity confirmation | User profile |
| 4 | Welcome message ("Welcome back, [Name]") | Contextual greeting | User profile + date |
| 5 | Date context ("Here's what's happening...") | Temporal orientation | System date |
| 6 | Create New Listing button | Primary action | Static |
| 7 | Import Listing button | Secondary action | Static |
| 8 | Earnings this month ($X,XXX) | KPI -- revenue | Aggregated from listings |
| 9 | Earnings change vs. last month (+X%) | KPI -- trend | Calculated |
| 10 | Occupancy rate (XX%) | KPI -- utilization | Aggregated from listings |
| 11 | Proposals needing action (count) | KPI -- urgency | Live count |
| 12 | Total pending proposals (count) | KPI -- context | Live count |
| 13 | Average host rating (X.X) | KPI -- reputation | Aggregated |
| 14 | "See all stats" link | Navigation -- deeper analytics | Static |
| 15 | Action banner icon (!) | Urgency signal | Dynamic |
| 16 | Action banner headline ("X proposals need attention") | Urgency message | Dynamic |
| 17 | Action banner detail (who submitted, which listing) | Context for urgency | Dynamic |
| 18 | Review Proposals CTA button | Action -- resolve urgency | Static |
| 19 | Onboarding section title ("Complete Your Host Profile") | Progress frame | Conditional |
| 20 | Onboarding progress text ("X of 5 steps completed") | Progress metric | User state |
| 21 | Dismiss (X) button for onboarding | Control -- hide section | Static |
| 22 | 5 onboarding steps (Create Listing, Add Photos, Set Pricing, House Manual, Go Live) | Progress checklist | User state |
| 23 | Step completion indicators (checkmark vs. pending icon) | Step status | User state |
| 24 | Next step hint text | Guidance -- what to do next | Derived |
| 25 | Listings section title ("Your Listings") | Section label | Static |
| 26 | Listing count ("3 listings") | Context | Derived |
| 27 | Per-listing photo/placeholder | Visual identification | Listing data |
| 28 | Per-listing title | Identification | Listing data |
| 29 | Per-listing location | Geo context | Listing data |
| 30 | Per-listing status badge (Online/Offline + icon) | Operational state | Listing data |
| 31 | Per-listing earnings this month | Revenue per property | Aggregated |
| 32 | Per-listing occupancy % | Utilization per property | Aggregated |
| 33 | Per-listing proposal count | Demand per property | Live count |
| 34 | Per-listing Manage button | Action -- edit listing | Static |
| 35 | Per-listing Proposals button (+ badge count) | Action -- review proposals | Dynamic |

**Total: 35 discrete data elements**

---

## Priority Ranking

### P0 -- Scan First (Must be visible within 2 seconds of page load, above the fold at all viewports)

| Element | Rationale | Visual Treatment |
|---|---|---|
| **Proposals needing action (count)** (#11) | Highest urgency -- missed proposals = lost revenue. Host checks dashboard specifically for this. | Large metric value (40px), warning color accent, left-border accent bar |
| **Action banner** (#15-18) | Amplifies P0 urgency with name + listing context. Bridges awareness to action. | Full-width, warning background gradient, prominent CTA button |
| **Earnings this month** (#8) | Revenue is the host's primary motivation. Validates the platform is working. | Large metric value (40px), success color accent, left-border accent bar |
| **Earnings trend** (#9) | Directional context for earnings -- are things getting better or worse? | Small text below earnings value, green color for positive |

### P1 -- Secondary (Visible above the fold on desktop; within first scroll on mobile)

| Element | Rationale | Visual Treatment |
|---|---|---|
| **Listing status badges** (#30) | Online/offline affects whether a host needs to act (bring listing online). | Color-coded badge on listing image (green/gray) with icon |
| **Per-listing mini-stats** (#31-33) | Breaks down aggregate KPIs by property -- where is revenue coming from? | Compact stat row inside listing card, smaller type |
| **Onboarding progress** (#19-24) | Important for new hosts (drives them to completeness). Dismissible for experienced hosts. | Full-width purple gradient section, horizontal steps on desktop |
| **Listing Proposals button + badge** (#35) | Direct path to reviewing per-listing proposals | Button with count badge, secondary style |

### P2 -- Tertiary (Visible below the fold; supporting context)

| Element | Rationale | Visual Treatment |
|---|---|---|
| **Welcome message** (#4-5) | Contextual warmth but low information density. Host already knows their name. | Medium heading (28px clamp), muted subtitle |
| **Create/Import buttons** (#6-7) | Infrequent action (hosts don't create listings daily). Important but not urgent. | Button pair, primary + secondary styles, right-aligned on desktop |
| **Occupancy rate** (#10) | Supporting metric -- relevant but not action-driving. Rolled into earnings card subtitle. | Small text below earnings |
| **Average rating** (#13) | Vanity metric -- nice to know, not actionable from dashboard. Rolled into proposals card subtitle. | Small text below proposals |
| **Total pending proposals** (#12) | Context for the "needing action" count. Rolled into proposals card subtitle. | Small text within proposals stat card |
| **See all stats link** (#14) | Navigation to deeper analytics -- for power users. | Small text link in stat card header |
| **Listings section header** (#25-26) | Structural label -- minimal information value. | Section heading + count |
| **Per-listing title/location** (#28-29) | Identification -- hosts already know their properties. | Standard card text |
| **Per-listing photo** (#27) | Visual recognition aid -- secondary to data. | Card image placeholder with gradient |
| **Per-listing Manage button** (#34) | Edit action -- less frequent than reviewing proposals. | Primary button inside card |
| **Header nav** (#1-3) | Persistent chrome -- orientation, not information. | Header bar, logo left, nav right |

---

## Hierarchy Map: Visual Weight Assignments

Each element is assigned visual weight via 4 dimensions: **Size**, **Weight (boldness)**, **Position**, and **Contrast/Color**.

```
VIEWPORT SCAN ORDER (top to bottom, F-pattern on desktop):

Desktop (1280px+):
  ┌─────────────────────────────────────────────────────┐
  │ HEADER: Logo ── Nav links ── Avatar                 │  Position: Persistent top
  ├─────────────────────────────────────────────────────┤
  │ Welcome, Rod          [Create Listing] [Import]     │  Size: 28px heading
  │ Here's what's happening...                          │  Weight: Light subtitle
  ├───────────────────────┬─────────────────────────────┤
  │ EARNINGS: $2,847 ★    │ PROPOSALS: 2 ★              │  Size: 40px values (P0)
  │ +12% vs last · 78%    │ 3 pending · 4.9 rating      │  Color: Green/Warning accents
  ├───────────────────────┴─────────────────────────────┤
  │ ⚠ ACTION BANNER: 2 proposals need attention [CTA]  │  Color: Warning bg (P0)
  ├─────────────────────────────────────────────────────┤
  │ ONBOARDING: [✓ Create][✓ Photos][✓ Pricing]        │  Color: Purple gradient (P1)
  │             [📝 Manual][✅ Go Live]                  │  Position: Below KPIs
  │ Next: Add a House Manual...                         │  Weight: Medium
  ├─────────────────────────────────────────────────────┤
  │ Your Listings (3)                                   │  Size: 18px section title
  │ ┌──────────┐ ┌──────────┐ ┌──────────┐             │
  │ │ Card 1   │ │ Card 2   │ │ Card 3   │             │  Layout: 3-col auto-fill
  │ │ [image]  │ │ [image]  │ │ [image]  │             │
  │ │ title    │ │ title    │ │ title    │             │
  │ │ stats    │ │ stats    │ │ stats    │             │
  │ │ [buttons]│ │ [buttons]│ │ [buttons]│             │
  │ └──────────┘ └──────────┘ └──────────┘             │
  └─────────────────────────────────────────────────────┘

Mobile (375px):
  ┌───────────────────────┐
  │ Logo        ☰ Avatar  │  Compact header (56px)
  ├───────────────────────┤
  │ Welcome, Rod          │  Size: 22px (clamped down)
  │ What's happening...   │
  │ [Create] [Import]     │  Buttons wrap below text
  ├───────────────────────┤
  │ EARNINGS: $2,847      │  Full-width stacked (P0)
  │ +12% · 78% occupancy  │
  ├───────────────────────┤
  │ PROPOSALS: 2          │  Full-width stacked (P0)
  │ 3 pending · 4.9 avg   │
  ├───────────────────────┤
  │ ⚠ 2 proposals need    │  Banner wraps: text above
  │   your attention      │  CTA button full-width
  │ [Review Proposals]    │  below
  ├───────────────────────┤
  │ Complete Your Profile │  Onboarding steps become
  │ 3 of 5 steps     [X] │  vertical scrollable list
  │ ✓ Create Listing      │
  │ ✓ Add Photos          │
  │ ✓ Set Pricing         │
  │ 📝 House Manual       │
  │ ✅ Go Live            │
  │ Next: Add House...    │
  ├───────────────────────┤
  │ Your Listings (3)     │
  │ ┌─────────────────┐   │
  │ │ [  full-width   │   │  Cards stack 1-col
  │ │   image 16:9    │   │  Image stacks above text
  │ │ ]               │   │
  │ │ Title           │   │
  │ │ Location        │   │
  │ │ $1,240 · 85% · 2│   │
  │ │ [Manage][Propos]│   │
  │ └─────────────────┘   │
  │ (repeat for each)     │
  └───────────────────────┘
```

---

## Size Scale Reference

| Element | Desktop Size | Mobile Size | CSS Value |
|---|---|---|---|
| KPI metric values | 40px | 32px | `clamp(28px, 5vw, 40px)` |
| Page heading (h1) | 28px | 22px | `clamp(22px, 3vw, 28px)` |
| Section heading (h2) | 18px | 16px | `clamp(16px, 2vw + 0.25rem, 18px)` |
| Onboarding title | 18px | 16px | `clamp(16px, 2vw + 0.25rem, 18px)` |
| Listing card title | 16px | 15px | `clamp(15px, 1.8vw, 16px)` |
| Body/subtitle text | 14px | 14px | Fixed 14px |
| Small labels | 13px | 13px | Fixed 13px |
| Micro labels (stats) | 12px | 12px | Fixed 12px, uppercase |
| Stat card change text | 13px | 13px | Fixed 13px |

---

## Color Weight Assignments

| Element | Color Role | Value |
|---|---|---|
| Proposals needing action (P0) | Warning accent | `#FFC107` left-border, warm background |
| Earnings this month (P0) | Success accent | `#00C853` left-border |
| Action banner (P0) | Warning surface | `linear-gradient(135deg, #FFF8E1, #FFF3CD)` |
| Online status badge | Success | `#00C853` on `#E8F5E9` |
| Offline status badge | Neutral | `#666` on `#E0E0E0` |
| Onboarding section | Primary brand | `linear-gradient(135deg, #31135D, #23083D)` |
| Header | Primary brand | `#31135D` solid |
| Card backgrounds | White surface | `#FFFFFF` |
| Page background | Neutral surface | `#F0F0F0` |

---

## Position Weight Summary

| Position | What goes here | Why |
|---|---|---|
| Persistent top (header) | Logo, nav, avatar | Orientation chrome -- always present |
| First content area | Welcome + action buttons | Context setting, infrequent-use actions |
| Second content area | KPI stat cards | P0 data -- what the host came to see |
| Third content area | Action banner | P0 urgency -- bridges KPIs to action |
| Fourth content area | Onboarding progress | P1 -- important for new hosts, dismissible |
| Fifth content area | Listings grid | P1/P2 -- per-property breakdown |
