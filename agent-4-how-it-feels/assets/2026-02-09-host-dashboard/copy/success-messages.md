# Success & Confirmation Messages: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Scope: Every success/confirmation state a host encounters on or triggered from the dashboard.

---

## Principles for Success Copy

1. **Confirm what happened.** The host should never wonder "did it work?"
2. **Celebrate proportionally.** First-time achievements get more warmth. Routine actions get a brief confirmation.
3. **Point forward.** After confirming, suggest what to do next — but gently, not pushily.
4. **No forced interstitials.** Success messages appear inline or as brief toast notifications. No modal pop-ups that require dismissal.

---

## Listing Published / Goes Live

**First listing ever published:**
Toast notification (5s auto-dismiss):
"Your listing is live! Guests in {neighborhood} can now find and book your space."
Subtitle: "We'll notify you by email and on your dashboard when someone submits a proposal."

**Subsequent listing published:**
Toast notification (4s auto-dismiss):
"Listing published. {listingTitle} is now live."

**Listing re-published after being offline:**
Toast notification (4s auto-dismiss):
"Back online. {listingTitle} is visible to guests again."

---

## Proposal Accepted

**First proposal ever accepted:**
Inline confirmation on proposals page, with copy reflected on next dashboard visit:
"You accepted {guestFirstName}'s proposal! They'll receive confirmation and booking details shortly."
Dashboard welcome subtitle on next visit: "You accepted your first proposal. {guestFirstName} is getting ready for their stay."

**Subsequent proposal accepted:**
Toast notification (4s auto-dismiss):
"Proposal accepted. {guestFirstName} has been notified."

---

## Proposal Declined

Toast notification (4s auto-dismiss):
"Proposal declined. {guestFirstName} has been notified."
Subtitle: "You can always message them if you'd like to suggest different dates."

This is not a celebration — the tone is neutral and factual. We acknowledge the host's decision without judgment.

---

## Proposal Counter-Offer Sent

Toast notification (4s auto-dismiss):
"Counter-offer sent to {guestFirstName}. You'll be notified when they respond."

---

## Photo Uploaded

**First photo on a listing:**
Inline confirmation below the photo upload area:
"Great first photo! Listings with multiple photos get more proposals. Add a few more to show off your space."

**Additional photos:**
Toast notification (3s auto-dismiss):
"Photo added."

**All recommended photos added (5+):**
Inline message:
"Nice photo set! You have {n} photos — guests will get a great sense of your space."

---

## House Manual Completed

Inline confirmation on the house manual editor:
"House manual saved. Guests will see this after their booking is confirmed."

If this was the last onboarding step:
(See onboarding completion celebration in next section)

---

## Onboarding Step Completed

**Step 1 — Create Listing:**
Next-step hint updates: "Done! Now let's add photos so guests can see your space."

**Step 2 — Add Photos:**
Next-step hint updates: "Photos look great. Next, let's set your pricing."

**Step 3 — Set Pricing:**
Next-step hint updates: "Pricing is set. Now add a quick house manual so guests know what to expect."

**Step 4 — House Manual:**
Next-step hint updates: "Almost there! One last step — go live and start receiving proposals."

**Step 5 — Go Live (Onboarding Complete):**
Onboarding section transforms (see intervention-specs.md INT-SUCCESS-2):
Title: "You're all set! Your listing is live."
Body: "Guests in {neighborhood} can now find and book your space. We'll notify you when you get your first proposal."
CTA: "View Your Live Listing"

---

## First Earnings Posted

**On first visit to dashboard after first payout:**
Earnings card celebration (see intervention-specs.md INT-SUCCESS-1):
Value: "${amount}"
Subtitle: "You just earned your first payout on Split Lease. This is just the beginning."

Count-up animation from $0 to ${amount} over 1 second. Brief confetti within card.

---

## Listing Changes Saved

Toast notification (3s auto-dismiss):
"Changes saved."

If significant changes (pricing updated):
"Pricing updated. Your new rates are live."

If availability changed:
"Availability updated. Your calendar is up to date."

---

## Profile Updated

Toast notification (3s auto-dismiss):
"Profile updated."

---

## Referral Sent

Inline confirmation on referral page:
"Invite sent to {email}. You'll earn $50 when they host their first guest."

---

## Payout Processed

Toast notification (4s auto-dismiss):
"Payout of ${amount} is on its way. It should arrive in your account within 2-3 business days."

---

## Review Received

Dashboard notification (inline, near proposals card):
"New review from {guestFirstName}: {starRating} stars."
CTA: "Read the review"

**5-star review:**
"New review from {guestFirstName}: 5 stars! Your guests are loving their experience."

---

## Toast Notification Specs

All success toasts follow the same pattern:
- Position: Top-right of viewport, 24px from edges.
- Background: var(--color-success-bg) (#E8F5E9).
- Left border: 4px solid var(--color-success) (#00C853).
- Text color: var(--color-neutral-900).
- Icon: Green checkmark circle, 20x20.
- Auto-dismiss: Duration specified per message (3-5 seconds).
- Manual dismiss: X button, top-right corner of toast.
- Stack: If multiple toasts, stack vertically with 8px gap, newest on top.
- Animation: Slide-in from right (200ms ease-out), fade-out (300ms) on dismiss.
- Max on screen: 3 toasts. If a 4th arrives, the oldest is dismissed immediately.
