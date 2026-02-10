# Proposed Flow: Host Overview Dashboard (Minimum Viable)

**Agent:** Agent 1 -- How it Works
**Date:** 2026-02-09
**Subject:** Minimum viable dashboard design -- fewest elements for goal completion

---

## Design Principle

Every element must pass this test: **"Does this help the host answer one of their three core questions in fewer seconds?"**

1. What needs my attention right now?
2. How are my listings performing?
3. How do I take the next action?

If an element does not directly serve one of these, it is eliminated or deferred.

---

## 1. Proposed Dashboard Structure

```
HOST LANDS ON DASHBOARD
|
+-- [A] HEADER BAR (minimal)
|   +-- Split Lease logo (home link)
|   +-- "Messages" with unread count badge
|   +-- User avatar (dropdown: Settings, Logout)
|   Note: "Host Overview" link removed -- you are already here.
|         "Host with Us" dropdown removed -- not relevant for logged-in hosts.
|
+-- [B] TOP BAR (compact, single row)
|   +-- Left: "Your Dashboard" (page title, no greeting subtitle)
|   +-- Right: "+ Create New Listing" button
|   Note: "Import Listing" moved to Create Listing flow as secondary option.
|         "Welcome back, Rod" eliminated -- name is in avatar dropdown.
|         "Here's what's happening..." eliminated -- stats are self-explanatory.
|
+-- [C] URGENCY STRIP (conditional -- only shows if items need attention)
|   +-- IF pending proposals > 0:
|   |   "You have [N] proposals waiting -- [Newest: Guest Name for Listing Name]"
|   |   + "Review Now" button
|   +-- IF listing incomplete AND not dismissed:
|   |   "Your listing [Name] is [X]% complete -- [Next step: Add Photos]"
|   |   + "Continue Setup" button + dismiss (X)
|   +-- IF no urgent items:
|       Strip does not render. Dashboard starts with stats.
|   Note: Combines action banner + onboarding into one urgency system.
|         Priority order: proposals first, then incomplete listings.
|         Max 2 items shown; "See all" link if more.
|
+-- [D] PERFORMANCE SUMMARY (2 KPI cards, unchanged from mockup)
|   +-- Card 1: "This Month's Earnings"
|   |   +-- Dollar amount (large)
|   |   +-- % change vs last month
|   |   +-- Occupancy % (inline)
|   +-- Card 2: "Proposals"
|   |   +-- Needing action (large number)
|   |   +-- Total pending (secondary)
|   |   +-- "See all stats" link (progressive disclosure to full analytics)
|   Note: Rating removed from card -- it belongs in analytics.
|         Two cards are the right number. More would increase scan time.
|
+-- [E] LISTINGS (card grid, enhanced)
|   +-- Section header: "Your Listings" + count
|   +-- For EACH listing (card):
|       +-- Real photo (or "Add Photo" placeholder with camera icon)
|       +-- Status badge: "Online" (green + checkmark) / "Offline" (gray + pause)
|       +-- Quick toggle: tap status badge to go online/offline (confirmation dialog)
|       +-- Listing title
|       +-- Location (only if host has listings in 2+ different areas; hide if all same)
|       +-- Mini-stats row:
|       |   +-- Earnings this month ($)
|       |   +-- Occupancy (%)
|       |   +-- Proposals (count, highlighted if > 0)
|       +-- Completion bar (only if listing < 100% complete):
|       |   +-- "[X]% complete -- Next: [step name]"
|       +-- Action buttons:
|           +-- "Manage" (edit listing)
|           +-- "Proposals [N]" (if N > 0, badge; if N = 0, no badge)
|   Note: Delete button removed from overview -- destructive action belongs in Manage.
|         "Preview" button removed from overview -- belongs in Manage.
|         "Leases" button removed -- hosts access leases through Proposals flow.
|         "Create House Manual" removed -- folded into completion bar.
|         Completion bar replaces separate onboarding section for per-listing guidance.
|
+-- [F] NO FOOTER ON DASHBOARD
    Note: Footer with referral, app download, company links is removed from dashboard.
          These are marketing/SEO elements that belong on public pages, not logged-in dashboards.
          "Give $50, Get $50" referral moved to Settings or a dedicated Referrals page.
          Import listing CTA moved into Create Listing flow.
```

---

## 2. Conditional Rendering Rules

The dashboard adapts based on host state. These are not "pages" -- they are the same dashboard with conditional elements.

### State: First-Time Host (0 listings)

```
DASHBOARD (first-time)
|
+-- [A] HEADER (same)
+-- [B] TOP BAR: "Your Dashboard" + "+ Create Your First Listing" (prominent)
+-- [C] URGENCY STRIP: not shown (nothing urgent)
+-- [D] PERFORMANCE SUMMARY: not shown (no data)
+-- [E] EMPTY STATE:
|   +-- Illustration or icon
|   +-- "You don't have any listings yet."
|   +-- "Create a listing to start receiving proposals from guests."
|   +-- Large "+ Create Your First Listing" button (repeated, primary CTA)
|   +-- Secondary: "Import from another platform" link
+-- No footer
```

### State: New Host (1 incomplete listing)

```
DASHBOARD (new host)
|
+-- [A] HEADER (same)
+-- [B] TOP BAR (same)
+-- [C] URGENCY STRIP:
|   +-- "Your listing [Name] is [X]% complete -- Next: [step]. Complete it to start receiving proposals."
|   +-- "Continue Setup" button
+-- [D] PERFORMANCE SUMMARY: not shown (no meaningful data yet)
+-- [E] LISTINGS: 1 card
    +-- Completion bar prominent
    +-- Status: "Offline" (cannot go online until complete)
    +-- Mini-stats: all zeros or dashes
    +-- "Manage" button
```

### State: Active Host (1-3 listings, some activity)

```
DASHBOARD (active host)
|
+-- [A] HEADER (same)
+-- [B] TOP BAR (same)
+-- [C] URGENCY STRIP: shown if proposals pending
+-- [D] PERFORMANCE SUMMARY: both KPI cards (populated)
+-- [E] LISTINGS: 1-3 cards in grid
    +-- Mini-stats populated
    +-- Proposal badges visible
    +-- Completion bar only on incomplete listings
```

### State: Power Host (4-5 listings, high volume)

```
DASHBOARD (power host)
|
+-- [A] HEADER (same)
+-- [B] TOP BAR (same)
+-- [C] URGENCY STRIP: shown, may have multiple items
|   +-- "[N] proposals across [M] listings need review"
|   +-- "Review All" button
+-- [D] PERFORMANCE SUMMARY: both KPI cards
|   +-- Aggregate earnings across all listings
|   +-- Aggregate proposals needing action
+-- [E] LISTINGS: 4-5 cards in grid
    +-- Cards may need to shrink or paginate on mobile
    +-- Sort: listings with proposals first, then by earnings descending
    +-- Mini-stats per listing enable comparison
```

---

## 3. Mobile Adaptation

On screens < 768px:

- **Header:** Hamburger menu replaces text links; avatar and Messages icon remain
- **Top Bar:** "+ Create" button becomes floating action button (FAB) at bottom-right
- **Urgency Strip:** Full width, swipeable if multiple items
- **KPI Cards:** Stack vertically (1 column) instead of 2-column grid
- **Listing Cards:** Stack vertically, full width
- **Mini-stats:** Compact single row, abbreviate labels ("$1.2K" instead of "$1,240")
- **Actions:** "Manage" and "Proposals" buttons stack or become icon buttons

---

## 4. Information Architecture (Final)

```
LAYER 1: Dashboard (overview)
    |-- Urgency strip (proposals, incomplete listings)
    |-- KPI summary (earnings, proposals)
    |-- Listing cards (per-listing performance + actions)
    |
LAYER 2: Listing Detail (manage)
    |-- Full listing editor (all sections)
    |-- Preview
    |-- Status toggle (online/offline)
    |-- Delete listing
    |-- House Manual editor
    |
LAYER 3: Proposals (per-listing)
    |-- Proposal list
    |-- Accept/Decline/Counter
    |-- Guest details
    |
LAYER 4: Analytics (expanded stats)
    |-- Historical earnings
    |-- Occupancy trends
    |-- Rating breakdown
    |-- Comparison across listings
```

---

## 5. Flow: Host Routine Check (Happy Path)

This is the most common flow -- an active host checking in:

```
1. Host opens dashboard (via login or bookmark)
2. Eyes land on URGENCY STRIP:
   - "2 proposals waiting" --> Host decides to review
   - Clicks "Review Now" --> Goes to Proposals page
   - (OR) No urgency items --> Eyes move to KPI cards
3. Host scans KPI CARDS:
   - Earnings: "$2,847 (+12%)" --> Satisfied or concerned
   - Proposals: "2 needing action" --> Reinforces urgency
4. Host scans LISTING CARDS:
   - Identifies which listing has proposals (badge count)
   - Checks per-listing earnings and occupancy
   - Notes any listing that's Offline (gray badge)
5. Host takes action:
   - Clicks "Proposals [2]" on specific listing card
   - OR clicks "Manage" to edit a listing
   - OR closes the tab (routine check complete, nothing urgent)
6. Host exits dashboard.

Total time for routine check (no action needed): ~10 seconds
Total time for proposal review path: ~15 seconds to reach proposals
```

---

## 6. Flow: First-Time Host (Onboarding Path)

```
1. Host signs up and is redirected to dashboard
2. Dashboard shows EMPTY STATE:
   - "You don't have any listings yet."
   - "+ Create Your First Listing" (large, primary)
3. Host clicks "Create Your First Listing"
   --> Enters listing creation flow
4. Host completes basic listing info (title, type, location)
   --> Redirected back to dashboard
5. Dashboard now shows:
   - URGENCY STRIP: "Your listing is 40% complete -- Next: Add Photos"
   - 1 LISTING CARD with completion bar
6. Host clicks "Continue Setup" or "Manage"
   --> Returns to listing editor at the next incomplete section
7. Host iterates until listing is 100% complete
8. Dashboard shows:
   - URGENCY STRIP: "Your listing is ready! Go Online to start receiving proposals."
   - Listing card status: "Offline" with "Go Online" toggle
9. Host toggles listing Online
10. Dashboard enters Active Host state (waiting for first proposal)

Total sessions to complete: 1-3 (host may leave and return)
Key design requirement: Host must be able to complete onboarding in a SINGLE session if motivated.
```

---

## 7. Justification for Every Proposed Element

| Element | User Goal Served | Business Goal Served | Why It Stays |
|---------|-----------------|---------------------|--------------|
| Header (minimal) | Navigation, identity | Platform cohesion | Essential infrastructure |
| Page title "Your Dashboard" | Orientation | None | Minimal, confirms location |
| "+ Create New Listing" | P4 (next action) | B4 (new listings) | Primary growth action |
| Urgency Strip | P1 (attention items) | B1 (fast proposal response), B2 (listing completion) | Answers #1 host question immediately |
| Earnings KPI | P2 (performance) | B3 (retention/motivation) | Core host need |
| Proposals KPI | P1 (attention) | B1 (fast response) | Core host need |
| Listing cards with mini-stats | P2, P3 (per-listing performance) | B1, B3 | Enables comparison and action per listing |
| Status badge with toggle | P3 (listing state) | B3 (keep listings online) | Removes a step (no need to enter Manage to toggle) |
| Completion bar (conditional) | P5 (what's incomplete) | B2 (listing completion) | Replaces full onboarding section with per-listing guidance |
| "Manage" button | P4 (edit listing) | B2 (listing completeness) | Direct action path |
| "Proposals" button with badge | P1, P4 | B1 | Direct path to proposals |
| Empty state (0 listings) | P4 (first action) | B4 (new listings) | Prevents confusion for new hosts |
| Conditional rendering | All | All | Reduces noise for each persona |

---

*Generated by Agent 1 (How it Works) -- 2026-02-09*
