# Task: Host Success Stories — Bare Functional Page
Date: 2026-02-10
Priority: Pipeline Step 1 of 4
Run ID: run-20260210-130900

## Objective
Produce the simplest possible HTML page that lets a visitor read host success stories and take action (list their property). No styling. No opinions about layout. Just raw function: every piece of content visible, every action reachable.

## Input — Raw Page Content

```
Page Title: Our Hosts' Success Stories

---

Testimonial 1:
Name: Emily Johnson
Profession: Graphic Designer
Photo: [avatar placeholder]
Pull Quote: "Maximize your unused space with Split Lease—flexible, reliable, and profitable short-term rentals."

Story:
As a graphic designer in New York City, I travel frequently for work, leaving my apartment empty for days. Split Lease has been a game-changer, allowing me to rent out my space during these periods. The registration and listing process was straightforward, and the platform's flexibility is perfect for my needs, letting me rent out my apartment only on the nights I'm away.

The verification process for guests gave me peace of mind, ensuring trustworthy renters. Communication tools made coordinating with guests easy, and my first experience was seamless, with the guest leaving my apartment in great condition. Over the past six months, I've hosted several guests, earning extra income that has helped me save for a vacation and cover unexpected expenses.

One of the highlights of using Split Lease is the supportive community and excellent customer service. Connecting with other hosts and getting prompt assistance from the Split Lease team has made the experience smooth and stress-free.

Split Lease has provided a flexible, reliable, and profitable way to rent out my apartment. I highly recommend it to anyone looking to make the most of their unused space.

---

CTA Section:
Headline: Let's Find Your Ideal Tenant
Button: List Your Property
```

## Context
This is a marketing/social-proof page on Split Lease (NYC rental platform). Its job:
- **User goal:** Prospective host reads real stories → gains confidence → clicks "List Your Property"
- **Business goal:** Convert visitors into hosts by showing real success stories
- The page will eventually have multiple testimonials (Emily is the first)
- Page must work as a standalone — visitor may land here from Google or a referral link

## Process
1. **Map what this page must do functionally:**
   - Display the page title
   - Show host testimonial(s): name, profession, photo, quote, full story
   - Provide a clear CTA to list a property
   - Include navigation back to the main site (header/nav)
   - Work if there's 1 testimonial or 10
2. **Produce bare HTML** — semantic elements only:
   - `<header>` with site name + nav links
   - `<main>` with the page content
   - `<article>` for each testimonial
   - `<section>` for the CTA
   - `<footer>` optional
3. **Minimal CSS** — only what's needed for the page to not be broken:
   - Max 5 CSS rules (max-width, basic margin, nothing decorative)
4. **No icons, no colors, no fonts, no shadows** — that's Agent 3's job
5. **Mark structure with HTML comments** so Agent 2 can read the intent

## Eval Target
All must pass:
- [ ] Page title is visible
- [ ] Host name, profession, quote, and full story are all present
- [ ] Photo placeholder exists (can be an empty bordered div)
- [ ] CTA section with "List Your Property" action is present and clickable
- [ ] Site header with navigation exists
- [ ] Semantic HTML: article for testimonial, section for CTA
- [ ] Works with 1 testimonial — and would work with N testimonials (no hardcoded single layout)
- [ ] A first-time visitor can understand the page purpose within 3 seconds
- [ ] All actions are reachable without JavaScript
- Max retries: 3

## Output
Save to: `run-20260210-130900/step-1-works/host-success-stories.html`

## When Done
Update memory.md with: outcome | files produced | eval score | decisions made | patterns learned
