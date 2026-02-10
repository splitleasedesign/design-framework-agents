# Alternatives Considered: Adversarial Architect Analysis

Agent: 4 (How it Feels)
Date: 2026-02-09
Journey: Host Dashboard
Method: For each HIGH/CRITICAL gap, 3 intervention approaches generated, failure-analyzed, and one selected.

---

## Gap 1: Welcome Message (HIGH)

### Approach A: Dynamic Status Summary
Replace the static subtitle "Here's what's happening with your listings today" with a real-time, context-aware one-liner that summarizes the most important dashboard state.

**Examples:**
- "You have 2 new proposals waiting — your listings are getting attention."
- "Your earnings are up 12% this month. Nice work."
- "All 3 listings are online and running smoothly."

**How it could fail:** Requires a priority hierarchy when multiple states are active simultaneously (new proposals AND earnings up AND onboarding incomplete). If the logic is wrong, the summary could highlight the wrong thing — e.g., showing earnings growth to a host who has an urgent proposal expiring in 2 hours. Also, if the data feed is delayed, the summary could be stale and erode trust.

### Approach B: Persona-Adaptive Welcome
Show a different welcome message structure per persona. New hosts get a warm, reassuring message. Active hosts get a motivation-focused message. Power hosts get a data-dense status line.

**Examples:**
- New host: "Welcome back, Rod. Your listing is live and visible to guests in Manhattan."
- Active host: "Good evening, Rod. $2,847 earned this month — up 12%."
- Power host: "Rod: 3 listings online, 2 proposals pending, $2,847 MTD."

**How it could fail:** Persona detection based on listing count or tenure may miscategorize hosts. A host with 4 listings who just started last week is technically a "power host" by listing count but emotionally a "new host." Also, maintaining 3 parallel copy systems increases maintenance cost and risk of inconsistency.

### Approach C: Contextual Greeting Card
Replace the text-only welcome with a small card that shows a time-of-day greeting plus the single most actionable item, with a direct-action button.

**Examples:**
- Morning: "Good morning, Rod. 2 guests are interested in your space." [See proposals]
- Evening: "Good evening, Rod. Your listings earned $143 today." [View earnings]

**How it could fail:** The card format takes more vertical space, pushing listings and stats below the fold. On mobile, this could mean hosts need to scroll to see their actual content. Also, the "single most actionable item" logic could feel random if the host came to the dashboard with a different intent (e.g., they want to check earnings but the card shows proposals).

### Selected: Approach A (Dynamic Status Summary)
**Rationale:** Approach A preserves the existing layout (minimal UI change), provides the highest information density in the least space, and addresses the core gap (the subtitle is a dead sentence). The priority hierarchy risk is mitigable with a simple ranking: (1) urgent proposals > (2) onboarding incomplete > (3) earnings summary > (4) "all running smoothly" fallback. Approach B's persona detection is fragile. Approach C's increased vertical footprint harms mobile.

---

## Gap 2: Earnings Stats — Zero State (CRITICAL)

### Approach A: Replace Zero with Progress Narrative
Never show "$0" in the earnings card. Instead, show a progress-oriented message: "Your first earning is on its way" with a subtle metric below (listing views, search impressions, or proposals received) that proves the listing is working even before money comes in.

**Examples:**
- "Your first earning is on its way. Your listing has been viewed 23 times this week."
- "No bookings yet. 4 guests have viewed your listing — you're getting noticed."

**How it could fail:** If the listing also has zero views (brand new, not yet indexed), the progress narrative has nothing to attach to, and the message feels hollow. Also, hosts who understand marketplaces may see "23 views with 0 bookings" as a bad conversion rate rather than encouragement.

### Approach B: Expectation-Setting Timeline
Show a timeline graphic: "Most new listings get their first booking within 2-3 weeks." Place a marker showing where the current host is on that timeline. This normalizes the zero-earnings period as expected.

**Examples:**
- Visual: A small timeline bar with "Listed Feb 5" on the left, "First booking (avg: 2-3 weeks)" in the middle, "Today" marker showing progress.
- Text: "You're in Week 1. Most hosts earn their first booking by Week 3."

**How it could fail:** The "2-3 weeks" average may not be accurate for all markets or listing types. If a host hits Week 4 with no bookings, the timeline becomes a source of anxiety rather than comfort ("I'm behind the average"). Also, this requires reliable historical data to set honest expectations.

### Approach C: Social Proof Earnings Ramp
Show what typical hosts in this area earn at 1 month, 3 months, and 6 months. Frame the current zero as the natural starting point of a growth curve.

**Examples:**
- "Manhattan hosts typically earn $800-1,200/month in their first 3 months. Your listing is off to a strong start with 23 views in Week 1."
- Small sparkline chart showing a typical earnings ramp from $0 to average.

**How it could fail:** If the host's listing is poorly set up (no photos, bad pricing), the social proof could set expectations they won't meet, leading to greater disappointment later. Also, showing other hosts' earnings could trigger comparison anxiety rather than motivation.

### Selected: Approach A (Replace Zero with Progress Narrative) with fallback from Approach B
**Rationale:** Approach A directly addresses the core problem (bare "$0" in large font) and replaces it with proof of progress. The failure case (zero views) is handled by falling back to Approach B's timeline framing: "You listed on Feb 5. Most hosts see their first proposals within 2 weeks." Approach C's social proof is risky for underperforming listings and could amplify inadequacy rather than reduce it.

---

## Gap 3: Proposal Notifications (HIGH)

### Approach A: Reframe from Warning to Opportunity
Change the visual language: replace the yellow warning banner with a calm blue/purple opportunity card. Change "2 proposals need your attention" to "2 guests are interested in your space." Replace the (!) icon with a guest avatar silhouette or a subtle sparkle icon. Change "Review Proposals" to "See Who's Interested."

**How it could fail:** Reducing urgency too much could lower response rates. If hosts don't feel the proposals are time-sensitive, they may procrastinate, leading to guest frustration and lost bookings. The sparkle icon could feel frivolous.

### Approach B: Add Response Window Context
Keep the current urgency framing but add context that reduces anxiety: "2 proposals need your attention. You have 48 hours to respond — no rush." This acknowledges the time-sensitivity without creating panic.

**How it could fail:** "No rush" may feel condescending to power hosts. The 48-hour window, while meant to relieve pressure, could also start a mental countdown timer that creates time anxiety. Also, if the policy changes, hardcoded timeframes become misleading.

### Approach C: Social Proof + Opportunity Frame
Combine opportunity framing with social proof: "2 guests are interested in your space. Hosts who respond within 24 hours are 3x more likely to get bookings." This motivates quick action through positive framing rather than obligation.

**How it could fail:** Social proof creates implicit pressure — the host may feel guilty if they can't respond within 24 hours. The "3x more likely" statistic must be real and verifiable; if hosts discover it's fabricated, trust collapses. Also, this is borderline manipulation — using a statistic to pressure behavior is a softer version of "Respond NOW!"

### Selected: Approach A (Reframe from Warning to Opportunity)
**Rationale:** The core problem is that good news (someone wants your space) is being presented as a problem (needs your attention). Approach A directly fixes this by changing the visual and verbal framing. Approach B keeps the urgency framing and just adds a band-aid. Approach C introduces social proof pressure that borders on manipulation — using statistics to drive behavior is a dark pattern even when the stat is real. Approach A is the cleanest solution: present good news as good news.

**Compromise:** Add a gentle time context without "no rush" language. Instead: "Respond by Feb 12 so guests can finalize their plans." This is factual, not pressuring.

---

## Gap 4: Onboarding Progress (HIGH)

### Approach A: Progress-First Framing
Change the title from "Complete Your Host Profile" (task-focused) to "You're Almost Ready to Earn" (goal-focused). Add time estimates to remaining steps. Change the next-step hint to include a motivational bridge explaining why the step matters.

**Examples:**
- Title: "You're Almost Ready to Earn"
- Progress: "3 of 5 steps done — just 2 more to go"
- Next step: "Next up: House Manual (about 5 min). Guests love knowing what to expect — this step helps you get better proposals."

**How it could fail:** "You're Almost Ready to Earn" could set false expectations. Completing onboarding doesn't guarantee earnings — it just makes the listing live. If a host finishes all steps and still gets no bookings, the promise feels broken.

### Approach B: Gamified Progress with Micro-Celebrations
Add a completion percentage (60%), celebrate each completed step with a brief animation (checkmark burst), and show a "completion reward" — e.g., "Complete all steps to unlock Priority Placement for your first week."

**How it could fail:** Gamification can feel patronizing to experienced users. The "completion reward" could be perceived as manipulative (withholding a feature to force behavior). If the animation is too playful for a financial platform, it undermines trust. Also, the reward promise must be deliverable — if priority placement doesn't actually exist, this is a lie.

### Approach C: Social Proof Progress
Show how the host compares to others: "You're ahead of 65% of new hosts — most are still on Step 2." This uses competitive motivation to drive completion.

**How it could fail:** Comparison with other hosts creates competitive anxiety. If the host is behind ("You're behind 70% of hosts"), it's demoralizing. The percentage must be real and updated, creating a data dependency. Also, some hosts may not care about other hosts and find this irrelevant.

### Selected: Approach A (Progress-First Framing)
**Rationale:** Approach A reframes without introducing new psychological mechanisms (gamification, competition). It addresses the core issue: the current framing feels like homework, the new framing feels like progress toward a goal. The "false promise" risk is mitigated by changing "Ready to Earn" to "Ready to Welcome Guests" — which is true (completing onboarding makes you live). Approach B's gamification and rewards create promises the platform may not keep. Approach C's competitive framing introduces comparison anxiety.

---

## Gap 5: Listing Status Badges — Offline State (HIGH)

### Approach A: Inline Reason + Fix Link
Below the "Offline" badge, add a single line explaining why and a direct action link: "Offline — missing house manual. [Add it now]" This turns confusion into a clear, one-step resolution.

**How it could fail:** The reason may be complex (multiple missing items) and hard to compress into one line. If the reason is "Paused by admin" or "Under review," the host may feel punished, and the tone needs to be carefully handled. Also, showing the reason on the card may create visual clutter on the listings grid.

### Approach B: Offline Status Page
Keep the badge simple ("Offline") but make it clickable, leading to a dedicated status page that explains the reason, shows what's needed, and provides a "Go Live" checklist. This keeps the card clean but adds a click.

**How it could fail:** The extra click adds friction. New hosts in a state of confusion may not think to click the badge — they might just stare at it and worry. The status page is additional UI to build and maintain. For power hosts managing many listings, having to click into each one is inefficient.

### Approach C: Traffic Light System
Replace the binary Online/Offline with a three-state system: Green (Online, receiving guests), Yellow (Almost ready — 1-2 items to complete), Red (Offline — needs attention). This provides gradation and makes "almost there" feel less severe than "off."

**How it could fail:** Three states increase cognitive load. Hosts may not understand the difference between Yellow and Red. The Yellow state could create a false sense of safety ("It's yellow, not red, so it's fine") when the listing is actually not receiving guests. Also, color-only systems have accessibility issues even with icons.

### Selected: Approach A (Inline Reason + Fix Link)
**Rationale:** The core need is answering "Why is it offline?" and "What do I do?" in the least possible friction. Approach A does both in a single visible line without requiring a click. The clutter risk is acceptable because the offline state is relatively rare (most listings are online) and the information is critical when present. For complex reasons, show the primary blocker only: "Offline — complete 2 remaining items to go live. [See what's needed]." Approach B adds unnecessary friction. Approach C over-engineers the status system.

---

## Gap 6: Empty States (CRITICAL)

### Approach A: Contextual Guidance Messages
Replace every "No X" and bare-zero with a message that (1) normalizes the empty state, (2) explains why X matters, and (3) provides a direct action. Customize per field.

**Examples:**
- No proposals: "No proposals yet. Listings with photos get 3x more interest — [add photos to get noticed]."
- No photos: "Guests scroll past listings without photos. [Add your first photo] — it takes 2 minutes."
- No amenities: "[Select your amenities] — guests filter by these. It takes about 1 minute."

**How it could fail:** Too many guidance messages at once (if everything is empty) could feel like a wall of nagging. Each individual message is helpful, but 6 of them stacked is overwhelming. Also, the "3x more interest" statistic must be real — fabricated social proof is manipulation.

### Approach B: Progressive Disclosure Empty States
Show a prioritized single empty-state message (the most impactful thing to fix), not all at once. After the host fixes the first one, reveal the next. This creates a guided flow rather than a wall of gaps.

**Examples:**
- First priority: "Photos are the #1 way to attract guests. [Add your first photo]"
- After photos added: "Nice! Now let's add amenities so guests can find you in search. [Select amenities]"

**How it could fail:** Hides the full picture from the host. A power host setting up a new listing may want to see all empty fields at once and batch-fill them. Progressive disclosure could feel patronizing or slow. Also, if the host navigates away and comes back, they need to re-enter the flow, which is confusing.

### Approach C: Empty State as Onboarding Integration
Merge the empty states with the onboarding progress section. Instead of showing empty states on individual fields, treat them all as onboarding steps. The onboarding checklist becomes the master to-do list, and individual sections just show "Will be completed in Step X."

**How it could fail:** This creates a dependency between the onboarding flow and the listing editor. If the host dismisses onboarding (HOD-2 improvement allows this), they lose the guidance entirely. Also, hosts who return to edit a listing later (not during onboarding) would see "Will be completed in Step X" which makes no sense outside the onboarding context.

### Selected: Approach A (Contextual Guidance Messages) with a cap from Approach B
**Rationale:** Approach A is the strongest because each empty state gets a tailored, helpful message. The "wall of nagging" risk is mitigated by borrowing from Approach B: if more than 3 fields are empty, show the top 3 with guidance and collapse the rest under "5 more items to complete — [see all]." Approach C's onboarding integration is architecturally fragile and fails when onboarding is dismissed.

See `copy/empty-states.md` for the full set of replacement copy strings.

---

## Gap 7: Referral Banner — Premature Display (HIGH)

### Approach A: Maturity Gate
Hide the referral banner from hosts who have not yet completed their first booking. Show it only after the host has had at least one successful guest stay. For active/power hosts, keep it visible but reframe the language.

**How it could fail:** The referral banner is a growth lever for the business. Hiding it from new hosts reduces referral funnel volume. Product/growth team may resist this change because it directly impacts a business metric.

### Approach B: Conditional Positioning
Keep the referral banner for all hosts but move its position based on maturity. New hosts: bottom of dashboard (below all listings), small and dismissible. Active hosts: mid-page, standard size. Power hosts: prominent with earnings tracker.

**How it could fail:** Bottom-of-page placement for new hosts means they'll never see it (few scroll that far), making it functionally invisible. The position-per-persona logic adds complexity. If persona detection is wrong, the banner appears in the wrong position, which is confusing.

### Approach C: Contextual Referral Trigger
Don't show the referral banner on the dashboard at all. Instead, trigger it at moments of delight: after a 5-star review, after hitting an earnings milestone, after a proposal is accepted. This catches the host at peak positive emotion when they're most likely to refer.

**How it could fail:** Contextual triggers are harder to implement (require event-based display logic). The host may never encounter the trigger if they don't check the platform at the right moment. Also, interrupting a celebratory moment with a referral ask could feel transactional — "We're celebrating your success so we can ask you for something."

### Selected: Approach A (Maturity Gate) with timing from Approach C
**Rationale:** The core principle is simple: don't ask a host to recruit for you before you've delivered value to them. Approach A's maturity gate is the most respectful and the simplest to implement (check: has_completed_booking). The business risk (reduced referral volume from new hosts) is mitigated by the insight from Approach C: trigger the referral ask after a moment of delight (first booking completed, first positive review) when conversion is actually higher. Approach B's conditional positioning is over-engineered.

**Combined implementation:** Hide banner until first completed booking. Then show it once with: "Your first guest had a great stay. Know someone with a great space? You'll both earn $50."

---

## Gap 8: Action Buttons — "Manage" Ambiguity (MEDIUM)

This gap is MEDIUM, but including alternatives for completeness.

### Approach A: Tooltip for New Hosts
On first dashboard visit, add a one-time tooltip to the "Manage" button: "Manage lets you edit your listing details, photos, pricing, and availability. Nothing saves until you confirm." Dismiss after first click.

**How it could fail:** Tooltips are easily missed or dismissed without reading. Mobile users may not see hover-triggered tooltips at all. The tooltip adds visual noise to an already dense card.

### Approach B: Rename to "Edit Listing"
Replace "Manage" with "Edit Listing" — clearer, more specific, universally understood.

**How it could fail:** "Edit Listing" implies modification, which might make cautious new hosts more nervous ("I don't want to edit, I just want to look"). Also, "Manage" may encompass more than editing (viewing stats, managing availability), and "Edit Listing" narrows the perceived scope.

### Approach C: Split into Specific Actions
Replace the single "Manage" button with two specific buttons: "Edit Details" and "View Stats." This removes ambiguity entirely.

**How it could fail:** Doubles the number of buttons per listing card (now 3-4 buttons), creating visual clutter. On mobile, this doesn't fit. Also, if the host wants to do something that doesn't fit either label, they're stuck.

### Selected: Approach B (Rename to "Edit Listing")
**Rationale:** The simplest fix with the broadest impact. "Edit Listing" is clearer than "Manage" and universally understood. The "nervous about editing" risk is minimal if we add a safety net: auto-save drafts and "Discard changes" option inside the editor. Approach A's tooltip is too easy to miss. Approach C creates clutter.
