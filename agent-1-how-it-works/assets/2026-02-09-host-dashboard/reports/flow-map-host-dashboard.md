# Flow Map: Host Overview Dashboard

**Agent:** Agent 1 -- How it Works
**Date:** 2026-02-09
**Subject:** Host Overview Dashboard (Split Lease)
**Source:** Live site screenshots + Don Norman improved mockup (run-002)

---

## 1. Entry Points

| Entry Point | Context | User State |
|---|---|---|
| **Login redirect** | Host logs in via splitlease.com | Returning host, expects to see dashboard immediately |
| **Header nav "Host Overview"** | Host clicks "Host Overview" from any page | Mid-task, switching back to dashboard |
| **Direct URL** | Host bookmarks or types dashboard URL | Variable -- could be first visit or routine check |
| **Mobile deep link** | Push notification (proposal received) | High urgency, narrow task focus |
| **Post-listing-creation redirect** | Host just finished creating a listing | Expects to see their new listing on dashboard |

---

## 2. Current Flow Map (Live Site -- from screenshots)

```
HOST LANDS ON DASHBOARD
|
+-- [A] HEADER BAR
|   +-- Split Lease logo (link to homepage)
|   +-- "Host with Us" dropdown
|   +-- "Host Overview" button (current page, highlighted)
|   +-- Messages icon (envelope)
|   +-- User avatar + name dropdown ("Rod")
|
+-- [B] WELCOME MESSAGE
|   +-- "Welcome back, Rod" (static text)
|
+-- [C] SPECIALIST CO-HOST BANNER
|   +-- "Need help setting up? Ask a Specialist Co-host!"
|   +-- Dismiss (X) button
|
+-- [D] PRIMARY ACTION BUTTONS
|   +-- "+ Create New Listing" (primary CTA)
|   +-- "Import Listing" (secondary CTA)
|
+-- [E] YOUR LISTINGS SECTION
|   +-- Section title: "Your Listings"
|   +-- For EACH listing (repeated card):
|       +-- Listing thumbnail (or placeholder icon)
|       +-- Listing title (e.g., "Stylish Private Room In Vibrant Neighborhood")
|       +-- Location text (e.g., "Location not specified" or "Manhattan")
|       +-- Delete icon (trash can)
|       +-- "Manage Listing" button
|       +-- "Preview" button
|       +-- "Proposals" button + badge count (e.g., "2")
|       +-- "Leases" button + badge count (e.g., "1")
|       +-- "Create House Manual" link
|
+-- [F] HOUSE MANUALS SECTION
|   +-- Section title: "House Manuals"
|   +-- "+ Create New Manual" button
|   +-- Empty state: "You don't have any house manuals yet."
|
+-- [G] FOOTER
    +-- Company links (About, Periodic Tenancy, About the Team, etc.)
    +-- For Hosts links (List Property Now, How to List, Success Stories, etc.)
    +-- Refer a Friend ("Give $50, Get $50", Invite Friends button)
    +-- Import Your Listing (paste URL + email, Import Now)
    +-- App Store / Amazon Appstore download banners
    +-- Terms / Privacy / Copyright
```

---

## 3. Current Flow Map (Don Norman Improved Mockup)

```
HOST LANDS ON DASHBOARD
|
+-- [A] HEADER BAR
|   +-- Split Lease logo
|   +-- "Host Overview" link
|   +-- "Messages" link
|   +-- User avatar ("R")
|
+-- [B] WELCOME SECTION
|   +-- Left: "Welcome back, Rod" + "Here's what's happening with your listings today"
|   +-- Right: "+ Create New Listing" button + "Import Listing" button
|
+-- [C] STATS DASHBOARD (2 KPI cards -- HOD-1)
|   +-- Card 1: "This Month's Earnings"
|   |   +-- Value: "$2,847"
|   |   +-- Change: "+12% vs last month . 78% occupancy"
|   |   +-- "See all stats" link
|   +-- Card 2: "Proposals Needing Action"
|       +-- Value: "2"
|       +-- Detail: "3 total pending . 4.9 avg rating"
|
+-- [D] ACTION REQUIRED BANNER
|   +-- Warning icon (!)
|   +-- "2 proposals need your attention"
|   +-- Detail: "Leo Di Caprio submitted a new proposal for Sunny Private Room"
|   +-- "Review Proposals" button (with loading state -- HOD-5)
|
+-- [E] ONBOARDING SECTION (dismissible -- HOD-2)
|   +-- Dismiss (X) button
|   +-- "Complete Your Host Profile" title
|   +-- Progress: "3 of 5 steps completed"
|   +-- 5 step indicators:
|   |   +-- Step 1: Create Listing (completed, checkmark)
|   |   +-- Step 2: Add Photos (completed, checkmark)
|   |   +-- Step 3: Set Pricing (completed, checkmark)
|   |   +-- Step 4: House Manual (pending, clipboard icon)
|   |   +-- Step 5: Go Live (pending, checkmark icon)
|   +-- Next step hint: "Add a House Manual to help guests understand..." (HOD-3)
|
+-- [F] YOUR LISTINGS SECTION
    +-- Section header: "Your Listings" + "3 listings"
    +-- Grid of listing cards:
        +-- For EACH listing:
            +-- Image placeholder with gradient
            +-- Status badge with icon: "Online" (green, checkmark) or "Offline" (gray, pause) -- HOD-6
            +-- Listing title
            +-- Location
            +-- Mini stats row:
            |   +-- This Month ($)
            |   +-- Occupancy (%)
            |   +-- Proposals (count)
            +-- Action buttons:
                +-- "Manage" (primary)
                +-- "Proposals" + badge count (secondary)
```

---

## 4. Current Flow Map (Listing Dashboard -- from screenshot 02)

When a host clicks "Manage Listing" from the overview, they reach a single-listing detail dashboard:

```
LISTING DASHBOARD
|
+-- [A] HEADER (same as overview)
|
+-- [B] SUB-NAVIGATION TABS
|   +-- "All My Listings"
|   +-- "Proposals" (with badge)
|   +-- "Give $50, Get $50" (referral CTA)
|
+-- [C] SPECIALIST CO-HOST BANNER (repeated)
|
+-- [D] QUICK ACTIONS
|   +-- "Preview Listing"
|   +-- "Copy Listing Link"
|   +-- "Proposals" link
|
+-- [E] AI IMPORT ASSISTANT + "Choose a Section" selector
|
+-- [F] LISTING DETAILS (single long page, scrollable sections):
|   +-- Listing title + edit button
|   +-- "Import reviews from other sites" link
|   +-- Address
|   +-- Status: "Listing is offline" / online indicator
|   +-- Active since date
|   +-- Description of Lodging (edit)
|   +-- Neighborhood Description (edit) -- often empty
|   +-- Amenities (edit) -- often empty
|   +-- Details (edit): Type, bedrooms, bathrooms, sq.ft., etc.
|   +-- Safety Features -- often empty
|   +-- Pricing and Lease Style (edit):
|   |   +-- Lease style (Nightly)
|   |   +-- Nights/Week selector
|   |   +-- Weekly Total by Occupancy table
|   |   +-- Additional Charges (Damage Deposit, Maintenance Fee)
|   |   +-- "Edit Pricing & Lease Style" button
|   +-- Rules (edit) -- often empty
|   +-- Listing Availability:
|   |   +-- Ideal Lease Term slider
|   |   +-- Earliest available date
|   |   +-- Check In / Check Out times
|   |   +-- Calendar with blocked dates
|   +-- Photos (Add Photos)
|   +-- Cancellation Policy (Standard)
|
+-- [G] FOOTER (same as overview)
```

---

## 5. Decision Points (User Decisions on Dashboard)

| # | Decision | Options | Typical Choice |
|---|----------|---------|----------------|
| D1 | What do I check first? | Earnings / Proposals / Listings | Proposals (time-sensitive) |
| D2 | Which listing needs attention? | Scan listing cards for badges/alerts | One with proposal badge |
| D3 | Should I respond to a proposal? | Review Proposals / Ignore | Review (business value) |
| D4 | Is my listing complete? | Check onboarding steps | Complete next step |
| D5 | Should I create a new listing? | Create New / Import / Neither | Usually neither (routine visit) |
| D6 | Do I need to manage a listing? | Manage specific listing / Stay on overview | Depends on task |
| D7 | Should I dismiss onboarding? | Dismiss / Complete steps / Ignore | Ignore (banner blindness risk) |
| D8 | Is my listing online/offline? | Take action to toggle / Leave as-is | Check then leave |

---

## 6. Actions Available (Full Inventory)

| # | Action | Location | Destination |
|---|--------|----------|-------------|
| A1 | Create New Listing | Welcome section buttons | Listing creation flow |
| A2 | Import Listing | Welcome section buttons | Import flow (paste URL) |
| A3 | Review Proposals | Action banner button | Proposals page/modal |
| A4 | Dismiss Onboarding | Onboarding X button | Hides onboarding section |
| A5 | Complete Onboarding Step | Click onboarding step | That step's edit page |
| A6 | Manage Listing | Listing card button | Listing detail/edit page |
| A7 | View Proposals (per listing) | Listing card "Proposals" button | Proposals for that listing |
| A8 | See All Stats | Stats card link | Full analytics page |
| A9 | Navigate to Messages | Header "Messages" link | Messages inbox |
| A10 | Navigate to Host Overview | Header "Host Overview" link | Current page (no-op) |
| A11 | Access User Menu | Header avatar | Profile, settings, logout |

---

## 7. Information Displayed (Full Inventory)

| # | Data Element | Location | Purpose |
|---|-------------|----------|---------|
| I1 | Host name | Welcome section | Personalization / confirmation of logged-in identity |
| I2 | Summary text ("Here's what's happening...") | Welcome section | Contextual framing |
| I3 | This Month's Earnings (aggregate) | Stats card | Answer "How much am I making?" |
| I4 | % change vs last month | Stats card | Trend awareness |
| I5 | Aggregate occupancy % | Stats card | Performance indicator |
| I6 | Proposals needing action (count) | Stats card | Answer "What needs my attention?" |
| I7 | Total pending proposals | Stats card | Context for action count |
| I8 | Average rating | Stats card | Reputation indicator |
| I9 | Action banner text | Action banner | Urgency signal for proposals |
| I10 | Specific proposal detail | Action banner | Who submitted, which listing |
| I11 | Onboarding progress (X of Y) | Onboarding section | Completion awareness |
| I12 | Next step hint | Onboarding section | Reduces decision cost |
| I13 | Listing title | Listing card | Identify which listing |
| I14 | Listing location | Listing card | Disambiguate listings |
| I15 | Listing status (Online/Offline) | Listing card badge | Is this listing visible to guests? |
| I16 | Per-listing monthly earnings | Listing card mini-stats | Per-listing performance |
| I17 | Per-listing occupancy % | Listing card mini-stats | Per-listing performance |
| I18 | Per-listing proposal count | Listing card mini-stats | Per-listing activity |
| I19 | Total listing count | Section header | Portfolio size awareness |

---

## 8. Exit Points

| Exit Point | Trigger | Where Host Goes |
|---|---|---|
| Manage Listing | Click "Manage" on listing card | Listing detail/edit page |
| View Proposals | Click "Proposals" or "Review Proposals" | Proposals page/list |
| Create Listing | Click "+ Create New Listing" | Listing creation wizard |
| Import Listing | Click "Import Listing" | Import flow |
| See All Stats | Click "See all stats" link | Analytics/stats page |
| Messages | Click "Messages" in header | Messages inbox |
| Onboarding Step | Click incomplete step | That step's edit form |
| Profile/Settings | Click avatar dropdown | User settings |
| Logout | Avatar dropdown > Logout | Login page |

---

## 9. Differences: Live Site vs. Don Norman Mockup

| Element | Live Site | Don Norman Mockup |
|---------|-----------|-------------------|
| Stats/KPIs | None visible on overview | 2 KPI cards (earnings + proposals) |
| Action Banner | None | Warning banner with proposal urgency |
| Onboarding | None visible (maybe completed) | Dismissible 5-step progress tracker with next-step hint |
| Listing Cards | Flat list with buttons | Grid cards with images, mini-stats, status badges |
| House Manuals | Separate section below listings | Integrated into onboarding step |
| Status Badges | Not visible | Color + icon badges (Online/Offline) |
| Specialist Co-host | Dismissible info banner | Not present in mockup |
| Footer | Full footer with referral, import, app download | Not present in mockup |
| Listing Actions | Manage, Preview, Proposals, Leases, Create House Manual | Manage, Proposals |
| Delete Button | Trash icon on each listing | Not present |

---

*Generated by Agent 1 (How it Works) -- 2026-02-09*
