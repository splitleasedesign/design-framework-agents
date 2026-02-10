# Emotion Map: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Journey: Host Dashboard (overview page, all personas)
Method: Evidence-Gap Probe

---

## Touchpoint 1: Welcome Message (Hero Section)

### Current Emotional State
- **New Host:** Hopeful but uncertain. Scans the welcome line for proof the platform is working. Sees "Welcome back, Rod" and "Here's what's happening with your listings today" — generic, gives no signal of progress or safety. Emotion: **cautious hope mixed with low-grade anxiety** ("Is anything happening? Did I set this up right?")
- **Active Host:** Routine check-in. Slightly impatient — wants to skip the greeting and see numbers. Emotion: **neutral efficiency** ("Show me the numbers")
- **Power Host:** Ignores the welcome entirely. Emotion: **indifference verging on annoyance** if it takes up space without information density

### Target Emotional State
- **New Host:** **Grounded confidence** — "Everything is running, and here's proof"
- **Active Host:** **Motivated momentum** — "Things are growing, let me keep it going"
- **Power Host:** **Informed control** — "I see the status of my operation at a glance"

### Gap Rating: HIGH
The current welcome line is a dead sentence. "Here's what's happening with your listings today" promises information but delivers none — the actual information is below in the stat cards. This gap is most damaging for new hosts who need immediate reassurance.

### Intervention
Replace the static welcome subtitle with a dynamic one-line status summary that changes based on context:
- If proposals are pending: "You have 2 new proposals waiting — your listings are getting attention."
- If earnings are up: "Your earnings are up 12% this month. Nice work."
- If onboarding is incomplete: "You're 3 steps away from going live. Let's finish up."
- If everything is quiet: "All 3 listings are online and running smoothly."

See `intervention-specs.md` for exact copy strings and `alternatives-considered.md` for the 3 approaches evaluated.

---

## Touchpoint 2: Earnings Stats

### Current Emotional State
- **New Host (zero or low earnings):** **Deflation and doubt** — "$0" or a small number feels like failure. The stat card's large 40px font amplifies the number's emotional weight. Seeing "$0" in bold is a punch. Emotion: **discouragement + self-doubt** ("Maybe this won't work for me")
- **Active Host (moderate earnings):** **Cautious satisfaction** — The number feels validating but the "+12% vs last month" comparison can trigger **comparison anxiety** if the number is down. Emotion: **conditional pride** ("Good, but is it enough?")
- **Power Host (strong earnings):** **Confirmation of competence** — The number is fuel. But wanting to see per-listing breakdown quickly. Emotion: **satisfied efficiency** ("On track")

### Target Emotional State
- **New Host:** **Patient optimism** — "Earnings grow as my listing gets traction. Here's what to expect."
- **Active Host:** **Growth motivation** — "I'm building something real."
- **Power Host:** **Data confidence** — "I can see exactly where my money comes from."

### Gap Rating: CRITICAL (for new hosts with zero/low earnings)
A new host seeing "$0" in 40px bold font with no context is the single most damaging emotional moment on this dashboard. There is no framing, no expectation-setting, no encouragement. The current design treats zero earnings the same as $2,847 — just a different number. This is a critical gap because it can cause host churn at the most vulnerable moment.

### Intervention
For zero-earnings state: Replace "$0" with a contextual message. Never show a bare zero in large type. Instead: "Your first earning is on its way" with a subtle progress indicator showing listing views or proposal activity. For positive earnings: Add a human-readable sentence below the number: "That's 12% more than last month — your best February yet."

See `intervention-specs.md` for exact copy and `copy/empty-states.md` for zero-earnings copy.

---

## Touchpoint 3: Proposal Notifications

### Current Emotional State
- **New Host:** **Excitement spiked with performance pressure** — "Someone wants my place!" immediately followed by "I need to respond or I'll lose them." The action banner's exclamation mark icon (!) and "2 proposals need your attention" framing creates urgency. Emotion: **excited anxiety** ("Don't mess this up")
- **Active Host:** **Opportunity awareness with time pressure** — The word "need" in "need your attention" creates a mild obligation burden. Emotion: **dutiful engagement** ("I should deal with this now")
- **Power Host:** **Task-list processing** — Proposals are workflow items. The banner is fine but the tone is irrelevant. Emotion: **neutral task-mode** ("How many, let me clear them")

### Target Emotional State
- **New Host:** **Eager anticipation** — "A guest is interested! Let me learn about them."
- **Active Host:** **Confident opportunity assessment** — "New opportunity. Let me review the details."
- **Power Host:** **Efficient triage** — "2 to review. Let me process them."

### Gap Rating: HIGH
The current banner uses alarm language: exclamation mark icon, "need your attention," yellow warning-gradient background. This is the visual language of problems, not opportunities. A new proposal is good news — a guest chose your listing. The current design codes it as a task/problem.

### Intervention
Reframe the visual language from warning to opportunity. Replace the yellow warning banner with a purple/blue opportunity card. Change "2 proposals need your attention" to "2 guests are interested in your space." Replace the (!) alarm icon with a guest avatar or a subtle sparkle. Change the CTA from "Review Proposals" to "See Who's Interested."

See `intervention-specs.md` for exact specs and `alternatives-considered.md` for the 3 approaches.

---

## Touchpoint 4: Onboarding Progress

### Current Emotional State
- **New Host (mid-onboarding):** **Effort fatigue mixed with progress pride** — Seeing 3/5 steps completed is positive, but the remaining 2 steps ("House Manual" and "Go Live") feel like homework. The next-step hint ("Add a House Manual to help guests understand your space rules and amenities") is functional but reads like an assignment. Emotion: **dutiful slog** ("More things to do before I can earn money")
- **Active Host (completed):** Not visible (onboarding dismissed). No emotion.
- **Power Host (completed):** Not visible. No emotion.

### Target Emotional State
- **New Host:** **Empowered momentum** — "I'm 60% done and each step gets me closer to earning. The next step is quick."

### Gap Rating: HIGH
The onboarding section is the biggest source of effort anxiety for new hosts. The current "Complete Your Host Profile" title frames it as work to do, not progress made. The steps show what's remaining rather than celebrating what's done. The next-step hint is practical but emotionally flat — it explains what to do but not why it matters or how long it takes.

### Intervention
Reframe from task-completion to progress-celebration. Change title from "Complete Your Host Profile" to "You're Almost Ready to Earn." Add time estimates to remaining steps ("House Manual — about 5 minutes"). Change the next-step hint to include a motivational bridge: "Next up: House Manual (about 5 min). Guests love knowing what to expect — this step helps you get better proposals."

See `intervention-specs.md` for animation specs and `alternatives-considered.md`.

---

## Touchpoint 5: Listing Status Badges (Online/Offline)

### Current Emotional State
- **New Host (listing offline):** **Alarm and confusion** — "Offline" in grey with a pause icon feels like something is wrong. The host may not understand why it's offline (incomplete setup? they turned it off? the platform deactivated it?). Emotion: **worried confusion** ("Is my listing broken? Am I losing money?")
- **Active Host (listing offline):** **Concerned urgency** — Knows what offline means but still feels the cost of lost bookings. Emotion: **motivated concern** ("I need to fix this")
- **Power Host (listing offline):** **Operational awareness** — Sees it as a status to manage. Emotion: **neutral alertness** ("Which one, and why?")

### Target Emotional State
- **New Host:** **Informed calm** — "My listing is offline because X. Here's how to make it live."
- **Active Host:** **Clear next action** — "I know what to do to get this back online."
- **Power Host:** **Quick diagnosis** — "Offline because X. One-click to fix."

### Gap Rating: HIGH
The current "Offline" badge provides no explanation. The host sees a grey badge that says "Offline" with a pause icon, but gets zero information about why. For new hosts, this is especially damaging because they may not know if they caused it, if the platform caused it, or if it's a problem at all. The gap between "worried confusion" and "informed calm" is large.

### Intervention
Add a reason to the offline state. Below the badge or on hover: "Offline — missing house manual" or "Offline — paused by you." Add a single-action link: "Add house manual to go live" or "Resume listing." This turns confusion into a clear, low-effort next step.

See `intervention-specs.md` for exact implementation.

---

## Touchpoint 6: Empty States

### Current Emotional State
- **No proposals on a listing:** Seeing "0 Proposals" in large font on a listing card creates **inadequacy** ("Nobody wants my place"). The "Proposals" button without a badge number feels like a dead end.
- **No earnings (new host):** "$0" in 40px bold — **discouragement** (covered in Touchpoint 2).
- **No photos uploaded:** "No photos uploaded yet." in the listing dashboard — **guilt and overwhelm** ("I know I should do this but it feels like a lot of work"). The current text offers no guidance, no encouragement, no reason why this matters.
- **No amenities selected:** "No amenities selected" — **apathy or confusion** ("I don't know which ones to pick")
- **No rules selected:** "No rules selected" — **uncertainty** ("Is this bad? Will I get bad guests?")
- **No neighborhood description:** "No neighborhood description provided." — **guilt** ("I should write something but I don't know what")

### Target Emotional State
- **No proposals:** **Patient confidence** — "Proposals take time. Here's what's happening with your listing views."
- **No earnings:** **Grounded expectation** — "Earnings come after your first booking. You're on track."
- **No photos:** **Motivated action** — "Photos are the #1 thing guests look at. Let me add some now."
- **No amenities:** **Easy action** — "Selecting amenities takes 2 minutes and helps guests find you."
- **No rules:** **Protective confidence** — "Setting rules protects you and sets clear expectations."
- **No neighborhood description:** **Creative encouragement** — "Tell guests what makes your area special."

### Gap Rating: CRITICAL
Every empty state in the current design is either a bare zero ("0 Proposals," "$0") or a negative declaration ("No amenities selected," "No photos uploaded yet"). These are the most emotionally corrosive patterns in the dashboard. They turn every incomplete field into a failure. New hosts encounter many of these at once, creating a cascade of inadequacy. None of the current empty states offer guidance, context, or encouragement.

### Intervention
Replace every bare-zero and "No X" message with a contextual, helpful, action-oriented message. See `copy/empty-states.md` for the complete set of replacement strings.

---

## Touchpoint 7: Action Buttons (Manage, Proposals, Create New Listing)

### Current Emotional State
- **New Host:** **Uncertain hesitation** — "Manage" is vague. What will happen when I click? Will I break something? Emotion: **cautious clicking** ("I hope I don't mess up my listing")
- **Active Host:** **Functional navigation** — Knows what Manage does. Emotion: **neutral efficiency**
- **Power Host:** **Rapid scanning** — Wants the most important action surfaced first. "Manage" is too generic for quick triage. Emotion: **mild frustration** ("Just show me what needs attention")

### Target Emotional State
- **New Host:** **Safe exploration** — "I can look around without breaking anything."
- **Active Host:** **Clear pathways** — "I know exactly where each button takes me."
- **Power Host:** **Priority-first actions** — "The most urgent action is always visible."

### Gap Rating: MEDIUM
The "Manage" button is vague but not harmful. The loading state on "Review Proposals" (HOD-5 improvement) helps with feedback. The main gap is for new hosts who don't know what "Manage" contains and may hesitate to click.

### Intervention
For new hosts (first 30 days), add a tooltip on first visit: "Manage lets you edit your listing details, photos, and pricing. Nothing saves until you confirm." For power hosts, add a priority indicator to the proposals button when proposals are time-sensitive: "2 Proposals (oldest: 2 days ago)."

---

## Touchpoint 8: Referral Banner ("Give $50 Get $50")

### Current Emotional State
- **New Host:** **Premature sales pitch** — They haven't earned anything yet, and the platform is already asking them to recruit. Emotion: **mild annoyance + distrust** ("They care more about growth than helping me succeed")
- **Active Host:** **Moderate interest** — Has had good experiences, might consider sharing. Emotion: **open but passive** ("Maybe later")
- **Power Host:** **Potential motivator** — $50 is small but the concept is valid. Emotion: **calculating interest** ("How much effort is this?")

### Target Emotional State
- **New Host:** Should not see this banner until after first successful booking. Target: **Not shown.**
- **Active Host:** **Rewarded loyalty** — "I'm part of a community and I benefit from bringing others in."
- **Power Host:** **Strategic opportunity** — "This scales my network and my earnings."

### Gap Rating: HIGH
Showing a referral banner to a host who has zero earnings and incomplete onboarding is emotionally tone-deaf. It signals that the platform prioritizes growth over the host's success. This should be gated by host maturity: show only after first completed booking or after earnings exceed a threshold.

### Intervention
Gate the referral banner: hide for new hosts until after first completed booking. For active hosts, reframe from transactional ("Give $50 Get $50") to community ("Know someone with a great space? You'll both earn $50 when they host their first guest."). For power hosts, add a referral dashboard link showing their referral earnings.

See `alternatives-considered.md` for the 3 approaches evaluated.

---

## Gap Summary

| # | Touchpoint | Gap Rating | Primary Persona Affected |
|---|-----------|------------|--------------------------|
| 1 | Welcome Message | HIGH | New Host |
| 2 | Earnings Stats (zero state) | CRITICAL | New Host |
| 3 | Proposal Notifications | HIGH | New Host, Active Host |
| 4 | Onboarding Progress | HIGH | New Host |
| 5 | Listing Status Badges | HIGH | New Host |
| 6 | Empty States (all) | CRITICAL | New Host |
| 7 | Action Buttons | MEDIUM | New Host, Power Host |
| 8 | Referral Banner | HIGH | New Host |

**Total gaps requiring Adversarial Architect treatment (HIGH + CRITICAL): 7**
**MEDIUM gaps with targeted fix: 1**
