# Bug History

## 2026-02-09

### Host Proposals missing horizontal padding
- **Status:** Fixed
- **Area:** `page-host-proposals`
- **Issue:** Host Proposals content rendered full-bleed with no container padding, causing misalignment with the rest of the site.
- **Root cause:** The host proposals page did not have a `.container` wrapper while adjacent pages did.
- **Fix:** Wrapped host proposals content in `<div class="container" style="padding-top:32px;">...</div>` inside `#page-host-proposals`.
- **File changed:** `Site Current State/mockup - Claude/version-b - responsiveness.html`

### Guest Proposals missing horizontal padding
- **Status:** Fixed
- **Area:** `page-guest-proposals`
- **Issue:** Guest Proposals cards rendered outside the container, creating full-bleed content and inconsistent side padding.
- **Root cause:** The `.container` was closed immediately after the header, leaving proposal cards outside it.
- **Fix:** Kept the guest proposals cards inside the existing `.container` by moving the container close tag to the end of the section.
- **File changed:** `Site Current State/mockup - Claude/version-b - responsiveness.html`

### Follow-up hardening for proposals page gutters
- **Status:** Fixed
- **Area:** `page-guest-proposals`, `page-host-proposals`
- **Issue:** Padding still appeared inconsistent after first fix in some renders.
- **Fix:** Added page-specific layout rules to enforce top spacing and container side gutters for both proposals pages, and removed inline container top-padding styles.
- **File changed:** `Site Current State/mockup - Claude/version-b - responsiveness.html`
