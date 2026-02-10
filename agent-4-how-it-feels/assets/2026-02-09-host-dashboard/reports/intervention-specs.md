# Intervention Specs: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Journey: Host Dashboard
Purpose: Exact copy, animation, timing, and micro-interaction specifications for each intervention.

---

## INT-1: Dynamic Welcome Subtitle

**Component:** `.welcome-text p` (currently: "Here's what's happening with your listings today")

### Copy Strings (Priority Order)
The system evaluates top-to-bottom and shows the first match:

1. **Urgent proposals (>24h old):**
   "You have 2 proposals waiting — the oldest is from 2 days ago."

2. **New proposals (<24h old):**
   "2 guests are interested in your space. Take a look when you're ready."

3. **Onboarding incomplete:**
   "You're 2 steps away from going live. Let's get you there."

4. **Earnings positive, proposals zero:**
   "Your listings earned $2,847 this month — up 12% from January."

5. **Earnings zero, listing live:**
   "Your listing is live and visible to guests in Manhattan."

6. **Earnings zero, listing not yet live:**
   "Let's finish setting up so guests can find your space."

7. **Default (all running, no action needed):**
   "All 3 listings are online and running smoothly."

### Animation
- **Transition:** Fade-in on page load, 200ms ease-out, 100ms delay after header renders.
- **On data refresh:** Crossfade to new text if status changes (300ms).
- **No animation on return visits within same session** (avoid repetitive motion).

### Timing
- Subtitle text is generated server-side on page load.
- Updates if the host performs an action that changes state (e.g., responds to a proposal).
- Does NOT auto-refresh while the host is on the page (no jarring text changes).

---

## INT-2: Earnings Card — Zero State Replacement

**Component:** `.stat-card.earnings` when earnings = $0

### Current State (to remove)
```
$0
```
Shown in 40px bold font. No context. No guidance.

### Replacement Copy

**Primary message (replaces the $0 value):**
"Your first earning is on its way"
- Font: 22px, semi-bold (not 40px bold — reduce the visual weight)
- Color: var(--color-neutral-900)

**Sub-message (replaces the "+12% vs last month" line):**

If listing has views:
"Your listing has been viewed {X} times this week. Guests are noticing."

If listing has no views (brand new):
"You listed on {date}. Most hosts see their first proposals within 2 weeks."

If listing is not yet live:
"Once your listing is live, you'll start seeing views and proposals here."

**"See all stats" link:** Keep visible. Leads to full stats page where the host can see views, impressions, and search ranking even with zero earnings.

### Animation
- **On first load (zero state):** Gentle pulse animation on the sub-message text (opacity 0.7 to 1.0, 2s cycle, 2 repetitions, then static). This draws the eye to the reassurance text.
- **Transition to non-zero:** When the host's first earning posts, the card transitions from the narrative to the number with a celebration micro-animation (confetti burst, 1.5s, contained within the card boundaries). See INT-SUCCESS-1.

### Timing
- Zero-state message shows immediately on page load.
- Sub-message updates on each visit (views count is recalculated).
- Celebration triggers once — on the first visit after first earning posts. Flag stored in localStorage to prevent repeat.

---

## INT-3: Proposal Banner Reframe

**Component:** `.action-banner` (currently: yellow warning gradient with "!" icon)

### Visual Changes
- **Background:** Change from `linear-gradient(135deg, var(--color-warning-bg) 0%, #FFF3CD 100%)` to `linear-gradient(135deg, var(--color-primary-bg) 0%, #E8E0F5 100%)`
- **Border:** Change from `1px solid var(--color-warning)` to `1px solid var(--color-primary-light)`
- **Icon:** Replace "!" alarm icon with a person-plus silhouette icon (represents "new guest interest"). Background color: `var(--color-primary-light)`.

### Copy Changes

**Headline (currently: "2 proposals need your attention"):**
New: "2 guests are interested in your space"

**Sub-text (currently: "Leo Di Caprio submitted a new proposal for Sunny Private Room"):**
New: "Leo submitted a proposal for Sunny Private Room. Take a look when you're ready."
- Use first name only (familiar, human).
- "Take a look when you're ready" replaces the implied urgency.

**If response deadline approaching (within 12 hours):**
"Leo submitted a proposal for Sunny Private Room. Respond by tomorrow so they can finalize their plans."
- Factual deadline, not pressure.

**CTA button (currently: "Review Proposals"):**
New: "See Who's Interested"
- Background: var(--color-primary) (keep purple, not warning yellow).

### Animation
- **Banner entrance:** Slide-down from top, 250ms ease-out. Appears after the stat cards have loaded (staggered, 400ms delay from page load).
- **CTA hover:** Gentle scale-up (1.02x, 150ms ease-in-out). No color change — the button is already prominent.
- **CTA click loading state:** Keep existing HOD-5 spinner. Change "See Who's Interested" to spinner. After load, redirect to proposals page.

### Timing
- Banner only appears when there are proposals needing action (proposals > 0 pending response).
- When all proposals are responded to, the banner fades out (300ms fade) and the space collapses.
- On return visit after responding to all proposals: banner is gone, and the welcome subtitle updates to reflect new status.

---

## INT-4: Onboarding Section Reframe

**Component:** `.onboarding-section`

### Copy Changes

**Title (currently: "Complete Your Host Profile"):**
New: "You're Almost Ready to Welcome Guests"

**Progress text (currently: "3 of 5 steps completed"):**
New: "3 of 5 steps done — you're more than halfway there"

**Step labels (keep existing):**
1. Create Listing (completed)
2. Add Photos (completed)
3. Set Pricing (completed)
4. House Manual (pending)
5. Go Live (pending)

**Next-step hint (currently: "Add a House Manual to help guests understand your space rules and amenities."):**
New: "Next up: House Manual (about 5 minutes). Guests love knowing what to expect — this step helps you get better proposals."

### Time Estimates (add to each pending step)
- House Manual: "~5 min"
- Go Live: "~1 min"

These appear as small labels below the step icon on pending steps.

### Animation
- **Completed step checkmarks:** Green checkmark icon scales from 0 to 1 with a bounce (300ms, cubic-bezier(0.68, -0.55, 0.265, 1.55)) when the step is first completed. On subsequent views, checkmarks are static.
- **Current step highlight:** The next pending step has a soft pulsing border (opacity 0.3 to 0.6, 2s cycle) to draw attention.
- **Progress bar:** Under the title, add a thin progress bar (60% filled for 3/5). Bar color: var(--color-success). Bar fills left-to-right on page load (500ms ease-out).

### Timing
- Onboarding section appears only for hosts with incomplete onboarding.
- The dismiss button (HOD-2) is retained. If dismissed, onboarding collapses.
- After dismissal, a small "Resume setup" link appears in the welcome section subtitle: "You're 2 steps from going live. [Resume setup]."
- After all 5 steps complete, onboarding transitions to a celebration state (see INT-SUCCESS-2) then auto-dismisses after 10 seconds.

---

## INT-5: Offline Badge with Reason + Fix

**Component:** `.listing-status.offline` on listing cards

### Copy Strings

**Badge (keep):** "Offline" (with pause icon)

**Reason line (new, below the badge or below listing title):**

Reason: Missing house manual
"Offline — add a house manual to go live. [Add now]"

Reason: Missing photos
"Offline — add at least one photo to go live. [Add photos]"

Reason: Missing pricing
"Offline — set your pricing to go live. [Set pricing]"

Reason: Paused by host
"Paused by you. [Resume listing]"

Reason: Under platform review
"Under review — we're checking a few details. This usually takes 1-2 business days."

Reason: Multiple items missing
"Offline — complete 2 remaining items to go live. [See what's needed]"

### Visual Specs
- Reason line appears directly below the listing title, in 12px regular weight, color: var(--color-neutral-600).
- Action link: color: var(--color-primary), underline on hover.
- The reason line replaces the location text when the listing is offline (location moves to a second line).

### Animation
- **Reason line entrance:** Fade-in, 200ms, appears with the card on page load. No special animation — this is informational, not celebratory.
- **Action link click:** Standard button loading state (opacity 0.6 during navigation).

### Timing
- The reason is determined server-side and passed with the listing data.
- The action link navigates to the specific section of the listing editor that needs completion (deep link, not just the listing page).
- After the host completes the fix and returns to the dashboard, the badge should update to "Online" with a brief green flash (200ms, background-color transition from neutral to success-bg).

---

## INT-6: Empty State Replacement System

**Component:** All zero-state displays across dashboard and listing editor.

Full copy strings are in `copy/empty-states.md`. Here are the interaction specs:

### Visual Template for Empty States
```
[Icon: contextual, 32x32, color: var(--color-primary-light)]
[Headline: 16px semi-bold, color: var(--color-neutral-900)]
[Body: 14px regular, color: var(--color-neutral-600)]
[Action link: 14px semi-bold, color: var(--color-primary)]
```

### Animation
- **Entrance:** Fade-in, 200ms, staggered per empty state (100ms between each).
- **Action link hover:** Text color intensifies to var(--color-primary-dark), 150ms transition.
- **After action completed:** Empty state crossfades to the real content (300ms). The empty-state message is replaced by the actual data.

### Timing
- Empty states show immediately on page load. No loading skeleton for empty states (skeletons imply content is coming; empty states imply no content exists yet).
- If the host completes the action (e.g., adds a photo) and returns to the dashboard, the empty state is gone and the real content shows. No animation — just present the content.

---

## INT-7: Action Button Clarity

**Component:** `.listing-actions .btn` (currently: "Manage" and "Proposals")

### Copy Changes
- "Manage" becomes "Edit Listing"
- "Proposals" stays "Proposals" (with badge count)

### New Host Tooltip (first 30 days)
On first dashboard visit, the "Edit Listing" button shows a tooltip:
"Edit your listing details, photos, and pricing. Nothing saves until you confirm."
- Tooltip style: Dark background (var(--color-neutral-900)), white text, 12px, 8px padding, 4px radius.
- Tooltip position: Above button, centered, with arrow pointing down.
- Dismiss: Click anywhere or click the button. Stored in localStorage — shows once per listing.

### Power Host Enhancement
For hosts with 4+ listings, the proposals button shows age context:
"Proposals (oldest: 2d ago)" — the "2d ago" is in lighter text.
This helps power hosts prioritize which listing to review first.

### Animation
- **Tooltip:** Fade-in, 200ms, 500ms delay after page load.
- **Tooltip dismissal:** Fade-out, 150ms.
- **Button hover:** Existing transition (all 0.2s) is sufficient. No changes.

---

## INT-8: Referral Banner Maturity Gate

**Component:** Referral banner ("Give $50, Get $50") — currently visible to all hosts.

### Display Logic
```
if (host.completed_bookings === 0) {
  // Do not show referral banner
  return null;
}

if (host.completed_bookings === 1 && !host.has_seen_referral_banner) {
  // Show celebratory referral intro
  return REFERRAL_FIRST_BOOKING;
}

if (host.completed_bookings >= 2) {
  // Show standard referral banner
  return REFERRAL_STANDARD;
}
```

### Copy Strings

**REFERRAL_FIRST_BOOKING:**
Headline: "Your first guest had a great experience."
Body: "Know someone with a great space? Invite them to host on Split Lease. You'll both earn $50 when they welcome their first guest."
CTA: "Invite a Friend to Host"

**REFERRAL_STANDARD:**
Headline: "Grow the community, earn $50"
Body: "For every friend who hosts their first guest, you both get $50. No limit."
CTA: "Share Your Invite Link"

### Animation
- **REFERRAL_FIRST_BOOKING entrance:** Slide-up from bottom of dashboard, 300ms ease-out, appears 2 seconds after page load (so the host sees their dashboard first, then the referral as an afterthought).
- **REFERRAL_STANDARD:** No entrance animation (persistent element).
- **Dismiss:** X button in top-right. Fade-out, 200ms. Stored in localStorage — dismissed for 30 days, then resurfaces.

### Timing
- Referral banner checks host.completed_bookings on page load.
- REFERRAL_FIRST_BOOKING shows only once (after first booking). If dismissed, transitions to REFERRAL_STANDARD on next visit.
- REFERRAL_STANDARD appears on every visit but can be dismissed for 30 days.

---

## INT-SUCCESS-1: First Earnings Celebration

**Trigger:** Host visits dashboard for the first time after their first earning posts.

### Copy
Headline in earnings card: "${amount}"
Sub-text: "You just earned your first payout on Split Lease. This is just the beginning."

### Animation
- Earnings card gets a 1.5-second celebration:
  - Card background briefly flashes to var(--color-success-bg) (200ms in, 200ms hold, 500ms fade back to white).
  - Small confetti burst inside the card (CSS-only, 8 particles, contained within card boundaries, 1.5s total).
  - The dollar amount counts up from $0 to the actual amount (1s, ease-out).
- **Important:** Celebration is contained, brief, and does not block interaction. No modal, no overlay, no forced pause.

### Timing
- Triggered once. Flag in localStorage: `first_earnings_celebrated = true`.
- If the host navigates away before seeing it, it triggers on next visit.

---

## INT-SUCCESS-2: Onboarding Completion Celebration

**Trigger:** Host completes the 5th (final) onboarding step and returns to dashboard.

### Copy
Onboarding section transforms:
Title: "You're all set! Your listing is live."
Body: "Guests in Manhattan can now find and book your space. We'll notify you when you get your first proposal."
CTA: "View Your Live Listing"

### Animation
- All 5 step icons pulse green simultaneously (200ms).
- Title crossfades from "You're Almost Ready to Welcome Guests" to "You're all set! Your listing is live." (300ms).
- After 10 seconds, onboarding section smoothly collapses (400ms height transition to 0, with overflow hidden).
- On next visit, onboarding section is gone.

### Timing
- Celebration state persists for one dashboard visit.
- After celebration, onboarding section is permanently removed from this host's dashboard.
- A subtle "Setup complete" checkmark appears in the header nav for 7 days (reinforcement).
