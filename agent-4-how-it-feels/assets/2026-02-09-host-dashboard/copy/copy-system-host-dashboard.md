# Copy System: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Scope: All copy strings for the Split Lease Host Dashboard (overview page)

---

## Voice Principles

1. **Grounded, not giddy.** We celebrate wins without being over-the-top. Hosting is real work — we respect that.
2. **Clear, not clever.** Every word must be immediately understandable. No jargon, no puns, no double meanings.
3. **Warm, not syrupy.** We sound like a knowledgeable friend, not a greeting card.
4. **Actionable, not vague.** When something needs doing, we say exactly what and how long it takes.
5. **Honest, not optimistic-at-all-costs.** If earnings are down, we don't pretend they're up. We provide context.

---

## Tone Scale

| Context | Tone Level | Example |
|---------|-----------|---------|
| Celebration (first earning, booking confirmed) | Warm + proud | "You just earned your first payout. This is just the beginning." |
| Normal operations (stats, listing status) | Calm + informative | "Your listings earned $2,847 this month — up 12% from January." |
| Guidance (onboarding, empty states) | Encouraging + specific | "Next up: House Manual (about 5 min). Guests love knowing what to expect." |
| Proposals (guest interest) | Positive + unhurried | "2 guests are interested in your space. Take a look when you're ready." |
| Errors (save failed, connection lost) | Calm + recovery-focused | "Your changes didn't save. Check your connection and try again." |
| Waiting (loading, processing) | Patient + informative | "Loading your listings..." or "Saving your changes..." |
| Empty states (no data yet) | Helpful + forward-looking | "No proposals yet. Listings with complete profiles get noticed faster." |
| Offline listing | Factual + action-oriented | "Offline — add a house manual to go live." |

---

## Dashboard Copy: Every Element

### 1. Page Title (Browser Tab)
"Host Overview | Split Lease"

### 2. Header Navigation
- "Host Overview" (current page, active state)
- "Messages"
- Avatar with first initial

### 3. Welcome Section

**Greeting headline:**
- Morning (5am-12pm): "Good morning, {firstName}"
- Afternoon (12pm-5pm): "Good afternoon, {firstName}"
- Evening (5pm-9pm): "Good evening, {firstName}"
- Night (9pm-5am): "Welcome back, {firstName}"

**Dynamic subtitle (priority order — show first match):**

| Priority | Condition | Copy |
|----------|-----------|------|
| 1 | Proposals > 24h old | "You have {n} proposals waiting — the oldest is from {X} days ago." |
| 2 | New proposals < 24h old | "{n} guests are interested in your space. Take a look when you're ready." |
| 3 | Onboarding incomplete | "You're {n} steps away from going live. Let's get you there." |
| 4 | Earnings > 0, proposals = 0 | "Your listings earned ${amount} this month — up {X}% from {lastMonth}." |
| 5 | Earnings = 0, listing live | "Your listing is live and visible to guests in {neighborhood}." |
| 6 | Earnings = 0, listing not live | "Let's finish setting up so guests can find your space." |
| 7 | Default (everything normal) | "All {n} listings are online and running smoothly." |

If earnings are down vs last month, replace "up X%" with context:
"Your listings earned ${amount} this month. February is typically slower — bookings pick up in March."

### 4. Action Buttons (Top Right)

**Primary CTA:**
"+ Create New Listing"
- Tooltip (new host, first 30 days): "List another room or apartment. You can save a draft and come back anytime."

**Secondary CTA:**
"Import Listing"
- Tooltip (all hosts): "Already listed on another platform? Import your details in one step."

### 5. Stat Cards

**Earnings Card**

Label: "This Month's Earnings"
Link: "See all stats"

Value states:
| State | Display |
|-------|---------|
| Has earnings, up vs last month | "${amount}" (40px bold) + "Up {X}% from {lastMonth} -- {Y}% occupancy" |
| Has earnings, down vs last month | "${amount}" (40px bold) + "Down {X}% from {lastMonth}. February is typically slower." |
| Has earnings, flat vs last month | "${amount}" (40px bold) + "Steady from {lastMonth} -- {Y}% occupancy" |
| Zero earnings, listing live | "Your first earning is on its way" (22px semi-bold) + "Your listing has been viewed {X} times this week. Guests are noticing." |
| Zero earnings, listing live, zero views | "Your first earning is on its way" (22px semi-bold) + "You listed on {date}. Most hosts see their first proposals within 2 weeks." |
| Zero earnings, listing not live | "Earnings start when your listing is live" (22px semi-bold) + "Complete setup to start receiving guests." |

**Proposals Card**

Label: "Proposals Needing Action"

Value states:
| State | Display |
|-------|---------|
| Has proposals needing action | "{n}" (40px bold) + "{total} total pending -- {rating} avg rating" |
| Zero proposals needing action, has responded | "All caught up" (22px semi-bold) + "You've responded to all proposals. Nice work." |
| Zero proposals ever | "No proposals yet" (22px semi-bold) + "When guests are interested, you'll see their proposals here." |

### 6. Proposal Action Banner

**With pending proposals:**
- Headline: "{n} guests are interested in your space"
- Detail: "{guestFirstName} submitted a proposal for {listingName}. Take a look when you're ready."
- Detail (deadline near): "{guestFirstName} submitted a proposal for {listingName}. Respond by {date} so they can finalize their plans."
- CTA: "See Who's Interested"

**After all proposals handled (banner hidden):**
No banner shown. Proposals card shows "All caught up."

### 7. Onboarding Section

**Title:** "You're Almost Ready to Welcome Guests"
**Progress:** "{n} of 5 steps done — you're more than halfway there"
(For 1/5: "1 of 5 steps done — great start, let's keep going")
(For 4/5: "4 of 5 steps done — just one more to go")

**Step labels with status:**
| Step | Completed | Pending |
|------|-----------|---------|
| Create Listing | "Create Listing" + checkmark | "Create Listing" |
| Add Photos | "Add Photos" + checkmark | "Add Photos (~10 min)" |
| Set Pricing | "Set Pricing" + checkmark | "Set Pricing (~3 min)" |
| House Manual | "House Manual" + checkmark | "House Manual (~5 min)" |
| Go Live | "Go Live" + checkmark | "Go Live (~1 min)" |

**Next-step hints (per step):**
| Next Step | Hint Copy |
|-----------|-----------|
| Create Listing | "Start by describing your space. You can save a draft anytime." |
| Add Photos | "Next up: Add Photos (~10 min). Listings with photos get 3x more proposals." |
| Set Pricing | "Next up: Set Pricing (~3 min). We'll show you what similar spaces charge in your area." |
| House Manual | "Next up: House Manual (~5 min). Guests love knowing what to expect — this step helps you get better proposals." |
| Go Live | "Last step: Go Live (~1 min). Flip the switch and guests in {neighborhood} can find your space." |

**Dismiss confirmation:**
When host clicks dismiss (X): Section collapses immediately, no confirmation dialog.
Recovery: Welcome subtitle changes to "You're {n} steps from going live. [Resume setup]"

**Completion state:**
Title: "You're all set! Your listing is live."
Body: "Guests in {neighborhood} can now find and book your space. We'll notify you when you get your first proposal."
CTA: "View Your Live Listing"

### 8. Listings Section

**Section header:**
Title: "Your Listings"
Count: "{n} listings" (or "1 listing" for singular)

**Listing card elements:**

Title: "{listingTitle}" (e.g., "Sunny Private Room Near Central Park")
Location: "{neighborhood}, NY"

**Status badge:**
- Online: green badge, checkmark icon, "Online"
- Offline with reason: grey badge, pause icon, "Offline"
  + Reason line below title (see INT-5 for full copy set)

**Mini stats per listing:**
- "${amount}" / "This Month"
- "{X}%" / "Occupancy"
- "{n}" / "Proposals"

**Action buttons:**
- Primary: "Edit Listing" (formerly "Manage")
- Secondary: "Proposals" with badge count, or "Proposals" without badge when count is 0

**Listing card — zero earnings on individual listing:**
Instead of "$0" in mini stat, show: "--" with label "This Month"
(The full zero-earnings context is handled in the top stat card. Per-listing, a simple dash is less harmful than a bold zero.)

### 9. Referral Banner

**Pre-first-booking:** Not shown.

**Post-first-booking (first display):**
Headline: "Your first guest had a great experience."
Body: "Know someone with a great space? Invite them to host on Split Lease. You'll both earn $50 when they welcome their first guest."
CTA: "Invite a Friend to Host"

**Standard (returning active/power host):**
Headline: "Grow the community, earn $50"
Body: "For every friend who hosts their first guest, you both get $50. No limit."
CTA: "Share Your Invite Link"

### 10. Specialist Co-host Banner

"Need help setting up? Talk to a Specialist Co-host."
Body: "Our specialists can help you optimize your listing and attract more guests."
CTA: "Get Expert Help"

This banner appears only for hosts with incomplete onboarding (new hosts).
For active/power hosts, it is hidden.

---

## Formatting Rules

- **Numbers:** Use commas for thousands ($2,847 not $2847). Use % symbol after number (85% not 85 percent).
- **Names:** Use first name only for guest references in proposals ("Leo submitted..." not "Leo Di Caprio submitted...").
- **Dates:** Use friendly format: "Feb 12" not "02/12/2026". For relative dates: "2 days ago" not "February 8, 2026."
- **Time estimates:** Round to nearest 5 minutes. Say "about 5 minutes" or "~5 min" not "approximately 4-6 minutes."
- **Contractions:** Use them naturally. "You're" not "You are." "Let's" not "Let us." "We'll" not "We will."
- **Capitalization:** Sentence case for all copy. Title Case for proper nouns only. Never ALL CAPS except status badges (ONLINE/OFFLINE).
- **Exclamation marks:** Maximum one per page. Use only for genuine celebrations (first earning, onboarding complete). Never for urgency or calls to action.
