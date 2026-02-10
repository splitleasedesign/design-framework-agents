# Error Recovery Matrix: Host Overview Dashboard

**Agent:** Agent 1 -- How it Works
**Date:** 2026-02-09
**Subject:** Every failure point, empty state, and edge case with recovery path

---

## Matrix Structure

For each error/failure scenario:
- **Trigger:** What causes this state
- **What the host sees:** The visible result
- **Impact:** How bad is this for the host and business
- **Recovery path:** How the host gets back on track
- **Design requirement:** What the UI must show

---

## Section 1: Empty States (Zero-Data Scenarios)

### ERR-01: No Listings (First-Time Host)

| Field | Value |
|---|---|
| **Trigger** | Host creates account, has never created a listing |
| **What host sees** | Dashboard with no listings, no stats, no proposals |
| **Impact** | HIGH -- if host sees a blank page, they bounce and may never return |
| **Recovery path** | Dashboard shows dedicated empty state with single CTA |
| **Design requirement** | Show: illustration + "You don't have any listings yet." + "Create a listing to start receiving proposals from guests." + large "+ Create Your First Listing" button + secondary "Import from another platform" link. Do NOT show: KPI cards, urgency strip, listing grid. Hide all data-dependent UI. |

### ERR-02: No Earnings (Listing Exists but No Revenue Yet)

| Field | Value |
|---|---|
| **Trigger** | Host has a listing (online or offline) but no accepted proposals yet, so $0 earned |
| **What host sees** | Earnings KPI card shows "$0" |
| **Impact** | MEDIUM -- host may feel discouraged or confused ("Is something broken?") |
| **Recovery path** | KPI card shows "$0" with contextual message instead of empty |
| **Design requirement** | Show: "$0" as the value (not blank, not "--"). Below the value, show: "You'll see earnings here once a proposal is accepted." If listing is offline: add "Your listing is offline -- go online to receive proposals." If listing is incomplete: add "Complete your listing to start receiving proposals." Color: neutral (no red/error styling -- $0 is expected for new hosts). |

### ERR-03: No Proposals (Listing Online, No Guest Interest)

| Field | Value |
|---|---|
| **Trigger** | Host has an online listing but no proposals have been submitted |
| **What host sees** | Proposals KPI card shows "0", no urgency strip, no proposal badges on listing cards |
| **Impact** | MEDIUM -- host may feel their listing is invisible or uncompetitive |
| **Recovery path** | Proposals card shows 0 with encouraging/guidance text |
| **Design requirement** | Show: "0" as the value (not blank). Below: "No proposals yet. Proposals typically arrive within [X] days of going online." If listing has been online > 14 days with 0 proposals: show optimization nudge: "Try adding more photos or adjusting your price." Urgency strip: does not show (nothing to act on). Listing card: "Proposals" button visible but no badge. |

### ERR-04: No Proposals Needing Action (All Proposals Responded To)

| Field | Value |
|---|---|
| **Trigger** | Host has responded to all pending proposals (accepted/declined/countered) |
| **What host sees** | Proposals KPI card shows "0" needing action, urgency strip hidden |
| **Impact** | LOW -- this is the ideal state, host should feel good |
| **Recovery path** | No recovery needed -- this is success |
| **Design requirement** | Show: "0" in Proposals card. Below: "All caught up!" or "No proposals need your attention." Urgency strip: hidden (no items). This is a positive state -- do not show any warning colors. |

### ERR-05: Listing Has No Photos

| Field | Value |
|---|---|
| **Trigger** | Host created a listing but skipped the photo upload step |
| **What host sees** | Listing card shows placeholder instead of photo |
| **Impact** | HIGH -- listings without photos get dramatically fewer proposals |
| **Recovery path** | Placeholder drives host to add photos |
| **Design requirement** | Show: camera icon placeholder with text "Add Photos" (clickable, links to photo upload in listing editor). Completion bar: "60% complete -- Next: Add Photos." If listing is online with no photos: urgency strip: "Your listing [Name] has no photos. Listings with photos get 5x more proposals." Do NOT show: gradient placeholder that looks decorative (current mockup). The placeholder must communicate action needed, not decoration. |

### ERR-06: Listing Has No Description

| Field | Value |
|---|---|
| **Trigger** | Host created a listing but left description empty or default |
| **What host sees** | Listing exists but description field is empty on the detail page |
| **Impact** | MEDIUM -- reduces listing quality, fewer proposals |
| **Recovery path** | Completion bar flags this as next step |
| **Design requirement** | Completion bar on listing card: "[X]% complete -- Next: Add Description." This is not visible from the listing card content (descriptions are too long to preview), so the completion bar is the signal. Inside Manage Listing: Description section shows "No description yet. A good description helps guests understand your space." with edit button. |

### ERR-07: Listing Has No Amenities Selected

| Field | Value |
|---|---|
| **Trigger** | Host skipped amenity selection |
| **What host sees** | "No amenities selected" on listing detail page |
| **Impact** | MEDIUM -- guests filter by amenities; missing amenities = missing from search |
| **Recovery path** | Completion bar + contextual nudge in listing editor |
| **Design requirement** | Completion bar includes amenities as a completion step. Inside Manage Listing: "No amenities selected. Guests filter listings by amenities -- add yours to appear in more searches." Quick-add: checkbox list of common amenities (WiFi, A/C, Washer, etc.) |

---

## Section 2: Loading and Data Errors

### ERR-08: Dashboard Fails to Load (Network Error)

| Field | Value |
|---|---|
| **Trigger** | API call to fetch dashboard data fails (timeout, server error, no internet) |
| **What host sees** | Page partially loads or shows error |
| **Impact** | HIGH -- host cannot access their business data |
| **Recovery path** | Full-page error state with retry |
| **Design requirement** | Show: error illustration + "We couldn't load your dashboard. This might be a temporary issue." + "Try Again" button (refreshes data, not full page reload). + "If this keeps happening, contact support." with support link. Do NOT show: blank page, browser error, or partial data. If header loads but content fails: show error state in the content area only (header stays functional for navigation). Cache: if dashboard was loaded previously in this session, show stale data with banner: "Having trouble connecting. Showing data from [time]. Retrying..." |

### ERR-09: Single Listing Card Fails to Load

| Field | Value |
|---|---|
| **Trigger** | One listing's data fails to fetch while others succeed |
| **What host sees** | N-1 listings load normally; one card is broken |
| **Impact** | MEDIUM -- host can see most data but one listing is inaccessible |
| **Recovery path** | Broken card shows error state with retry option |
| **Design requirement** | Show: listing card shell with: "Couldn't load this listing. [Retry]" link. Do NOT show: the broken card as if it doesn't exist (host would think listing was deleted). Do NOT block other listings from rendering. KPI totals: show with disclaimer if one listing's data is missing: "Totals may be incomplete -- one listing failed to load." |

### ERR-10: Stale Data (Dashboard Shows Outdated Information)

| Field | Value |
|---|---|
| **Trigger** | Data hasn't refreshed due to caching, slow sync, or background job delay. A proposal was submitted but dashboard still shows old count. |
| **What host sees** | Numbers don't match reality (e.g., just accepted a proposal but count hasn't decremented) |
| **Impact** | MEDIUM -- erodes trust in the dashboard's accuracy |
| **Recovery path** | Timestamp + manual refresh option |
| **Design requirement** | Show: "Last updated: [time]" below KPI cards (subtle, gray text). If data is > 5 minutes old: show refresh icon next to timestamp. If data is > 30 minutes old: show yellow warning: "Data may be outdated. [Refresh]". On any action completion (accept proposal, edit listing): auto-refresh dashboard data. Pull-to-refresh on mobile. |

### ERR-11: KPI Data Shows Negative or Anomalous Values

| Field | Value |
|---|---|
| **Trigger** | Refund processed, calculation error, or data corruption causes negative earnings or >100% occupancy |
| **What host sees** | "-$50" in earnings or "112% occupancy" |
| **Impact** | MEDIUM -- confusing and trust-eroding |
| **Recovery path** | Data validation + explanatory text |
| **Design requirement** | If earnings < 0: show "$0" with tooltip: "A recent refund was processed. See all stats for details." Do NOT show negative values on the dashboard. If occupancy > 100%: show "100%" with a note. If any value is clearly anomalous: log the error server-side and show the last known good value with "Data is being verified." |

---

## Section 3: Action Errors

### ERR-12: "Review Proposals" Button Leads to Empty State

| Field | Value |
|---|---|
| **Trigger** | Race condition -- urgency strip says "2 proposals waiting" but by the time host clicks, proposals have been withdrawn or expired |
| **What host sees** | Clicks "Review Now" but proposals page shows no pending proposals |
| **Impact** | LOW-MEDIUM -- confusing but not blocking |
| **Recovery path** | Proposals page shows "no pending proposals" message; dashboard refreshes on return |
| **Design requirement** | Proposals page: "No proposals need your attention right now. This page updates automatically." Back link to dashboard. On return to dashboard: auto-refresh data so urgency strip disappears. Do NOT show: the urgency strip with stale count after host returns. |

### ERR-13: "Manage" Button Fails (Listing Detail Page Error)

| Field | Value |
|---|---|
| **Trigger** | Host clicks "Manage" but the listing detail page fails to load |
| **What host sees** | Error or blank page on listing detail |
| **Impact** | HIGH -- host cannot manage their listing |
| **Recovery path** | Error page with retry and back-to-dashboard option |
| **Design requirement** | Show: "Couldn't load this listing. [Try Again] or [Back to Dashboard]." If the listing was recently deleted by another session: "This listing no longer exists. [Back to Dashboard]." |

### ERR-14: Status Toggle Fails (Online/Offline)

| Field | Value |
|---|---|
| **Trigger** | Host taps status badge to toggle online/offline, but the API call fails |
| **What host sees** | Badge appears to toggle but then reverts (or stays in ambiguous state) |
| **Impact** | HIGH -- host doesn't know if their listing is visible to guests |
| **Recovery path** | Immediate visual feedback + error toast |
| **Design requirement** | On toggle attempt: show loading spinner on the badge. On failure: revert badge to original state + show toast: "Couldn't update listing status. Check your connection and try again." Do NOT leave the badge in an ambiguous state. The badge must always reflect the confirmed server-side state. On success: animate badge to new state + brief "Updated!" confirmation. |

### ERR-15: "Create New Listing" Leads to Incomplete Flow

| Field | Value |
|---|---|
| **Trigger** | Host clicks "+ Create New Listing" but abandons the creation flow partway through (closes tab, navigates away) |
| **What host sees** | On next dashboard visit: either no trace of the attempt, or a phantom incomplete listing |
| **Impact** | MEDIUM -- lost work if no draft saved; confusion if draft appears unexpectedly |
| **Recovery path** | Auto-save draft + clear listing card state |
| **Design requirement** | If draft exists: show listing card with "Draft" status badge (blue) and completion bar at the step where host left off. "Continue" button instead of "Manage." If host explicitly deletes draft: card disappears immediately. If creation flow was abandoned before any data was saved: no trace on dashboard. |

---

## Section 4: Edge Cases by Persona

### ERR-16: First-Time Host Dismisses Empty State Guidance

| Field | Value |
|---|---|
| **Trigger** | First-time host somehow navigates past the empty state without creating a listing (e.g., explores header links first) |
| **What host sees** | Returns to empty dashboard |
| **Impact** | LOW -- empty state is persistent, not dismissible |
| **Recovery path** | Empty state always shows until a listing exists |
| **Design requirement** | The empty state for 0 listings is NOT dismissible. It always shows the CTA. The only way to remove it is to create a listing. This prevents the "blank dashboard" dead-end. |

### ERR-17: Power Host Has 5+ Listings (Grid Overflow)

| Field | Value |
|---|---|
| **Trigger** | Host has 5 or more listings; grid becomes long |
| **What host sees** | Many listing cards requiring significant scroll |
| **Impact** | MEDIUM -- power hosts need to find specific listings quickly |
| **Recovery path** | Sorting + search/filter at scale |
| **Design requirement** | 1-3 listings: no sort/filter needed. 4-5 listings: add sort dropdown (by earnings, by proposals, by name). 6+ listings (future): add search bar + filter by status (Online/Offline). Default sort: listings with proposals first, then by earnings descending. This puts actionable listings at the top. |

### ERR-18: Host on Mobile with Slow Connection

| Field | Value |
|---|---|
| **Trigger** | Host opens dashboard on mobile with 3G or spotty connection |
| **What host sees** | Slow loading, potentially partial content |
| **Impact** | HIGH for mobile hosts -- they may be checking from a property showing or commute |
| **Recovery path** | Progressive loading + skeleton screens |
| **Design requirement** | Load order: (1) Header + page title (instant, cached). (2) Urgency strip (highest priority data, smallest payload). (3) KPI cards (two numbers). (4) Listing card shells (title + status, no images). (5) Listing images (lazy load). (6) Mini-stats in listing cards. Skeleton screens: show gray animated placeholders for each section while loading. Total payload for initial render: < 50KB (excluding images). Images: lazy-loaded, compressed, max 400px wide for mobile. |

### ERR-19: Host Has Listings in Multiple Boroughs/Areas

| Field | Value |
|---|---|
| **Trigger** | Host has listings in Manhattan, Queens, Brooklyn |
| **What host sees** | Listing cards with different location labels |
| **Impact** | LOW -- just needs disambiguation |
| **Recovery path** | Show location only when needed |
| **Design requirement** | If all listings are in the same area: hide location from cards (redundant). If listings are in 2+ areas: show location on all cards for disambiguation. Location should be the neighborhood/borough level, not full address (e.g., "Manhattan" not "124-56 135th Pl, Jamaica, NY 11420"). |

### ERR-20: Host's Listing Was Flagged/Suspended by Platform

| Field | Value |
|---|---|
| **Trigger** | Split Lease suspended a listing due to policy violation, reported issue, or verification requirement |
| **What host sees** | Listing exists but is not Online or Offline -- it's in a third state |
| **Impact** | HIGH -- host's income is affected, they need to understand why and how to fix it |
| **Recovery path** | Clear status badge + explanation + resolution path |
| **Design requirement** | Status badge: "Suspended" (red, exclamation icon). Urgency strip: "Your listing [Name] has been suspended. [View Details]" (high priority, shows above proposals). View Details leads to: explanation of why, what action the host needs to take, timeline for resolution, support contact. The host must never be left wondering why their listing is down. The listing card still shows in the grid (host needs to access it to fix issues). |

### ERR-21: Host Receives a Proposal for an Offline Listing

| Field | Value |
|---|---|
| **Trigger** | Guest submitted a proposal while listing was online; host then took listing offline; proposal is still pending |
| **What host sees** | Listing card shows "Offline" but has a proposal badge |
| **Impact** | LOW-MEDIUM -- confusing but functional |
| **Recovery path** | Clear visual treatment that distinguishes the states |
| **Design requirement** | Listing card: "Offline" badge + proposal badge still visible. Urgency strip still shows the proposal. Inside the proposals view: note that "This listing is currently offline. You can still respond to pending proposals." The host is not blocked from acting on proposals for offline listings. |

### ERR-22: Host's Session Expires While on Dashboard

| Field | Value |
|---|---|
| **Trigger** | Host leaves dashboard tab open, session token expires, they return and try to take action |
| **What host sees** | Action fails (click "Manage" -> redirected to login, or API returns 401) |
| **Impact** | MEDIUM -- interrupts workflow, host may lose context |
| **Recovery path** | Graceful session expiry handling |
| **Design requirement** | On 401 response: show modal overlay (not full redirect): "Your session has expired. [Log In Again]." After re-login: return host to the SAME dashboard state (not homepage). Do NOT redirect to login page and lose the dashboard context. If host was mid-action (toggling status, clicking review): after re-login, complete the action or show the target page. |

---

## Section 5: Summary Table

| ID | Scenario | Severity | Recovery Mechanism |
|---|---------|----------|-------------------|
| ERR-01 | No listings | HIGH | Empty state with CTA |
| ERR-02 | No earnings | MEDIUM | $0 with contextual guidance |
| ERR-03 | No proposals (online listing) | MEDIUM | 0 with guidance/nudge |
| ERR-04 | No proposals needing action | LOW | "All caught up" positive state |
| ERR-05 | No photos | HIGH | Action placeholder + urgency nudge |
| ERR-06 | No description | MEDIUM | Completion bar flag |
| ERR-07 | No amenities | MEDIUM | Completion bar flag |
| ERR-08 | Dashboard load failure | HIGH | Error state with retry |
| ERR-09 | Single listing load failure | MEDIUM | Per-card error with retry |
| ERR-10 | Stale data | MEDIUM | Timestamp + refresh |
| ERR-11 | Anomalous data values | MEDIUM | Validation + fallback display |
| ERR-12 | Proposals gone after click | LOW-MEDIUM | Empty proposals page + auto-refresh |
| ERR-13 | Manage page load failure | HIGH | Error page with retry + back |
| ERR-14 | Status toggle failure | HIGH | Revert + error toast |
| ERR-15 | Abandoned listing creation | MEDIUM | Draft state on card |
| ERR-16 | First-time host bypasses guidance | LOW | Non-dismissible empty state |
| ERR-17 | 5+ listings grid overflow | MEDIUM | Sort/filter controls |
| ERR-18 | Mobile slow connection | HIGH | Progressive loading + skeleton |
| ERR-19 | Multi-area listings | LOW | Conditional location display |
| ERR-20 | Listing suspended | HIGH | Red badge + explanation + resolution |
| ERR-21 | Proposal on offline listing | LOW-MEDIUM | Both badges visible + note |
| ERR-22 | Session expiry | MEDIUM | Modal re-login + state preservation |

---

## Section 6: Edge Cases by Device

### Mobile-Specific Edge Cases

| Scenario | Design Requirement |
|----------|-------------------|
| Fat-finger on status toggle | Confirmation dialog before toggling ("Take listing offline?") |
| Horizontal scroll on listing cards | Cards must not overflow horizontally; single-column stack on mobile |
| Push notification deep link to expired proposal | Show "This proposal is no longer available" with back-to-dashboard |
| Screen reader on KPI cards | ARIA labels: "This month's earnings: $2,847, up 12% from last month" |
| Landscape mode on phone | KPI cards side-by-side, listing cards in 2-column grid |

### Desktop-Specific Edge Cases

| Scenario | Design Requirement |
|----------|-------------------|
| Browser zoom at 150%+ | Layout must not break; listing grid collapses to fewer columns gracefully |
| Multiple tabs with dashboard open | Actions in one tab should not cause stale data in another; use WebSocket or polling for real-time updates |
| Print the dashboard | Print stylesheet: show KPI values, listing names + status, hide interactive elements |

---

*Generated by Agent 1 (How it Works) -- 2026-02-09*
