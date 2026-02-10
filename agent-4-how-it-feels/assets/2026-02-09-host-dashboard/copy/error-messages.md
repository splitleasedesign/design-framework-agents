# Error & Recovery Messages: Host Dashboard

Agent: 4 (How it Feels)
Date: 2026-02-09
Scope: Every error state a host could encounter on or triggered from the dashboard.

---

## Principles for Error Copy

1. **Say what happened, not who's to blame.** Never "You entered invalid data." Instead: "This field needs a valid email address."
2. **Say what to do next.** Every error message includes a recovery action.
3. **Stay calm.** Errors are stressful enough. The copy should lower the temperature, not raise it.
4. **Be specific.** "Something went wrong" is forbidden. Name the thing that didn't work.
5. **Preserve the host's work.** Always mention if data was auto-saved. If not, explain how to recover.

---

## Network & Connection Errors

**Internet connection lost:**
Toast notification (persistent until resolved):
"You're offline. Changes you make will be saved once your connection is back."
Icon: Grey wifi-off icon.
Behavior: Persists until connection restores. On reconnect, changes to: "You're back online. All changes have been saved." (auto-dismisses after 4s).

**Server error (500):**
Toast notification (persistent, manual dismiss):
"Something didn't load correctly. Try refreshing the page."
CTA: "Refresh" (button that triggers page reload).
If persists after refresh: "We're having a temporary issue. Your data is safe — try again in a few minutes."

**Request timeout:**
Toast notification (persistent, manual dismiss):
"This is taking longer than expected. Check your internet connection and try again."
CTA: "Try Again" (retries the failed request).

---

## Listing Save Errors

**Listing failed to save (generic):**
Toast notification (persistent, manual dismiss):
"Your changes didn't save. Check your connection and try again."
CTA: "Try Again"
Subtitle: "Your draft is still here — nothing was lost."

**Listing failed to save (validation error):**
Inline error on the specific field:
"This field is required." / "Price must be at least $1." / "Please add at least one photo."
Toast summary: "Some fields need your attention. Scroll up to see what's highlighted."

**Listing failed to publish:**
Toast notification (persistent, manual dismiss):
"Your listing couldn't go live right now. Your draft has been saved."
CTA: "Try Again"
If the issue is a missing required field: "Your listing needs a few more details before it can go live. [See what's missing]"

---

## Photo Upload Errors

**Photo failed to upload (file too large):**
Inline error below the upload area:
"This photo is too large. Please use a photo under 10 MB."
Subtitle: "Tip: Most phone photos are under 5 MB."

**Photo failed to upload (wrong format):**
Inline error below the upload area:
"This file type isn't supported. Please use a JPG or PNG image."

**Photo failed to upload (server error):**
Inline error below the upload area:
"This photo didn't upload. Check your connection and try again."
CTA: "Retry Upload"

**Photo failed to upload (too many photos):**
Inline error below the upload area:
"You've reached the maximum of 20 photos for this listing. Remove one to add a new one."

---

## Proposal Response Errors

**Failed to accept proposal:**
Toast notification (persistent, manual dismiss):
"We couldn't confirm this proposal right now. Please try again."
CTA: "Try Again"
Subtitle: "The proposal is still waiting for your response — nothing has changed."

**Failed to decline proposal:**
Toast notification (persistent, manual dismiss):
"We couldn't process your response. Please try again."
CTA: "Try Again"

**Failed to send counter-offer:**
Toast notification (persistent, manual dismiss):
"Your counter-offer didn't send. Check your connection and try again."
CTA: "Try Again"
Subtitle: "Your counter-offer details are still saved — just hit send again."

**Proposal expired while responding:**
Modal (requires acknowledgment):
Title: "This proposal has expired"
Body: "The guest's requested dates have passed. You can still message {guestFirstName} to see if they're interested in other dates."
CTA: "Message {guestFirstName}" / "Close"

---

## Pricing Errors

**Invalid price entered:**
Inline error below the pricing field:
"Please enter a price between $1 and $9,999 per night."

**Pricing failed to save:**
Toast notification (persistent, manual dismiss):
"Your pricing didn't save. Check your connection and try again."
Subtitle: "Your previous pricing is still active."

---

## Availability / Calendar Errors

**Failed to block dates:**
Toast notification (persistent, manual dismiss):
"These dates couldn't be blocked. Please try again."
CTA: "Try Again"

**Failed to unblock dates:**
Toast notification (persistent, manual dismiss):
"These dates couldn't be unblocked. Please try again."
CTA: "Try Again"

**Conflict (dates already booked):**
Inline error on the calendar:
"Some of these dates already have confirmed bookings and can't be blocked."
Subtitle: "Only dates without bookings can be blocked."

---

## Account & Profile Errors

**Profile failed to save:**
Toast notification (persistent, manual dismiss):
"Your profile changes didn't save. Check your connection and try again."

**Invalid email format:**
Inline error below the email field:
"Please enter a valid email address (example: name@email.com)."

**Password change failed:**
Inline error:
"Your password couldn't be updated. Make sure your current password is correct."

---

## Payout Errors

**Payout method not set up:**
Inline message on earnings section:
"Set up your payout method to receive earnings."
CTA: "Add Payout Method"
Subtitle: "We support direct bank transfer and PayPal."

**Payout failed to process:**
Inline message on earnings section:
"Your latest payout couldn't be processed. Please check your payout method."
CTA: "Review Payout Settings"
Subtitle: "Your earnings are safe and will be sent once the issue is resolved."

---

## Referral Errors

**Referral invite failed to send:**
Inline error on the referral page:
"The invite couldn't be sent. Please check the email address and try again."

**Invalid referral email:**
Inline error below the email field:
"Please enter a valid email address."

**Self-referral attempt:**
Inline error:
"You can't send a referral to your own email address."

---

## Import Errors

**Listing import failed:**
Toast notification (persistent, manual dismiss):
"We couldn't import this listing. The link may be invalid or the listing may no longer be available."
CTA: "Try a Different Link"

**Partial import (some fields missing):**
Toast notification (auto-dismiss, 5s):
"Most details were imported successfully. A few fields need your attention."
CTA: "Review imported listing"
Subtitle: "We've highlighted the fields that need editing."

---

## Dashboard Load Errors

**Dashboard failed to load completely:**
Inline error replacing the stat cards:
"We're having trouble loading your dashboard. Your listings and data are safe."
CTA: "Refresh Page"
Subtitle: "If this keeps happening, contact us at support@splitlease.com."

**Individual stat card failed to load:**
Inside the stat card:
"Couldn't load this data right now."
CTA: "Retry"
(Other stat cards load normally — partial failure doesn't block the whole page.)

**Listings section failed to load:**
Inside the listings section:
"Your listings couldn't load right now. Please try refreshing."
CTA: "Refresh"

---

## Error Toast Notification Specs

All error toasts follow the same pattern:
- Position: Top-right of viewport, 24px from edges.
- Background: #FFF5F5 (very light red).
- Left border: 4px solid var(--color-error) (#D32F2F).
- Text color: var(--color-neutral-900).
- Icon: Red circle-X, 20x20.
- Persistent errors: Remain until manually dismissed (X button) or the issue is resolved.
- Auto-dismiss errors: Only for non-critical errors (partial import success, etc.).
- Stack: Same behavior as success toasts — stack vertically, newest on top, max 3.
- Animation: Slide-in from right (200ms ease-out). Shake animation on arrival (subtle horizontal shake, 300ms, 2px amplitude) to distinguish from success toasts without being alarming.
