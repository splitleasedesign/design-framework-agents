# Information Clarity Model for Agent 2

Purpose: This document is the quality model for Agent 2 (How we Communicate Information). Use it to make screens scannable, understandable, and action-oriented across all breakpoints.

---

## Part 1: Clarity Stack

### Level 1: Findability
- Primary information is visible without hunting.
- Critical actions are identifiable at a glance.
- Navigation and orientation are obvious.

Failure signal: Users ask "Where do I start?"

### Level 2: Hierarchy
- Information priority is visually explicit.
- Primary, secondary, and tertiary data are distinguishable.
- Competing elements are reduced.

Failure signal: Multiple elements look equally important.

### Level 3: Density Control
- Dense screens are chunked and grouped.
- Secondary data uses progressive disclosure.
- Layout supports fast scanning, not only deep reading.

Failure signal: Users miss key data even when it is present.

### Level 4: Responsive Integrity
- Meaning and hierarchy survive at 320px, 768px, and desktop.
- Components reflow without clipping or overlap.
- Interaction targets remain usable on touch.

Failure signal: Mobile layout changes what the screen means.

---

## Part 2: Information Inventory Method

For every screen, inventory all content into:

- P0: Must see to decide
- P1: Useful context
- P2: Optional details

Rules:
- P0 stays visible by default.
- P1 can collapse based on viewport.
- P2 is disclosed on demand.

---

## Part 3: Pattern Selection Matrix

- List: sequential, comparable records with quick actions.
- Cards: mixed media + metadata with moderate density.
- Grid: visual browse and high volume scanning.
- Table: precise comparison across shared fields.
- Accordion: detail-heavy content with low simultaneous visibility needs.

Choose pattern by task, not preference.

---

## Part 4: Core Patterns

### 1) Three-Tier Hierarchy
One primary message, one supporting layer, one metadata layer.

### 2) Scan Landmarks
Use repeated anchors (price, status, action row) in consistent positions.

### 3) Progressive Disclosure
Hide complexity until user intent is clear.

### 4) Chunked Sections
Group related data with spacing and headings before borders.

### 5) Mobile-First Reflow
Stack by priority, not by desktop source order.

---

## Part 5: Anti-Patterns

- Decorative blocks that do not increase comprehension
- Hiding P0 information behind clicks
- Inconsistent component ordering between cards
- Overloaded cards with no clear first read
- Desktop-perfect layouts that collapse poorly on mobile

---

## Part 6: Clarity Scorecard (0-20)

Score each item 0 (fail), 1 (partial), 2 (pass):

1. Information inventory is complete
2. Priority mapping (P0/P1/P2) is explicit
3. Hierarchy is visually obvious
4. Pattern choice matches content type
5. Primary action is unambiguous
6. Scan landmarks are consistent
7. Cognitive load is controlled
8. Mobile reflow preserves meaning
9. Touch targets remain usable
10. User can find P0 info in under 3 seconds

Target: 16+ for release, 18+ for benchmark quality.
