# Task: Host Dashboard Emotional Journey + Copy System
Date: 2026-02-09
Token Budget: 1.5M

## Input
You are designing the **emotional experience and copy system** for the Split Lease Host Dashboard.

### Reference Material
- Existing mockup: `C:\Users\igor\OneDrive\Desktop\long-running processes\AI Team - SL22\runs\run-002--2026-01-30\html\improved-host-overview-dashboard--don-norman.html`
- Real listing content: `C:\Users\igor\OneDrive\Desktop\long-running processes\Site Current State\listing-dashboard-text.md`

### Context
Split Lease is a NYC rental platform. Hosts list rooms/apartments for nightly stays. Guests browse and submit proposals with their preferred dates and terms. The host dashboard is the host's command center — they check it 2-3x per week to see how their listings are doing and respond to proposals.

### Host Personas
- **New Host (first listing):** Anxious, uncertain if this will work, needs encouragement and clear next steps
- **Active Host (1-3 listings):** Building confidence, wants to see results, motivated by earnings growth
- **Power Host (4+ listings):** Efficient, wants data fast, annoyed by hand-holding, values density over warmth

### Dashboard Emotional Touchpoints
1. Welcome message (first thing host sees)
2. Earnings stats (financial validation)
3. Proposal notifications (urgency + opportunity)
4. Onboarding progress (effort anxiety vs. accomplishment)
5. Listing status badges (online = good, offline = anxiety)
6. Empty states (no proposals, no earnings, no photos)
7. Action buttons (commitment to respond/manage)
8. Referral banner ("Give $50 Get $50")

## Process
Execute the Evidence-Gap Probe + Adversarial Architect compound action:

1. **Map CURRENT emotional state** at each dashboard touchpoint:
   - Landing on dashboard: relief + checking anxiety ("any problems?")
   - Seeing earnings: validation (if good) or worry (if low)
   - Seeing proposals: excitement (someone wants my place!) + pressure (I need to respond)
   - Seeing onboarding: effort fatigue ("more steps?") or progress pride
   - Seeing offline listing: concern ("am I missing bookings?")

2. **Define TARGET emotional state** at each touchpoint:
   - Landing: confident control ("everything's running smoothly")
   - Earnings: motivated ("my listings are working")
   - Proposals: eager anticipation ("let me review this opportunity")
   - Onboarding: empowered progress ("I'm almost there, this is easy")
   - Offline listing: informed action ("I know why it's offline and what to do")

3. **Calculate emotional gaps** — rate each: low/medium/high/critical

4. **For each HIGH/CRITICAL gap, generate 3 intervention approaches:**
   Example for "proposal notification creates pressure instead of eagerness":
   - Approach A: Reframe as opportunity ("New guest interested in your space!")
   - Approach B: Reduce time pressure ("Respond within 48 hours — no rush")
   - Approach C: Add social proof ("Hosts who respond in 24h get 3x more bookings")
   - Failure analysis for each, then pick most robust

5. **Write specific copy for every dashboard state:**
   - Welcome: time-of-day aware greeting + earnings summary in one line
   - Stats: human-readable labels, not just numbers
   - Proposals: eager tone, not urgent tone
   - Onboarding: encouragement at each step, celebrate completions
   - Empty states: helpful, not hollow (no "nothing here yet" — instead guide to action)
   - Error states: calm, specific, recovery-focused
   - Offline listing: explain why, make going live feel easy

6. **Compile into copy system document** with tone guidelines per context

## Eval Target
All must pass:
- [ ] Every dashboard touchpoint has documented current AND target emotion
- [ ] All HIGH/CRITICAL gaps have interventions
- [ ] Each intervention has 3 approaches considered + failure analysis
- [ ] All copy is specific: exact strings, not "something encouraging"
- [ ] No manipulation: no false urgency ("Respond NOW!"), no artificial scarcity
- [ ] Empty states are helpful, not hollow
- [ ] Copy adapts to persona: new host (warm), active host (motivating), power host (efficient)
- [ ] Success, error, waiting, empty, confirmation tones all defined
- [ ] Vulnerable moments protected: first-time dashboard visit, zero earnings, listing rejection
- Max retries: 3

## Output
Save to: `assets/2026-02-09-host-dashboard/`
Expected files:
- `reports/emotion-map-host-dashboard.md` — Every touchpoint: current, target, gap, intervention
- `reports/intervention-specs.md` — Specific designs per gap (copy, timing, approach)
- `reports/alternatives-considered.md` — 3 approaches per gap + failure analysis
- `copy/copy-system-host-dashboard.md` — Full tone/voice guide with exact strings
- `copy/success-messages.md` — All success/confirmation copy for dashboard actions
- `copy/error-messages.md` — All error/recovery copy
- `copy/empty-states.md` — All zero-state copy (no listings, no proposals, no earnings, no photos)
- `copy/onboarding-copy.md` — Welcome, each step label, completion celebration, next-step hints
- `copy/personality-guide.md` — Tone per persona (new/active/power host), do/don't

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
