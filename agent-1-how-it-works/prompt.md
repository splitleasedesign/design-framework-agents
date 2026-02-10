# Task: Host Dashboard Flow Audit
Date: 2026-02-09
Token Budget: 1.5M

## Input
You are designing the **Host Overview Dashboard** for Split Lease, a NYC rental platform where hosts list rooms/apartments for nightly stays and guests propose lease terms.

### Reference Material
- Existing mockup: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\runs\run-002--2026-01-30\html\improved-host-overview-dashboard--don-norman.html`
- Real listing content: `C:\Users\igor\OneDrive\Desktop\long-running processes\Site Current State\listing-dashboard-text.md`
- Host dashboard screenshots: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\agents\orchestrator\assets\screenshots\host-journeys\03-host-dashboard\`

### Context
The host dashboard is the first thing a host sees after logging in. It must answer:
- How are my listings performing? (earnings, occupancy, proposals)
- What needs my attention right now? (pending proposals, incomplete steps)
- How do I manage my listings? (edit, go online/offline, view proposals)
- What should I do next? (onboarding steps, optimization tips)

The host has 1-5 listings on Split Lease. They check the dashboard 2-3x per week. They care most about: money earned, proposals waiting, and listing status.

## Process
Execute the Plan-Act-Verify compound action:

1. **Map the current flow** — What steps does a host take on the dashboard? What decisions do they make? What actions can they take?
2. **Identify the user goal** — Host wants to: see earnings, respond to proposals, manage listings
3. **Identify the business goal** — Split Lease wants to: keep hosts active, get proposals accepted fast, get listings completed
4. **Question every element** — Does the welcome message serve the goal? Does the onboarding section serve the goal? Does the stats layout serve the goal?
5. **Design the minimum viable dashboard** — What's the fewest elements needed for a host to accomplish their goals?
6. **Document error states** — What if there are no listings? No proposals? No earnings? Listing is incomplete?
7. **Document edge cases** — First-time host (0 listings), new host (1 incomplete listing), active host (3+ listings), power host (5+ listings, high volume)

## Eval Target
All must pass:
- [ ] User goal is explicitly stated
- [ ] Business goal is explicitly stated
- [ ] Every dashboard element is justified against a goal
- [ ] Empty/zero states documented (no listings, no earnings, no proposals)
- [ ] Edge cases: first-time host, new host, active host, power host
- [ ] Entry points: what brought the host here? Exit points: where do they go next?
- [ ] Error recovery: what if a listing fails to load? What if data is stale?
- [ ] Proposed flow eliminates any elements that don't serve user or business goal
- Max retries: 3

## Output
Save to: `assets/2026-02-09-host-dashboard/`
Expected files:
- `reports/flow-map-host-dashboard.md` — Every element, action, decision on the dashboard
- `reports/goal-analysis-host-dashboard.md` — User goal, business goal, persona analysis
- `reports/proposed-flow-host-dashboard.md` — The minimum viable dashboard design
- `reports/steps-eliminated.md` — What was cut from the current mockup and why
- `reports/error-recovery-matrix.md` — Every failure/empty state + recovery path

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
