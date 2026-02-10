# Goal Analysis: Host Overview Dashboard

**Agent:** Agent 1 -- How it Works
**Date:** 2026-02-09
**Subject:** Host Overview Dashboard (Split Lease)

---

## 1. User Goal (Explicit)

**Primary goal:** "Show me the state of my listings business in under 10 seconds."

The host opens the dashboard to answer three questions, in priority order:

1. **"What needs my attention right now?"** -- Pending proposals, guest messages, incomplete listings
2. **"How are my listings performing?"** -- Earnings this month, occupancy rate, proposal volume
3. **"How do I take the next action?"** -- Respond to a proposal, edit a listing, go online/offline

### Goal decomposition:

| Priority | Host Question | Success Metric | Time Budget |
|----------|--------------|----------------|-------------|
| P1 | What needs my attention? | Host can identify urgent items in < 3 seconds | Glance |
| P2 | How much am I earning? | Aggregate earnings visible without scrolling | < 5 seconds |
| P3 | Which listing has activity? | Per-listing proposal/earnings visible at a glance | < 10 seconds |
| P4 | What should I do next? | Clear primary CTA visible | < 5 seconds |
| P5 | Is my listing complete? | Onboarding progress visible (if applicable) | < 10 seconds |

---

## 2. Business Goal (Explicit)

**Primary goal:** "Keep hosts active, get proposals accepted quickly, get listings fully completed."

Split Lease's revenue depends on completed transactions (proposal -> accepted lease). The dashboard must drive three business outcomes:

1. **Fast proposal response** -- Every hour a proposal sits unreviewed increases abandonment risk
2. **Listing completion** -- Incomplete listings get fewer proposals; hosts with empty sections (no photos, no amenities, no description) underperform
3. **Host retention** -- Hosts who check the dashboard regularly and see positive performance indicators are less likely to churn

### Business goal decomposition:

| Priority | Business Outcome | Dashboard Lever | Metric |
|----------|-----------------|-----------------|--------|
| B1 | Proposals accepted fast | Surface proposals with urgency signals | Time from proposal submission to host response |
| B2 | Listings fully completed | Onboarding progress + next-step nudges | % of listing fields completed |
| B3 | Hosts stay active | Show positive performance (earnings, occupancy) | Dashboard visit frequency, host churn rate |
| B4 | New listings created | Create/Import buttons prominent | Listings created per host |
| B5 | Platform trust | Show ratings, reviews, professional design | Host NPS, support ticket volume |

---

## 3. Persona Analysis

### Persona 1: First-Time Host (0 listings)

- **Context:** Just signed up, no listings created yet
- **Goal:** Understand what to do first
- **Dashboard state:** Empty -- no stats, no listings, no proposals
- **Emotional state:** Uncertain, exploratory, possibly overwhelmed
- **Key need:** Clear onboarding path, single obvious CTA ("Create Your First Listing")
- **Risk:** If the dashboard shows a blank page with no guidance, the host bounces and never returns
- **Device:** Likely desktop (first-time setup is a sit-down task)

### Persona 2: New Host (1 incomplete listing)

- **Context:** Created a listing but hasn't finished all sections (missing photos, amenities, description)
- **Goal:** Complete listing setup so it can go live
- **Dashboard state:** 1 listing card (offline), onboarding progress partial, no earnings, no proposals
- **Emotional state:** Motivated but frustrated if unclear what's missing
- **Key need:** Specific next-step guidance ("Add photos to go live"), progress indicator
- **Risk:** If the host can't easily see what's incomplete, they abandon the listing
- **Device:** Desktop or mobile (may toggle between)

### Persona 3: Active Host (1-3 listings, regular activity)

- **Context:** Has listings live, gets proposals periodically, checks dashboard 2-3x/week
- **Goal:** Check earnings, respond to proposals, ensure listings are performing
- **Dashboard state:** Stats populated, some proposals pending, listings with varied performance
- **Emotional state:** Routine, efficiency-focused, wants quick scan
- **Key need:** At-a-glance performance summary, fast path to proposals
- **Risk:** If the dashboard buries proposals or makes performance hard to scan, the host responds slowly
- **Device:** Desktop and mobile roughly equal

### Persona 4: Power Host (4-5 listings, high volume)

- **Context:** Multiple listings, frequent proposals, treats Split Lease as a serious income source
- **Goal:** Manage portfolio efficiently, identify underperforming listings, respond to all proposals
- **Dashboard state:** Full stats, multiple proposal badges, varied listing performance
- **Emotional state:** Business-minded, impatient with friction, wants data
- **Key need:** Comparative listing performance, batch actions, quick proposal triage
- **Risk:** If the dashboard doesn't scale well beyond 3 listings, the power host outgrows it
- **Device:** Primarily desktop (portfolio management is a power-user task)

---

## 4. Context Analysis

### Frequency and Duration

- **Visit frequency:** 2-3x per week for active hosts; daily when proposals are pending
- **Session duration:** 30 seconds (quick check) to 5 minutes (respond to proposals, edit listing)
- **Session pattern:** Open dashboard -> scan stats -> check proposals -> maybe edit listing -> leave

### Environment

- **Device split:** ~60% desktop, ~40% mobile (estimated for NYC host demographic)
- **Time of day:** Morning (before work) and evening (after work) peaks
- **Interruption level:** High -- hosts are checking between other tasks
- **Connectivity:** Generally good (NYC), but mobile can be spotty underground

### Information Hierarchy (What Matters Most)

Based on host behavior patterns and the three core questions:

1. **Proposals needing action** (time-sensitive, revenue-driving)
2. **Earnings this month** (motivation, performance validation)
3. **Listing status** (online/offline, are guests seeing my listing?)
4. **Occupancy rate** (am I priced right? is my listing competitive?)
5. **Onboarding progress** (only relevant for incomplete listings)
6. **Create/Import actions** (only relevant when adding new listings)

---

## 5. Element-by-Element Goal Justification

Every element on the current mockup evaluated against user and business goals:

| # | Element | Serves User Goal? | Serves Business Goal? | Justified? | Notes |
|---|---------|--------------------|-----------------------|------------|-------|
| 1 | Header nav (logo, links, avatar) | Yes -- navigation, identity | Yes -- platform navigation | YES | Standard, minimal |
| 2 | "Welcome back, Rod" | Weak -- personalization signal | Weak -- retention/warmth | MARGINAL | Takes vertical space for low value; could be smaller |
| 3 | "Here's what's happening with your listings today" | Marginal -- sets context | No direct business value | MARGINAL | The stats themselves convey this; text is redundant |
| 4 | "+ Create New Listing" button | Yes (P4 for hosts adding) | Yes (B4) | YES | But only relevant for a subset of visits |
| 5 | "Import Listing" button | Yes (P4) | Yes (B4) | YES | Same caveat -- not every-visit relevant |
| 6 | Earnings KPI card | Yes (P2) | Yes (B3 -- retention) | YES | Core value |
| 7 | "+12% vs last month" change indicator | Yes (P2) | Yes (B3) | YES | Trend context, motivating |
| 8 | "78% occupancy" in earnings card | Yes (P2) | Yes (B3) | YES | Key performance metric |
| 9 | "See all stats" link | Yes (P2 expansion) | Yes (B3) | YES | Progressive disclosure |
| 10 | Proposals Needing Action card | Yes (P1) | Yes (B1) | YES | Core value |
| 11 | "3 total pending" detail | Yes (P1) | Yes (B1) | YES | Context for action count |
| 12 | "4.9 avg rating" | Marginal (P2) | Yes (B5) | MARGINAL | Doesn't drive immediate action; nice-to-know |
| 13 | Action Required Banner | Yes (P1) | Yes (B1) | YES | Urgency signal |
| 14 | Specific proposal name in banner | Yes (P1) | Yes (B1) | YES | Reduces cognitive load |
| 15 | "Review Proposals" button w/ loading | Yes (P4) | Yes (B1) | YES | Direct action path |
| 16 | Onboarding section (dismissible) | Yes (P5, new hosts) | Yes (B2) | CONDITIONAL | Essential for new hosts; noise for completed hosts |
| 17 | Dismiss (X) button on onboarding | Yes (reduces noise) | Marginal (host may dismiss prematurely) | YES | Respects user autonomy |
| 18 | "3 of 5 steps completed" text | Yes (P5) | Yes (B2) | YES | Progress awareness |
| 19 | 5 step indicators | Yes (P5) | Yes (B2) | YES | Visual progress |
| 20 | Next step hint | Yes (P4, P5) | Yes (B2) | YES | Reduces decision cost |
| 21 | Listing cards (grid) | Yes (P3) | Yes (B3) | YES | Core content |
| 22 | Listing image placeholder | Marginal (recognition) | Marginal | MARGINAL | Placeholder adds no info; real photos would help |
| 23 | Status badge (Online/Offline) w/ icon | Yes (P3) | Yes (B3) | YES | Critical listing state info |
| 24 | Listing title | Yes (P3) | No direct | YES | Identification |
| 25 | Listing location | Marginal (redundant if host knows) | No direct | MARGINAL | Useful for multi-location hosts; redundant for most |
| 26 | Per-listing mini-stats (earnings, occupancy, proposals) | Yes (P2, P3) | Yes (B1, B3) | YES | Per-listing performance at a glance |
| 27 | "Manage" button per listing | Yes (P4) | Yes (B2, B3) | YES | Edit path |
| 28 | "Proposals" button per listing | Yes (P1, P4) | Yes (B1) | YES | Direct proposal access |

---

## 6. Goal Alignment Summary

### Elements fully aligned (keep):
- Stats KPI cards (earnings + proposals)
- Action Required Banner with specific details
- Listing cards with mini-stats and status badges
- Onboarding section (for incomplete hosts, dismissible)
- Next step hint
- Create/Import buttons
- Review Proposals CTA

### Elements marginally aligned (simplify or conditionally show):
- Welcome text ("Welcome back, Rod") -- shrink to inline or remove subtitle
- "Here's what's happening..." subtitle -- remove, stats convey this
- Avg rating in proposals card -- move to expanded stats view
- Listing location text -- only show if host has listings in multiple locations
- Image placeholder (gradient) -- replace with real photo or remove if no photo uploaded

### Elements missing (should add):
- **No "last checked" timestamp** -- host doesn't know if data is current
- **No listing completion %** per listing card -- host can't see which listings need work without entering each one
- **No "Go Online" toggle** on listing card -- host must enter Manage to toggle status
- **No message indicator** -- proposals and messages are separate concerns; messages are absent from dashboard
- **No mobile-optimized priority view** -- same layout forced to mobile

---

*Generated by Agent 1 (How it Works) -- 2026-02-09*
