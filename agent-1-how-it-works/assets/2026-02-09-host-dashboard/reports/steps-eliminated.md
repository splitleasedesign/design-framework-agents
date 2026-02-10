# Steps Eliminated: Host Overview Dashboard

**Agent:** Agent 1 -- How it Works
**Date:** 2026-02-09
**Subject:** Elements removed from current design and why

---

## Elimination Criteria

Every element was tested against:
- **User Goal Test:** Does this help the host answer their three core questions?
- **Business Goal Test:** Does this drive proposal acceptance, listing completion, or host retention?
- **Frequency Test:** Is this relevant on most dashboard visits, or only edge-case visits?
- **Location Test:** Does this belong on the dashboard, or does it belong elsewhere?

If an element fails all four tests, it is eliminated. If it fails some tests, it is evaluated for relocation or conditional display.

---

## 1. Elements Eliminated Entirely

### E1: "Welcome back, [Name]" Greeting + Subtitle

**Current state:** Two lines of text -- "Welcome back, Rod" + "Here's what's happening with your listings today"

**Why eliminated:**
- The host's name is already visible in the avatar/dropdown in the header
- "Here's what's happening with your listings today" is redundant -- the KPI cards and urgency strip convey this through actual data, not text
- These two lines consume ~60px of vertical space above the fold, pushing actionable content down
- On mobile, this is especially costly -- every pixel above the fold is prime real estate

**User Goal Test:** FAIL -- does not answer any of the three core questions
**Business Goal Test:** FAIL -- no measurable business impact
**Frequency Test:** Shown every visit, adds zero information after the first visit
**Location Test:** Greeting belongs on login success toast, not persistent dashboard

**Replacement:** Page title "Your Dashboard" (compact, functional, orients the user)

---

### E2: "Import Listing" Button (from top-level)

**Current state:** Secondary button next to "+ Create New Listing" in the welcome section

**Why eliminated:**
- Import is a subset of creating a listing -- it's an alternative method, not a parallel action
- Having two listing-creation CTAs side by side creates a decision point where none is needed
- Most hosts will never use import (it's for hosts migrating from Airbnb/VRBO)
- Occupying top-level dashboard space for a one-time action is wasteful

**User Goal Test:** FAIL for routine visits -- only relevant when adding a new listing
**Business Goal Test:** MARGINAL -- helps B4 (new listings) but only for a niche use case
**Frequency Test:** FAIL -- used once or never per host lifetime
**Location Test:** Belongs inside the Create Listing flow as a secondary option

**Replacement:** "Import from another platform" link appears inside the Create Listing wizard as step 1 option

---

### E3: Specialist Co-Host Banner

**Current state (live site):** Dismissible info banner -- "Need help setting up? Ask a Specialist Co-host! Our specialists can help you optimize your listing and attract more quality tenants."

**Why eliminated:**
- This is a marketing/upsell element, not a functional dashboard element
- It occupies significant vertical space and adds visual noise
- Hosts who need a co-host specialist will find this through Help/Support or be reached via email
- The banner uses a generic message that becomes irrelevant after initial setup
- Already removed in the Don Norman mockup, confirming its low value

**User Goal Test:** FAIL -- does not answer any core question
**Business Goal Test:** MARGINAL -- could drive co-host adoption, but interrupts the primary flow
**Frequency Test:** FAIL -- irrelevant on routine visits
**Location Test:** Belongs in Help Center, onboarding email sequence, or Settings > Services

**Replacement:** If co-host recommendation is important, add a contextual nudge inside the listing editor when performance metrics are low (e.g., "This listing has 0 proposals this month. A specialist co-host can help optimize it.")

---

### E4: House Manuals Section (Separate Section)

**Current state (live site):** Dedicated "House Manuals" section below listings with its own header and "+ Create New Manual" button. Shows empty state: "You don't have any house manuals yet."

**Why eliminated:**
- House manuals are a per-listing concern, not a standalone dashboard section
- A separate section creates the impression that manuals are a separate product, when they are a listing completion step
- The empty state ("You don't have any house manuals yet") provides no guidance on why manuals matter or which listing needs one
- This section competes for attention with more important elements (proposals, earnings)

**User Goal Test:** FAIL -- not one of the three core questions
**Business Goal Test:** MARGINAL -- manuals improve guest experience but showing a separate section doesn't drive manual creation
**Frequency Test:** FAIL -- only relevant when a listing lacks a manual (setup phase)
**Location Test:** Belongs inside the listing editor as a section, and as a step in the per-listing completion bar

**Replacement:** "Create House Manual" appears as a step in the per-listing completion bar (e.g., "80% complete -- Next: Add House Manual") and as a section within Manage Listing.

---

### E5: Delete Button (Trash Icon) on Listing Cards

**Current state (live site):** Each listing card has a trash can icon for deletion

**Why eliminated:**
- Deletion is a destructive, irreversible action
- Placing it on the overview dashboard -- at the same visual level as "Manage" and "Proposals" -- creates accidental deletion risk
- The trash icon has no confirmation dialog visible in the current UI (unknown if one exists)
- Deletion is a rare action (hosts delete listings maybe once per year)
- Proximity of the delete button to everyday action buttons violates error-prevention principles

**User Goal Test:** FAIL -- no host opens the dashboard intending to delete a listing
**Business Goal Test:** FAIL -- business wants hosts to keep listings, not delete them
**Frequency Test:** FAIL -- extremely rare action
**Location Test:** Belongs inside Manage Listing > Settings > "Delete This Listing" (buried, with confirmation)

**Replacement:** Delete is accessible via Manage Listing > scroll to bottom > "Delete This Listing" (red text, requires confirmation dialog with listing name re-entry)

---

### E6: "Preview" Button on Listing Cards (Overview Level)

**Current state (live site):** Each listing card has a "Preview" button alongside "Manage Listing"

**Why eliminated:**
- Preview is a secondary action -- hosts preview after making edits, not from the overview
- Having Preview at the overview level implies the host needs to check what their listing looks like routinely, which they don't
- It adds a button to every listing card, increasing visual density
- The distinction between "Manage" (edit) and "Preview" (view) is unclear to some users

**User Goal Test:** FAIL -- not one of the three core questions on routine visits
**Business Goal Test:** MARGINAL -- previewing may encourage hosts to improve listings, but indirect
**Frequency Test:** FAIL -- used only after editing a listing
**Location Test:** Belongs inside Manage Listing as a top-level action (e.g., "Preview" button in the listing editor header)

**Replacement:** "Preview" button appears at the top of the Manage Listing page, where the host has just made edits and wants to see the result.

---

### E7: "Leases" Button on Listing Cards

**Current state (live site):** Each listing card has a "Leases" button with a badge count

**Why eliminated:**
- Leases are a downstream consequence of accepted proposals -- the flow is Proposal -> Accepted -> Lease
- A host doesn't manage leases from the overview dashboard; they manage leases through the specific lease management flow
- Having both "Proposals" and "Leases" on each card creates decision fatigue ("Which do I click?")
- Active leases are not an urgent attention item in the same way proposals are

**User Goal Test:** FAIL -- "How are my leases?" is not a routine dashboard question
**Business Goal Test:** MARGINAL -- lease management matters, but the dashboard is the wrong entry point
**Frequency Test:** FAIL -- hosts manage leases infrequently (term changes, early termination)
**Location Test:** Belongs in a dedicated Leases page accessible from nav, or within the Proposals flow (Accepted Proposals = Active Leases)

**Replacement:** Leases are accessible via header navigation (dedicated "Leases" page) or through Proposals > Accepted tab. Per-listing lease info appears inside Manage Listing.

---

### E8: Full Footer (Company Links, Referral, App Download, Import)

**Current state (live site):** Large footer with Company links, For Hosts links, Refer a Friend module, Import Your Listing module, App Store badges, legal links

**Why eliminated:**
- This is a marketing/SEO footer designed for public-facing pages, not logged-in dashboard pages
- Every element in the footer has a better home:
  - Company links: accessible from main site footer (public pages)
  - Referral: dedicated Referrals page or Settings
  - Import: inside Create Listing flow
  - App download: one-time email or dedicated downloads page
- The footer pushes the page length significantly, making the listings section feel lower
- On the live site screenshot, the footer is nearly as tall as the listings section

**User Goal Test:** FAIL for every element
**Business Goal Test:** MARGINAL -- referral drives growth, but this is the wrong context
**Frequency Test:** FAIL -- none of these are routine actions
**Location Test:** Each element has a more appropriate home elsewhere

**Replacement:** Dashboard has no footer. A minimal footer with "Terms | Privacy | Help" appears in the global layout but contains no marketing modules.

---

### E9: Average Rating in Proposals KPI Card

**Current state (mockup):** "4.9 avg rating" displayed in the Proposals Needing Action card

**Why eliminated:**
- The avg rating is not directly actionable from the dashboard
- It's not related to proposals needing action (conflates two concepts in one card)
- Rating is a vanity metric for routine visits -- hosts check it occasionally, not every session
- Including it in the proposals card muddles the card's purpose (action vs. vanity)

**User Goal Test:** FAIL -- not one of the three core questions
**Business Goal Test:** MARGINAL -- rating awareness helps, but doesn't drive immediate action
**Frequency Test:** FAIL -- hosts check rating occasionally, not on every visit
**Location Test:** Belongs in the expanded analytics view ("See all stats")

**Replacement:** Rating appears in the analytics page accessible via "See all stats" link.

---

## 2. Elements Relocated (Not Eliminated, Moved)

| Element | Current Location | New Location | Reason |
|---------|-----------------|--------------|--------|
| Import Listing button | Top-level dashboard | Inside Create Listing flow | One-time action, not routine |
| Co-host specialist banner | Dashboard banner | Contextual nudge in listing editor (low performance) | More relevant in context |
| House Manuals section | Standalone dashboard section | Per-listing completion bar + Manage Listing section | Per-listing concern |
| Delete listing | Trash icon on listing card | Manage Listing > Settings > Delete | Destructive action needs burial |
| Preview listing | Button on listing card | Top of Manage Listing editor | Relevant only after editing |
| Leases button | Button on listing card | Header nav + Proposals > Accepted | Different management context |
| Referral program | Footer module | Settings > Referrals or dedicated page | Not a dashboard concern |
| App download | Footer module | One-time email + Help Center | Not a dashboard concern |
| Average rating | Proposals KPI card | Analytics page ("See all stats") | Vanity metric, not actionable |

---

## 3. Elements Made Conditional (Show Only When Relevant)

| Element | Condition to Show | Condition to Hide |
|---------|-------------------|-------------------|
| Urgency Strip | Pending proposals > 0 OR any listing < 100% complete | No proposals AND all listings complete |
| Onboarding completion bar | Listing is < 100% complete | Listing is 100% complete |
| KPI cards | At least 1 listing exists | 0 listings (show empty state instead) |
| Listing location | Host has listings in 2+ different areas | All listings in same area |
| "See all stats" link | At least 1 month of data exists | Brand new host with no data |
| Proposal badge count | Proposals > 0 | Proposals = 0 (button still visible, no badge) |

---

## 4. Net Impact

| Metric | Current (Live Site) | Current (Mockup) | Proposed |
|--------|-------------------|-------------------|----------|
| Elements above the fold (desktop) | ~5 (welcome, banner, buttons, start of listings) | ~8 (welcome, stats, action banner, start of onboarding) | ~6-7 (title, urgency strip, stats, start of listings) |
| Buttons per listing card | 5 (Manage, Preview, Proposals, Leases, House Manual) | 2 (Manage, Proposals) | 2 (Manage, Proposals) |
| Distinct sections on page | 4 (Welcome, Listings, House Manuals, Footer) | 5 (Welcome, Stats, Action Banner, Onboarding, Listings) | 3-4 (Top Bar, Urgency Strip, Stats, Listings) |
| Decision points | 8+ (which button? which section?) | 6 (streamlined) | 4 (urgency -> stats -> listings -> action) |
| Vertical scroll required (desktop, 3 listings) | ~3 screens | ~2.5 screens | ~1.5 screens |
| Time to answer "What needs my attention?" | 5-10 sec (scan listing badges) | 3 sec (action banner) | 1-2 sec (urgency strip at top) |

---

*Generated by Agent 1 (How it Works) -- 2026-02-09*
