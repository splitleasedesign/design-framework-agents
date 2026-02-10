# Onboarding Copy: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Scope: All onboarding flow copy — welcome, step labels, descriptions, completion celebrations, next-step hints, and re-engagement.

---

## Principles for Onboarding Copy

1. **Goal-focused, not task-focused.** Every step is framed as "getting closer to earning" not "completing a checklist."
2. **Time-honest.** Every step shows an estimated duration. We never hide the effort.
3. **Reason-first.** Before asking the host to do something, we say why it matters to their success.
4. **Celebrate completions.** Every finished step gets a brief, warm acknowledgment.
5. **No dead ends.** If the host pauses, we always have a gentle re-entry path.

---

## First-Time Welcome (First Dashboard Visit Ever)

**When:** Host logs in for the first time after creating their account.

**Welcome overlay (not a modal — an inline section at the top of the dashboard):**

Headline: "Welcome to Split Lease, {firstName}."
Body: "You're about to set up your first listing. Most hosts go from sign-up to live in about 30 minutes. Let's walk through it together."
CTA: "Start Setting Up" (primary button)
Secondary: "I'll explore on my own" (text link, dismisses welcome and shows the standard dashboard)

**If host clicks "I'll explore on my own":**
Welcome dismisses. Standard dashboard shows with onboarding progress section visible.

---

## Onboarding Section (Dashboard Widget)

### Header

**Title:** "You're Almost Ready to Welcome Guests"

**Progress text (adaptive):**
| Steps Done | Copy |
|-----------|------|
| 0 of 5 | "Let's get started — 5 quick steps to go live" |
| 1 of 5 | "1 of 5 steps done — great start, let's keep going" |
| 2 of 5 | "2 of 5 steps done — you're making great progress" |
| 3 of 5 | "3 of 5 steps done — you're more than halfway there" |
| 4 of 5 | "4 of 5 steps done — just one more to go" |
| 5 of 5 | (Completion state — see below) |

---

## Step Labels + Descriptions

### Step 1: Create Listing

**Label:** "Create Listing"
**Time estimate:** "~15 min"
**Description (shown when step is the current next action):**
"Start by describing your space — the type of room, how many bedrooms and bathrooms, and what makes it special. You can save a draft at any point and come back later."

**Why it matters (shown in the next-step hint area):**
"Start by describing your space. You can save a draft anytime and come back later."

**On completion:**
Checkmark animation (bounce-in, 300ms).
Step label: "Create Listing" with green checkmark.
Next-step hint updates to: "Done! Now let's add photos so guests can see your space."

---

### Step 2: Add Photos

**Label:** "Add Photos"
**Time estimate:** "~10 min"
**Description:**
"Upload photos of your space. Start with the main room, then add the bedroom, bathroom, kitchen, and any shared areas. Listings with 5+ photos get noticeably more interest."

**Why it matters:**
"Next up: Add Photos (~10 min). Listings with photos get 3x more proposals."

**On completion:**
Checkmark animation.
Next-step hint: "Photos look great. Next, let's set your pricing."

---

### Step 3: Set Pricing

**Label:** "Set Pricing"
**Time estimate:** "~3 min"
**Description:**
"Choose your nightly rate and any additional charges. We'll show you what similar spaces in your area are charging so you can price competitively."

**Why it matters:**
"Next up: Set Pricing (~3 min). We'll show you what similar spaces charge in your area."

**On completion:**
Checkmark animation.
Next-step hint: "Pricing is set. Now add a quick house manual so guests know what to expect."

---

### Step 4: House Manual

**Label:** "House Manual"
**Time estimate:** "~5 min"
**Description:**
"Write a short guide for your guests: how to check in, WiFi password, any house rules, and tips for enjoying the space. This shows up after a guest's booking is confirmed."

**Why it matters:**
"Next up: House Manual (~5 min). Guests love knowing what to expect — this step helps you get better proposals."

**On completion:**
Checkmark animation.
Next-step hint: "Almost there! One last step — go live and start receiving proposals."

---

### Step 5: Go Live

**Label:** "Go Live"
**Time estimate:** "~1 min"
**Description:**
"Review your listing one last time and publish it. Once live, guests in your area can find your space, submit proposals, and book their stay."

**Why it matters:**
"Last step: Go Live (~1 min). Flip the switch and guests in {neighborhood} can find your space."

**On completion:**
Full completion celebration (see below).

---

## Completion Celebration (All 5 Steps Done)

**Trigger:** Host returns to dashboard after completing Step 5, or completes Step 5 directly on the dashboard.

**Onboarding section transforms:**

Title: "You're all set! Your listing is live."
Body: "Guests in {neighborhood} can now find and book your space. We'll notify you when you get your first proposal."
CTA: "View Your Live Listing" (primary button)

**Animation sequence (1.5s total):**
1. All 5 step icons flash green simultaneously (200ms pulse).
2. Title crossfades from "You're Almost Ready to Welcome Guests" to "You're all set! Your listing is live." (300ms).
3. Steps section fades out (200ms).
4. Body text and CTA fade in (200ms).
5. After 10 seconds, onboarding section smoothly collapses (400ms height to 0).

**On next dashboard visit:** Onboarding section is permanently removed.

**Reinforcement:** For 7 days after completion, the welcome subtitle includes: "Your listing is live and visible to guests."

---

## Re-Engagement (Host Pauses Mid-Onboarding)

### Scenario: Host dismisses onboarding (clicks X)

**Immediate:** Onboarding section collapses.
**Welcome subtitle changes to:** "You're {n} steps from going live. [Resume setup]"
**"Resume setup"** re-expands the onboarding section with a smooth slide-down (300ms).

### Scenario: Host hasn't logged in for 3+ days with incomplete onboarding

**Email subject:** "Your listing is almost ready, {firstName}"
**Email body:**
"Hi {firstName},

You've completed {n} of 5 steps for your listing in {neighborhood}. You're close — the remaining steps take about {totalMinutes} minutes.

[Continue Setting Up]

If you have questions, reply to this email or chat with a Specialist Co-host.

— The Split Lease Team"

### Scenario: Host logs in after 7+ day absence with incomplete onboarding

**Dashboard welcome subtitle:** "Welcome back, {firstName}. You're {n} steps from going live — pick up where you left off."
**Onboarding section is expanded by default** (even if previously dismissed). The dismiss button is still available.

---

## Onboarding Step Detail Pages

When the host clicks on a step, they navigate to that section of the listing editor. Each section has an onboarding-context header:

**Header format:**
"Step {n} of 5: {stepName}"
Sub-text: "This usually takes about {timeEstimate}."
Progress bar: Thin bar showing overall onboarding progress (e.g., 60% for step 4).

**After saving the step:**
Inline confirmation: "Saved! {transitionMessage}"
"Saved! Let's move on to the next step." [Continue to {nextStepName}]

If this is the last step:
"Saved! You're ready to go live." [Publish Your Listing]

---

## Edge Cases

### Host creates multiple listings
Onboarding tracks per-listing. If a host creates a second listing before completing the first:
- Onboarding section shows the most recently created listing's progress.
- A toggle or dropdown allows switching between listings: "Showing setup for: {listingTitle} [Switch]"

### Host completes steps out of order
Steps are not strictly sequential. The host can complete them in any order. The onboarding section always highlights the next incomplete step (in the defined order: Create, Photos, Pricing, Manual, Go Live).

If a host skips to "Go Live" with missing steps:
"Before you can go live, you'll need to complete: {missing steps}."
This is shown inline on the Go Live page, not as a blocking error.

### Host with listing imported from another platform
Imported listings may have some steps pre-completed (description, photos). The onboarding section reflects this: "3 of 5 steps done — we imported your details from {platform}. Just {n} more to go."
