# Task: Host Success Stories — Information Architecture & Layout
Date: 2026-02-10
Priority: Pipeline Step 2 of 4
Run ID: run-20260210-130900

## Objective
Take Agent 1's bare functional HTML and restructure it for optimal information communication. Improve hierarchy, cognitive load, layout patterns, and scannability. The visitor should instantly understand: "real hosts, real success, I should list my space too."

## Input
- **Agent 1's output:** `run-20260210-130900/step-1-works/host-success-stories.html`
- Read this file first — it contains the bare functional page with all content

## Context
- Marketing/social-proof page for Split Lease (NYC rental platform)
- **Visitor profile:** Prospective host, possibly skeptical, landed from Google or referral
- **Page goal:** Read stories → build trust → click "List Your Property"
- Currently 1 testimonial (Emily Johnson), but the layout must support N testimonials
- This is a conversion page — the CTA is the most important action

## Process
1. **Read Agent 1's HTML** — understand the raw content and structure
2. **Information inventory** — catalog every piece of information on the page:
   - Page title / hero headline
   - Host testimonial: photo, name, profession, pull quote, full story
   - CTA: headline + button
   - Navigation
3. **Priority ranking:**
   - P0: Hero headline + first testimonial pull quote (hook the visitor)
   - P0: CTA section (the conversion goal)
   - P1: Full testimonial story (social proof depth)
   - P1: Host identity (name, profession, photo — trust signals)
   - P2: Navigation
4. **Layout decisions:**
   - Hero section: page title + value proposition
   - Testimonial card pattern: photo + quote + expandable/visible story
   - Consider: card layout that scales from 1 to many testimonials
   - CTA section: sticky or prominent, hard to miss
   - Pull quote should be visually distinct from the story body
5. **Apply wireframe CSS:**
   - Two-column or card-based layout for testimonials
   - Visual hierarchy through size, weight, spacing (no colors yet)
   - Responsive: stack on mobile, grid on desktop
   - Clear separation between testimonial and CTA
6. **Do NOT add:** colors, shadows, icons, fonts, decorative elements — that's Agent 3

## Eval Target
All must pass:
- [ ] Hero section communicates page purpose in under 3 seconds
- [ ] Pull quote is the most prominent text in the testimonial (not buried in body)
- [ ] Host identity (name, profession, photo) is clearly associated with their story
- [ ] Full story is readable but doesn't overwhelm — progressive disclosure if long
- [ ] CTA section is visually prominent and clearly the next step
- [ ] Layout works for 1 testimonial and would work for 3-6 testimonials
- [ ] Information hierarchy is clear: headline > quote > identity > story > CTA
- [ ] Page is scannable — a visitor skimming gets the key message
- [ ] Responsive: readable on mobile (single column) and desktop (multi-column possible)
- [ ] Cognitive load is low — no competing calls to action, no visual noise
- Max retries: 3

## Output
Save to: `run-20260210-130900/step-2-communicates/host-success-stories.html`

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
