# Empty State Copy: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Scope: Every zero-state / empty-state across the dashboard and listing editor.

---

## Principles for Empty States

1. **Never show a bare zero or a negative declaration.** "$0" in bold and "No amenities selected" are emotionally corrosive.
2. **Every empty state must answer three questions:** What is this? Why does it matter? What do I do?
3. **Forward-looking, not backward-pointing.** "No photos uploaded yet" looks backward. "Add your first photo" looks forward.
4. **Include a direct action.** Every empty state has a clickable CTA that takes the host to the fix.
5. **Brief.** Empty states are not tutorials. 2-3 sentences maximum.

---

## Dashboard-Level Empty States

### No Listings (Brand New Host)

**Location:** Main content area, replacing the listings grid.

**Icon:** Illustration of a simple house outline with a plus sign (32x32, var(--color-primary-light))

**Headline:** "Create your first listing"

**Body:** "Describe your space, add photos, and set your price. Most hosts have their first listing live within 30 minutes."

**CTA:** "+ Create Your First Listing" (primary button)

**Secondary link:** "Import from another platform" (text link below CTA)

---

### No Proposals (Listing Live, Zero Proposals Ever)

**Location:** Proposals stat card (replacing the "0" value) and proposal action banner (hidden).

**Stat card display:**
Value area: "No proposals yet" (22px semi-bold, not 40px — reduce visual weight of emptiness)
Sub-text: "When guests are interested, you'll see their proposals here."

**No proposal banner is shown.** The yellow/purple action banner does not appear when there are zero proposals. Showing an empty action banner feels like a broken page.

---

### No Proposals (Listing Live, Previously Had Proposals, Currently Zero Pending)

**Location:** Proposals stat card.

**Stat card display:**
Value area: "All caught up" (22px semi-bold)
Sub-text: "You've responded to all proposals. Nice work."

This is not technically an empty state — it's a zero-active state. The tone is celebratory, not vacant.

---

### No Earnings (New Host, Listing Live)

**Location:** Earnings stat card (replacing "$0").

**Stat card display:**
Value area: "Your first earning is on its way" (22px semi-bold)

**Sub-text (conditional):**
- Has listing views: "Your listing has been viewed {X} times this week. Guests are noticing."
- No listing views yet: "You listed on {date}. Most hosts see their first proposals within 2 weeks."
- Listing not yet live: "Earnings start when your listing is live. Complete setup to get started."

**"See all stats" link:** Remains visible. Leads to stats page showing views and search impressions.

---

### No Earnings (New Host, Listing Not Yet Live)

**Location:** Earnings stat card.

**Stat card display:**
Value area: "Earnings start when your listing is live" (22px semi-bold)
Sub-text: "Complete your listing setup to start receiving guests and earning."
Link: "Resume setup" (links to onboarding or first incomplete step)

---

### No Earnings (Returning Host, Previously Had Earnings, Current Month = $0)

**Location:** Earnings stat card.

**Stat card display:**
Value area: "$0 so far this month" (40px bold is fine here — the host understands context)
Sub-text: "Last month you earned ${lastMonthAmount}. Bookings typically pick up as the month goes on."

**Note:** For returning hosts, showing $0 is acceptable because they have context. The sub-text normalizes it.

---

## Listing Editor Empty States

### No Photos

**Location:** Photos section of the listing editor.

**Current copy (to replace):** "No photos uploaded yet."

**New copy:**
**Icon:** Camera outline icon (32x32, var(--color-primary-light))
**Headline:** "Add photos to attract guests"
**Body:** "Listings with photos get noticed first. Start with a photo of the main room — it takes less than a minute."
**CTA:** "Add Your First Photo" (primary button)
**Secondary:** "Tips for great listing photos" (text link, opens a help article or tooltip with quick tips)

**Quick tips (if linked):**
- "Use natural light — open the curtains and shoot during the day."
- "Show the whole room from the doorway, not just a corner."
- "Include the bed, desk, and window if visible."
- "Clean the space and make the bed before photographing."

---

### No Amenities Selected

**Location:** Amenities section of the listing editor.

**Current copy (to replace):** "No amenities selected"

**New copy:**
**Icon:** Checkmark list icon (32x32, var(--color-primary-light))
**Headline:** "Select your amenities"
**Body:** "Guests filter by amenities like WiFi, laundry, and air conditioning. Selecting yours takes about 1 minute and helps your listing show up in more searches."
**CTA:** "Select Amenities" (primary button)

---

### No Neighborhood Description

**Location:** Neighborhood section of the listing editor.

**Current copy (to replace):** "No neighborhood description provided."

**New copy:**
**Icon:** Map pin icon (32x32, var(--color-primary-light))
**Headline:** "Tell guests about your neighborhood"
**Body:** "What's nearby? Mention the subway, grocery stores, parks, or restaurants you like. Guests love knowing what's around the corner."
**CTA:** "Write a Neighborhood Description" (primary button)

**Prompt starters (shown in the text area as placeholder):**
"My neighborhood is great because..."

---

### No Rules Selected

**Location:** Rules section of the listing editor.

**Current copy (to replace):** "No rules selected"

**New copy:**
**Icon:** Shield icon (32x32, var(--color-primary-light))
**Headline:** "Set your house rules"
**Body:** "Clear rules help you attract guests who are a good fit for your space. Common rules include quiet hours, no smoking, and shoe-free areas."
**CTA:** "Set Your Rules" (primary button)

---

### No Safety Features Selected

**Location:** Safety features section of the listing editor.

**Current copy (to replace):** "No safety features selected"

**New copy:**
**Icon:** Fire extinguisher icon (32x32, var(--color-primary-light))
**Headline:** "Add your safety features"
**Body:** "Guests want to know about smoke detectors, fire extinguishers, and first-aid kits. Listing these builds trust and may be required by local regulations."
**CTA:** "Select Safety Features" (primary button)

---

### No Description of Lodging (Beyond Default)

**Location:** Description section of the listing editor.

**Current copy (to replace):** "1 bedroom private room available for nightly rental." (auto-generated default)

The auto-generated description is functional but impersonal. We don't show an empty state here because there IS a default description. Instead, we add an enhancement prompt:

**Enhancement prompt (below the description):**
"This is an auto-generated description. Adding personal details — like natural light, a quiet street, or a great view — helps your listing stand out."
**CTA:** "Edit Description" (text link)

---

### No Storage

**Location:** Details section.

**Current copy:** "No storage"

**New copy:** "No storage mentioned"
Note: This is a factual field, not an empty state. If the host genuinely has no storage, "No storage" is correct. But if they simply haven't filled it in, we should distinguish. Since we can't tell, we soften to "No storage mentioned" with a small "Edit" link.

---

### No Parking

**Location:** Details section.

**Current copy:** "No Parking"

**New copy:** "No parking mentioned"
Same logic as storage. Soften to "mentioned" with an edit link.

---

### Zero Square Footage

**Location:** Details section.

**Current copy:** "0 sq.ft."

**New copy:** "Square footage not set"
**CTA:** "Add square footage" (text link to edit details)
A "0 sq.ft." display is clearly a missing-data bug, not a real measurement. Never show zero as if it's a fact.

---

### No Dates Blocked

**Location:** Calendar/availability section.

**Current copy:** "You don't have any future date blocked yet"

**New copy:** "No blocked dates"
**Body:** "All your available dates are open for proposals. Block any dates you're unavailable by tapping them on the calendar."

This is not a problem state — having no blocked dates is perfectly normal. The copy should confirm the status, not imply something is missing.

---

### No Import Reviews

**Location:** Reviews import section.

**Current copy:** "Import reviews from other sites"

This is a CTA, not an empty state. The copy is fine as-is. It's actionable and clear.

---

## Empty State Visual Template

All empty states follow a consistent layout:

```
+------------------------------------------+
|  [Icon]                                  |
|                                          |
|  Headline (16px, semi-bold, #1A1A1A)     |
|  Body text (14px, regular, #666666)      |
|                                          |
|  [CTA Button or Link]                    |
+------------------------------------------+
```

- Container: No border, no background. Centered within the parent section.
- Padding: 24px vertical, 16px horizontal.
- Max width: 400px (centered).
- Icon: 32x32, centered above headline.
- Spacing: 12px between icon and headline, 8px between headline and body, 16px between body and CTA.

---

## Cascade Rule: Maximum 3 Visible Empty States

If a listing or dashboard has more than 3 empty-state messages visible at once (common for brand-new listings), show the top 3 by priority and collapse the rest:

**Priority order:**
1. No photos (highest impact on guest interest)
2. No pricing (blocks going live)
3. No description (high impact)
4. No amenities
5. No neighborhood description
6. No rules
7. No safety features

**Collapsed message:**
"{n} more items to complete. [See all]"
Clicking "See all" expands all empty states.

This prevents the "wall of nagging" effect where every section screams for attention simultaneously.
