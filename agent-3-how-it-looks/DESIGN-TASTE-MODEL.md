# The Design Taste Model for Split Lease AI Agents

**Purpose:** This document is a continuous quality reference for any AI agent generating UI code for the Split Lease platform. Load this as context before producing any interface. It tells you HOW TO JUDGE whether something looks right -- not what components to use, but how to evaluate whether the output meets the perceptual standard of a premium rental marketplace.

**Synthesized from:** Competitive field research (12 platforms), 50 award-winning design examples, perception science literature, pixel-level forensic analysis of Split Lease's current UI, and user trust research across peer-reviewed studies.

---

## Part 1: The Perception Stack

*What humans actually evaluate, in order of importance, when they see a UI.*

The Psychologist (Agent 3) and the Anthropologist (Agent 5) both constructed hierarchies of how users perceive design quality. Their models largely align but diverge on one key point: the Psychologist places cognitive fluency (internal consistency) as the master variable, while the Anthropologist places photo quality as the top factor. The resolution: both are correct at different timescales. Photo quality dominates the **content** judgment (is this listing worth clicking?), while cognitive fluency dominates the **platform** judgment (is this site worth trusting?). For an AI agent generating UI code, the platform judgment is what you control. Photo quality is a content problem. Therefore, the stack below prioritizes what the AI agent can directly affect.

### Level 1: The 50-Millisecond Sweep (Pre-Attentive Processing)

Users form stable aesthetic judgments in 50 milliseconds (Lindgaard et al., 2006). In that window, the brain evaluates:

| Attribute | What the brain asks | Measurable proxy | Threshold |
|---|---|---|---|
| Visual complexity | Is this simple or chaotic? | Number of distinct visual elements above the fold | Fewer than 7 primary groups |
| Color harmony | Do these colors belong together? | Number of distinct hues (excluding grays and semantic status colors) | 3 or fewer active hues |
| Whitespace ratio | Does this feel spacious or cramped? | Empty pixels / total pixels above the fold | At least 40% whitespace |
| Prototypicality | Does this look like what I expect a rental site to look like? | Adherence to category conventions (header/search/cards/map pattern) | Recognizable within category norms |
| Visual hierarchy | Can I immediately tell what matters? | Size/weight contrast between the primary element and everything else | Primary element is at least 1.5x the visual weight of secondary elements |

**If Level 1 fails, nothing else matters.** The user has already formed a negative impression that colors every subsequent interaction (Thorndike's Halo/Horns Effect). For Split Lease specifically, because the platform has zero brand trust to offset a bad first impression, the 50ms sweep must pass perfectly.

### Level 2: The Fluency Scan (2-5 Seconds)

After the initial sweep, the brain begins processing relationships between elements. This is where cognitive fluency (Reber, Schwarz, & Winkielman, 2004) becomes the dominant variable. The brain asks:

| Attribute | What the brain asks | Measurable proxy | Threshold |
|---|---|---|---|
| Spacing consistency | Is there an underlying order? | All spacing values are multiples of a single base unit (4px or 8px) | Zero arbitrary spacing values |
| Alignment discipline | Do elements line up? | All elements sit on an implied grid; no "almost-aligned" items | Zero elements offset by 1-3px from their alignment axis |
| Component consistency | Do similar things look the same? | Buttons, cards, inputs, and badges use unified border-radius, shadow, and padding systems | Same component type = same visual treatment everywhere |
| Typography coherence | Does text feel organized? | Maximum 3 font weights visible; heading line-height differs from body; measure under 75 characters | 3 weights, heading line-height 1.1-1.25, body 1.5-1.7 |

**The Uncanny Valley Warning:** The Psychologist's most critical finding is that a half-polished design is worse than either a clean wireframe or a fully polished product. Mixing custom elements with template defaults creates cognitive disfluency -- the brain enters "finished product" processing mode but stumbles on every inconsistency. A design that is 70% custom and 30% template will feel cheaper than a 100% template. This means: when generating UI, do not mix design languages. Either generate everything according to the Split Lease system, or nothing. Partial customization is the enemy.

### Level 3: The Trust Assessment (5-30 Seconds)

Once the brain accepts the visual surface, it evaluates trustworthiness. Stanford Web Credibility Research (Fogg et al., 2002) found that 46.1% of participants assessed credibility based on "design look" -- making it the single most-cited factor.

| Attribute | What the brain asks | Measurable proxy | Threshold |
|---|---|---|---|
| Completeness | Is this finished? | No placeholder text, no broken layouts, no gray boxes | Zero unfinished elements visible |
| Social proof | Do other people use this? | Review counts, rating displays, verification badges, transaction counts | At least one social proof element per major view |
| Professional imagery | Do the photos look real and good? | Consistent aspect ratios, consistent lighting quality, no obvious phone snapshots mixed with professional shots | All images in a single view share the same aspect ratio and treatment |
| Contact transparency | Can I reach someone? | Visible support path, real company information | At least one contact method visible from any page |

**Trust asymmetry:** Trust is fragile and asymmetric -- many positive signals to build, one negative signal to destroy (NN/g). For Split Lease's cold-start trust problem: every design flaw that Airbnb users would forgive ("it's just a bug") will be interpreted by Split Lease users as evidence of incompetence. The design must be more careful than Airbnb's, not less.

### Level 4: The Quality Differentiation (30+ Seconds)

This is where users distinguish "good" from "great." These factors only matter after Levels 1-3 pass.

| Attribute | What the brain evaluates | Measurable proxy |
|---|---|---|
| Motion quality | Do transitions feel physical or robotic? | Spring-based animations (150-300ms, ease-out or spring with 0.7-0.8 damping) |
| Information density management | Can I choose my depth of detail? | Multiple view modes available (grid vs list, map vs cards) |
| Empty state design | Does the product handle edge cases gracefully? | Every empty state has illustration, explanation, and next-action CTA |
| Micro-interactions | Does the interface respond to me intelligently? | Hover states, loading skeletons, confirmation animations present |

### Contradiction Resolution: Psychologist vs. Anthropologist

The Psychologist argues that cognitive fluency is the unified theory of perceived quality. The Anthropologist argues that trust signals (social proof, photos, completeness) are the primary drivers. The evidence supports a synthesis: cognitive fluency is the *mechanism* by which trust is perceived. Inconsistent spacing does not directly signal "untrustworthy" -- it creates processing disfluency, which creates a feeling of effort, which is interpreted as "something is wrong," which erodes trust. They are describing the same phenomenon at different levels of abstraction. For the AI agent, the practical implication is: enforce consistency first (it is the mechanism), then layer trust signals on top (they are the content).

---

## Part 2: The Quality Gap Analysis

*Where Split Lease currently sits vs. the best platforms, and what closing each gap looks like perceptually.*

### Gap 1: Spacing System -- Currently Absent

**Current state (Agent 4):** Split Lease has no consistent content density standard. The Host Overview page is 70% whitespace with massive card padding. The Explore/Search page is packed dense. The Listing Detail is well-balanced. These three pages look like they were designed by three different teams.

**Benchmark (Agent 1):** Airbnb uses 80px horizontal padding on large screens, 24px section breathing room, and a 35:65 whitespace-to-content ratio. Stripe uses an 8px base grid with exactly six spacing values (8, 16, 24, 32, 48, 64). Vercel uses a three-tier system: 48px between sections, 24px within sections, 12px within components.

**What closing it looks like perceptually:** Every page feels like it belongs to the same product. Scrolling from the homepage to the dashboard to a listing feels like walking through rooms in the same building -- different purposes, same architecture. The eye develops a rhythm. You stop noticing the spacing because it is perfectly predictable. The feeling shifts from "three different apps stitched together" to "one cohesive tool."

**Specific target:** Adopt an 8px base grid. Three spacing tiers: 48px (section breaks), 24px (group breaks), 12px (element breaks). Card internal padding: 24px. Page margin: 80px on desktop, 24px on mobile. Whitespace ratio target: 35-45% on all pages.

### Gap 2: Color System -- Purple Overload

**Current state (Agent 4):** Purple is used for everything: primary actions, links, selected states, prices, badges, map markers, and backgrounds. When green appears (Accept button, HOST badge, Invite Friends), it feels accidental. There is no secondary or tertiary color. No defined semantic palette.

**Benchmark (Agent 1):** Airbnb uses 5 colors total, 92% neutral, 8% accent. Sonder uses 3-4 colors. Stripe uses 8 colors but each has a precise function. The most consistent pattern: brand accent on fewer than 10% of pixels, with semantic colors (green/yellow/red) for status only.

**What closing it looks like perceptually:** Purple stops meaning "everything" and starts meaning "do this." Selected states, links, and prices stop fighting for the same visual channel. When you see purple, you know it is a call to action. When you see green, you know something succeeded. When you see red, you know something needs attention. The page becomes *readable* rather than *colorful*. Financial figures ($266.49/night) render in the primary text color (near-black), not purple -- money is information, not decoration.

**Specific target:** Purple (#2D1B69 or refined version) for primary CTAs and the brand mark only. Near-black (#1A1A2E) for headings and prices. Three-tier gray system for text hierarchy. Semantic colors: green for success/accept, amber for warning/pending, red for error/decline/cancel. Purple on fewer than 8% of total pixels per screen.

### Gap 3: Badge and Status System -- Currently Chaotic

**Current state (Agent 4):** "Host Review" is a purple outlined pill, "Proposal" is a dark filled badge, "New" is a purple outlined pill, "Pending" is a gray outlined dropdown, "Upcoming" is a light outlined pill, "HOST" is a green outlined badge. No unified system.

**Benchmark (Agent 1):** Stripe uses status pills with 4px border-radius, colored background at 12% opacity, and matching text color at 100%. This single pattern handles all status types. Airbnb uses filter pills (18px radius, 1px border) distinct from status badges.

**What closing it looks like perceptually:** Badges become a language. You see a green-tinted pill and know immediately: something is confirmed. You see an amber-tinted pill and know: something is waiting. You do not need to read the text to understand the status. The badges disappear as visual noise and become visual data. The proposals page, the messages page, and the leases page feel like different views of the same system, not different products.

**Specific target:** One badge component with variants based on semantic color. Background: status color at 12% opacity. Text: status color at 100%. Border-radius: 6px. Height: 24px. Padding: 4px 10px. Font: 12px/500 weight, uppercase tracking 0.04em.

### Gap 4: Information Density Bifurcation

**Current state (Agent 4):** The product swings between extremely sparse (Host Overview) and extremely dense (Explore/Search). There is no consistent middle ground.

**Benchmark (Agent 1):** Airbnb maintains 35:65 whitespace-to-content on search. Zillow achieves high density (20:80) but manages it with the split map/list layout. Sonder uses 45:55 for luxury feel. The key insight: density should be intentional, not accidental.

**What closing it looks like perceptually:** Dashboard pages feel purposeful rather than empty. Search pages feel organized rather than overwhelming. The transition between pages does not require the user to recalibrate their scanning behavior. Empty states have illustrations and guidance, transforming "nothing here" into "here is what to do next." The feeling shifts from "some pages are unfinished" to "every page is designed for its purpose."

**Specific target:** Dashboard pages: 35:65 whitespace-to-content. Search pages: 25:75. Listing detail: 30:70. All pages share the same spacing base grid, type scale, and component library. Empty states include: illustration (120x120px), heading (20px/600), description (14px/400), and primary CTA button.

### Gap 5: Typography Lacks Depth

**Current state (Agent 4):** Most pages use only two levels: bold headings and regular body. The proposals page achieves five levels and is the best-structured page.

**Benchmark (Agent 1):** Airbnb uses 3 weights (400/500/600). Stripe uses a tight type scale (11px through 28px) with 3 weights (400/500/600). Vercel's Geist system defines 5 text color levels.

**What closing it looks like perceptually:** Text itself creates hierarchy. You can remove all colors, borders, and backgrounds and still understand what is a heading, what is a description, what is metadata, and what is a timestamp. The page feels layered -- like looking through depth rather than at a flat surface. The proposals page already achieves this; every other page should match it.

**Specific target:** 5 text levels. Primary (#1A1A2E) for headings and key values. Secondary (#4A4A5A) for descriptions and body. Tertiary (#717185) for metadata (bed/bath count, property type). Quaternary (#9B9BAE) for timestamps and "posted X days ago." Quinary (#C4C4D0) for disabled and placeholder text. Weights: 400 (body), 500 (navigation/emphasis), 600 (headings/prices). Body line-height: 1.5. Heading line-height: 1.2. Large headings: letter-spacing -0.02em.

---

## Part 3: The Pattern Library of Taste

*The 20 most powerful design techniques extracted from award-winning work, calibrated for AI generation.*

### 1. Three-Tier Spacing Hierarchy

**Principle:** Use exactly three spacing values for layout: large (48px) between major sections, medium (24px) between related groups, small (12px) between elements within a group.

**Cheap version:** Spacing is chosen arbitrarily for each element. Some gaps are 15px, others 23px, others 30px. Sections run together because there is no clear differentiation between "new section" and "next element." The page looks like a vertical stack of components with random gaps.

**Premium version:** Every gap is one of three values. Sections are immediately distinguishable by the 48px gap before them. Related elements cluster at 12px. The 24px mid-level groups elements into subsections. The user intuitively understands information grouping without any divider lines or background boxes. The interface has a vertical beat.

**Self-check:** "Can I replace every divider line on this page with spacing alone and still see the grouping?"

### 2. Five-Level Text Hierarchy

**Principle:** Define exactly 5 text color/opacity levels, each with a specific semantic role. Hierarchy is created through weight and color, not just size.

**Cheap version:** Two text colors: black for important, gray for less important. Everything is either fully prominent or washed out. Labels, metadata, timestamps, and descriptions share the same gray.

**Premium version:** Five distinct levels. Property name in primary (dark, 600 weight). Description in secondary (medium, 400 weight). "3 bed, 2 bath" in tertiary (lighter, 400 weight). "Listed 5 days ago" in quaternary (muted, 400 weight). Disabled text in quinary (very light). Every piece of text has a specific visual rank.

**Self-check:** "If I removed all color and borders, could a user still understand the information hierarchy from text weight and brightness alone?"

### 3. Multi-Layer Shadows for Depth

**Principle:** Use 2-3 shadow layers (tight/close for definition, diffuse/far for atmosphere) instead of a single box-shadow.

**Cheap version:** `box-shadow: 0 2px 8px rgba(0,0,0,0.15)`. Flat, stamped-on appearance. All elevated elements use the same shadow.

**Premium version:** `box-shadow: 0 1px 2px rgba(0,0,0,0.06), 0 4px 8px rgba(0,0,0,0.04), 0 12px 24px rgba(0,0,0,0.03)`. Three layers mimicking real light: contact shadow, penumbra, ambient shadow. On hover, only the far layer intensifies. Cards at low elevation, dropdowns at medium, modals at high.

**Self-check:** "Does this shadow look like it was cast by a real light source above and slightly in front, or does it look like a gray border?"

### 4. Strategic Color Scarcity

**Principle:** Use color on fewer than 5-8% of the screen's total pixel area. Make the rare colored elements carry meaning.

**Cheap version:** Colored badges, colored section headers, colored sidebar, colored buttons in every card, colored charts. The eye has no guidance on what to look at first.

**Premium version:** The entire interface is grayscale except for primary CTA buttons, status indicators, and error states. When a red error appears, it is the only red on the screen -- impossible to miss. When the purple "Submit Proposal" button appears, it magnetically draws the eye.

**Self-check:** "If I printed this page in grayscale, would I lose any critical information -- or only the calls to action?"

### 5. Single-Hue Multi-Opacity State System

**Principle:** Use one brand hue at different opacities for all interactive states: hover (4-6%), pressed (8-10%), selected (12-15%), focus ring (100%).

**Cheap version:** Hover is #E8E8E8, active is #D0D0D0, selected is #B0D4FF. Different colors for each state that do not feel related.

**Premium version:** Brand purple at 4% opacity for hover, 8% for pressed, 12% for selected, 100% for focus rings. One variable change updates every interactive state. All states harmonize automatically.

**Self-check:** "Are all my interactive state colors mathematically derived from a single brand color?"

### 6. Content-Width Constraint for Readability

**Principle:** Constrain body text to 640-720px max-width (60-75 characters per line), even when the viewport is wider. Let images and data go wider.

**Cheap version:** Text spans the full container (1000-1200px). Lines exceed 100 characters. The page feels like a spreadsheet.

**Premium version:** Body text at 640px. Images and galleries at 1200px. This creates rhythmic width variation: wide (images), narrow (text), wide (data). Property descriptions read like editorial features, not database dumps.

**Self-check:** "Is any line of body text longer than 75 characters?"

### 7. Image-First Card Design

**Principle:** Define cards by the image + text grouping, not by visible containers. When borders exist, they should be 1px or lighter.

**Cheap version:** Every card has a visible border, a shadow, a background color, rounded corners, and a hover shadow change. Five visual treatments per card. The grid feels heavy and decorated.

**Premium version:** Cards have no visible container. The image sits directly in the grid with text below, grouped by proximity alone. The gestalt principle of proximity does the work. One or at most two visual treatments per card.

**Self-check:** "How many distinct visual treatments (border, shadow, background, radius, hover-effect) does this card use? If more than 2, which can I remove?"

### 8. Asymmetric Animation Timing

**Principle:** Elements appear fast (0-100ms) and disappear gently (100-300ms). Use different easing curves for appearing vs. dismissing.

**Cheap version:** All animations use `transition: all 0.3s ease`. Everything moves the same way at the same speed. Motion feels robotic.

**Premium version:** Dropdown appears in 100ms with ease-out. Dropdown dismisses in 200ms with ease-in-out. Modal enters in 200ms, exits in 250ms. Tooltips snap in (80ms), fade out (150ms). The interface feels responsive when you ask for something and gentle when you dismiss something.

**Self-check:** "Does this opening animation feel snappy? Does this closing animation feel smooth? Are they different?"

### 9. Bilateral Map-List Connection

**Principle:** In split-panel layouts (list + map), hovering a list item highlights the map pin AND hovering a pin highlights the list item.

**Cheap version:** Map and list share data but have no visual connection. Users must mentally correlate between two disconnected views.

**Premium version:** Hovering a property card highlights its map pin (scale 1.3x, z-index boost, filled background). Hovering a map pin scrolls the list to the card and gives it a 2px accent border. Price labels in map pins match card typography. The two panels feel like one interface viewed through two lenses.

**Self-check:** "If I hover a card, does the map respond? If I hover a pin, does the list respond?"

### 10. Descending Border-Radius by Container Hierarchy

**Principle:** Larger containers get larger radii, smaller elements get smaller radii. This creates a natural visual hierarchy by size.

**Cheap version:** Everything uses 8px border-radius. Cards, buttons, badges, and inputs are all the same. No differentiation between container types.

**Premium version:** Cards and modals: 12px. Inputs and buttons: 8px. Badges and pills: 6px. Dot indicators: 50%. The radius itself communicates what type of element you are looking at.

**Self-check:** "Do my cards have a larger border-radius than my buttons, and my buttons larger than my badges?"

### 11. Inset Shadows on Form Inputs

**Principle:** Use `inset 0 1px 2px rgba(0,0,0,0.06)` on form inputs to create a "recessed" feel, making inputs appear physically pressed into the surface.

**Cheap version:** Flat inputs with only a border. They sit on the same plane as everything else. The form feels like a wireframe.

**Premium version:** Inputs have a subtle inset shadow that makes them appear recessed. Buttons have outward shadows (elevated). The form has a physical material quality: buttons push out, inputs push in.

**Self-check:** "Can I tell the difference between a clickable button and a typeable input by shadow direction alone?"

### 12. Error States as Zones, Not Lines

**Principle:** Combine red border + barely perceptible background tint (red at 2% opacity) + a shake animation (200ms, translateX 0 > -4px > 4px > 0) for errors.

**Cheap version:** Red border. Red text below. The error is a label attached to a field.

**Premium version:** The field gets a red border, a 2% red background tint creating a visual "zone," a quick shake animation for attention, and an error message that slides in from below. The error is an experience, not a state change.

**Self-check:** "Is the error visible in peripheral vision (the shake and tint), or does the user have to scan for a red border?"

### 13. Staggered Entry Animations for Grids

**Principle:** When loading a grid of cards, stagger each card's entrance by 50ms so they cascade into view.

**Cheap version:** All cards appear simultaneously with no animation. The grid appears as a flat block.

**Premium version:** Cards enter with 50ms stagger: each fades in (opacity 0 to 1) while translating up (12px to 0) over 300ms. The cascade takes approximately 800ms for 12 items. The page feels assembled rather than stamped.

**Self-check:** "When this grid loads, does it feel like a curtain revealing or a light switching on?"

### 14. Price-Labeled Map Pins

**Principle:** Map pins show the per-night or per-week price inside them, turning the map into a pricing comparison tool.

**Cheap version:** Generic colored dots on the map. Users must click each dot to see the price.

**Premium version:** Each pin is a white pill with price text (12px/600). On hover, the pill scales to 1.1x and gains the brand background color. The map simultaneously shows spatial information and pricing information, becoming one of the most useful views for comparison shopping.

**Self-check:** "Can a user compare prices of three properties by looking only at the map, without clicking anything?"

### 15. Tabular Numerals for Data Alignment

**Principle:** Use `font-variant-numeric: tabular-nums` for all number displays in tables, prices, and metrics.

**Cheap version:** Proportional numerals where "1" is narrower than "0." Price columns misalign. Dashboard metrics shift width when values update.

**Premium version:** Every digit has the same width. Price columns align at the decimal point. Metric cards maintain stable widths. The numbers feel engineered.

**Self-check:** "Are the decimal points in this column of prices perfectly vertically aligned?"

### 16. The Bento Photo Grid

**Principle:** Use a 5-image gallery with 1 large image (50% width, 100% height) on left and 4 smaller images in a 2x2 grid on right, with 8px gaps and 12px outer corner radius.

**Cheap version:** A single hero image, or a basic carousel with dots. The listing feels like a classified ad.

**Premium version:** The bento grid shows 5 images simultaneously, giving the user a comprehensive visual impression without clicking. The large image anchors attention. The smaller images provide context. The grid has rounded outer corners and square inner corners, creating a cohesive visual block.

**Self-check:** "Can the user see at least 4 property images without clicking or scrolling?"

### 17. Unified Hover Activation

**Principle:** When a card is hovered, both the image treatment and the text treatment change simultaneously. The card feels like a single interactive surface.

**Cheap version:** Only the shadow changes on hover. Or only the image zooms. The text remains static while the image moves, creating a disconnect.

**Premium version:** On hover: shadow deepens, image may zoom subtly (1.02-1.03x), and text opacity shifts from 85% to 100%. All three changes happen in the same 200ms transition. The card activates as a unified object.

**Self-check:** "When I hover this card, do ALL its elements respond, or just one?"

### 18. Semantic Background Alternation Instead of Borders

**Principle:** Replace divider lines between sections with alternating background colors (#FFFFFF and #F9FAFB) for softer separation.

**Cheap version:** 1px border lines between every section. The page looks like a wireframe or spreadsheet.

**Premium version:** Odd sections on white, even sections on near-white (#F9FAFB). No visible dividers. Sections are distinguished by background, not borders. The page feels continuous rather than segmented.

**Self-check:** "Can I remove every horizontal rule on this page and still see where one section ends and the next begins?"

### 19. The Sticky Action Sidebar

**Principle:** On detail pages, the primary conversion action (booking widget, proposal form) lives in a sticky right sidebar (320-380px wide) with `position: sticky; top: 80px`.

**Cheap version:** The CTA is at the top of the page and scrolls away. Or it is at the bottom and requires scrolling to reach.

**Premium version:** The booking sidebar remains visible throughout the entire scroll. It has a 1px border, 12px border-radius, subtle dual-layer shadow, and 24px internal padding. The price is always visible. The CTA button is always one click away.

**Self-check:** "Can the user always see the primary CTA without scrolling, even on a long listing page?"

### 20. Spring Physics over Ease Curves

**Principle:** Replace `ease` and `ease-out` with spring-based animations (damping 0.7-0.8) for interactive state changes. The slight overshoot creates physical realism.

**Cheap version:** `transition: all 0.3s ease`. Elements slide to their destination and stop. Motion feels like ice skating.

**Premium version:** Elements overshoot by approximately 5% before settling back. A dropdown opening bounces slightly past its final height. A card lift goes from 0 to -5px to -4px. The interface feels like it is made of material with mass and elasticity.

**Self-check:** "Does this animation feel like a physical object settling, or like a cursor moving on a screen?"

---

## Part 4: The Decision Framework

*When generating UI code and facing a specific design decision, use these decision trees.*

### If Building a Card (Listing Card, Proposal Card, Dashboard Card)

1. **Image ratio:** Use 20:19 (near-square) for browse/search cards, 16:9 for dashboard thumbnails, 3:4 (portrait) for editorial/luxury contexts. Never use an arbitrary ratio.
2. **Shadow depth:** Use 0-1 treatments. If the card sits on a white background, use a subtle border (1px #E5E5E5) OR a light shadow (0 1px 3px rgba(0,0,0,0.08)), not both.
3. **Corner radius:** 12px for the card outer container. Images clip to the card radius via overflow: hidden. No separate radius on the image.
4. **Text levels:** Maximum 4 in a card. Title (16px/600, primary color), subtitle (14px/400, secondary), metadata (14px/400, tertiary), price (18px/600, primary). Never 5+ levels inside one card.
5. **Padding:** Internal padding: 16-20px below the image. Zero padding on the image itself (it bleeds to card edges). Gap between text lines: 4-6px.
6. **Hover state:** Shadow deepens by one level + text opacity shifts from 90% to 100%. No scale transform greater than 1.02. No color changes on hover.
7. **Action buttons on cards:** Maximum 1 primary CTA visible per card. Secondary actions appear on hover or inside the detail view. Two buttons on every card creates button fatigue.

### If Building a Dashboard (Host Overview, Analytics, Metrics)

1. **Information density:** Target 30-40% whitespace. Show 3-5 stat cards at top, then one primary content section, then secondary sections. Never show 8+ metrics simultaneously.
2. **Stat card anatomy:** Metric label (12px/500, uppercase, letter-spacing 0.04em, tertiary color), metric value (24-28px/500, primary color), trend indicator (13px/400, semantic color: green up, red down). The contrast between tight 16px padding and 24px metric number creates focus within density.
3. **Whitespace ratio:** 35-40% minimum. If the page feels sparse (70%+ whitespace, as current Host Overview), the content needs restructuring: tighter cards, more data per view, or a sidebar layout.
4. **Section breathing room:** 48px between major sections. 24px between section heading and its content. 12px between items within a section.
5. **Empty states:** If fewer than 3 items exist, show an illustrated empty state with explanation and CTA. Never render a card with empty/placeholder data.

### If Building a Form (Profile, Listing Creation, Booking Sidebar)

1. **Label weight:** 14px/500, secondary color. Labels sit directly above inputs with 6px gap. The label-to-input distance must be less than 50% of the input-to-next-label distance.
2. **Input height:** 44px standard, 40px compact. Border: 1px solid #D0D0D8. Border-radius: 8px. Inset shadow: `inset 0 1px 2px rgba(0,0,0,0.06)`. Focus: 2px ring in brand purple with 2px offset.
3. **Spacing between fields:** 20-24px between complete field groups (label + input). 12px between stacked elements within a group (e.g., label and its help text).
4. **Button prominence:** Primary submit button: full width within its container, 48px height, brand purple fill, 16px/600 white text. Secondary actions: outlined style, never competing visually with the submit.
5. **Validation:** Use the Zone of Error pattern: red border (1px) + red background tint (2% opacity) + error message slides in below (200ms, translateY 8px to 0). Shake on submit if validation fails.

### If Building a Listing Page (Property Detail)

1. **Photo gallery:** Bento grid: 1 large (50% width) + 4 small (2x2 grid). 8px gaps. 12px outer corner radius. "Show all photos" button overlays bottom-right image.
2. **Sticky sidebar:** Position: sticky; top: 80px. Width: 340-380px. Border: 1px #E0E0E0. Border-radius: 12px. Shadow: 0 6px 16px rgba(0,0,0,0.12). Internal padding: 24px.
3. **Content layout:** 60:40 split (content left, sidebar right) at max-width 1120px. Body text max-width: 680px within the left column.
4. **Section headings:** 22px/600, primary color. 48px spacing above each new section. 16px spacing between heading and first content element.
5. **Amenities grid:** 2-column layout with 44px row height. Each amenity: 24px icon + 16px/400 text. 16px row-gap.
6. **Host section:** Host avatar (48-56px circle), name (16px/600), response stats (14px/400, tertiary color). Include a "Message Host" CTA.

### If Building a Search/Explore Page

1. **Map integration:** Split layout: 55% list / 45% map on desktop. Map pins show prices (white pill, 12px/600 text). Bilateral highlighting between list and map.
2. **Card density:** 3 columns on desktop, 2 on tablet, 1 on mobile. Cards per viewport: 6-9. Image-first with near-square (20:19) or 4:3 ratio.
3. **Filter treatment:** Horizontal filter bar with pill-shaped controls. Height: 36px. Border-radius: 18px (full pill). Border: 1px #D0D0D8. Active filter: 2px border in brand purple. The Split Lease day-of-week selector must appear prominently in the filter bar.
4. **Sort controls:** Dropdown or segmented control, right-aligned above the card grid. 14px/500, secondary color. Not competing with filter bar.
5. **Results count:** "28 Listings in NYC" in 14px/400, tertiary color, above the grid. Quiet but present.

### If Building a Modal or Overlay

1. **Backdrop:** rgba(0,0,0,0.5) overlay. On close, backdrop fades out over 200ms.
2. **Modal container:** Max-width 560px (small) or 720px (large). Border-radius: 12px. Shadow: 0 8px 30px rgba(0,0,0,0.15). Padding: 24-32px.
3. **Header:** Title (20px/600) + close X button (top right, 32px hit target). 1px divider below header.
4. **Actions:** Primary button full-width at bottom. Cancel as text link or secondary button, not competing visually.
5. **Animation:** Enter: 200ms ease-out, scale 0.95 to 1.0 + opacity 0 to 1. Exit: 150ms ease-in, opacity 1 to 0.

### If Building a Progress/Lifecycle Component (Proposal Stepper)

1. **Step indicator:** Circles (24px diameter) connected by 2px lines. Completed: filled in brand purple. Current: filled with a glow ring. Upcoming: gray outline.
2. **Step labels:** 12px/500 below each circle. Current step label in primary color. Others in tertiary.
3. **Spacing:** Equal horizontal distribution. Minimum 80px between step centers.
4. **Mobile adaptation:** Switch to vertical layout with steps stacked. Lines become vertical connectors.

---

## Part 5: The Anti-Patterns

*The 15 most common things AI generates that immediately make a design look like a template.*

### Anti-Pattern 1: Uniform Card Grids with No Hierarchy

**What it looks like:** Every card is exactly the same size. A 3x4 grid of identical rectangles with identical shadows.

**Why it happens:** AI generates grids from arrays, and arrays have uniform items. The code `cards.map(card => <Card />)` produces visual uniformity.

**What to do instead:** Make the first card span 2 columns, or alternate between feature cards (larger) and standard cards. If all cards must be equal, differentiate through content hierarchy (a verified host gets a badge, a popular listing gets a "Popular" indicator). The grid should have at least one visual interruption.

### Anti-Pattern 2: Using Purple (or Any Brand Color) for Everything

**What it looks like:** Purple buttons, purple links, purple prices, purple badges, purple map pins, purple progress bars, purple backgrounds. The page is a purple monochrome.

**Why it happens:** AI reads "brand color: purple" and applies it to every possible element. The instruction "use the brand palette" is interpreted as "make everything brand-colored."

**What to do instead:** Purple appears ONLY on primary CTA buttons and the logo. Prices are near-black. Links are near-black with underline. Badges use semantic colors (green/amber/red) at 12% opacity. Progress bars use semantic colors. The brand color should cover fewer than 8% of pixels.

### Anti-Pattern 3: Identical Shadows on Everything

**What it looks like:** Cards, buttons, inputs, dropdowns, and modals all use `box-shadow: 0 2px 8px rgba(0,0,0,0.1)`. Flat, uniform, like stickers on a page.

**Why it happens:** AI applies one shadow value to all elevated elements. The concept of "elevation levels" is not encoded in typical instructions.

**What to do instead:** Define 3 shadow levels. Low: `0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.06)` for cards. Medium: `0 4px 16px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04)` for dropdowns. High: `0 12px 40px rgba(0,0,0,0.12), 0 4px 8px rgba(0,0,0,0.06)` for modals. Each uses at least two layers.

### Anti-Pattern 4: Giant Spacing with No Content

**What it looks like:** A page with one heading, two cards, and massive white gaps between everything. The footer is visible on a page that should have content.

**Why it happens:** AI applies generous spacing recommendations universally without adjusting for content volume. "Use more whitespace" is interpreted as "add padding to everything."

**What to do instead:** Whitespace should be proportional to content. A page with one item needs a different layout than a page with twenty items. For near-empty pages, consolidate into a single centered column with an empty-state illustration. The page should never feel like it is mostly blank -- that signals "unfinished," not "premium."

### Anti-Pattern 5: Scroll-Triggered Entrance Animations on Content

**What it looks like:** Cards fade up as you scroll. Text slides in from the left. Every element has a 500ms entrance animation triggered by scrolling.

**Why it happens:** AI associates "premium" with "animated," and scroll-triggered animations were trendy circa 2014-2018 (WOW.js, AOS.js). Training data contains many examples.

**What to do instead:** Use animation for state changes (hover, click, expand, collapse), not page decoration. Content should be visible when the user scrolls to it, not performing a dance. If entry animation is needed, use a single staggered cascade on page load, not scroll-triggered per-element animations.

### Anti-Pattern 6: Too Many Font Weights and Sizes

**What it looks like:** 300 weight for subtitles, 400 for body, 500 for labels, 600 for subheadings, 700 for headings, 800 for hero text. Six different sizes in one card.

**Why it happens:** AI tries to create hierarchy by using every available weight. "Make this stand out more" translates to "increase the weight."

**What to do instead:** Maximum 3 weights: 400 (body), 500 (navigation/emphasis), 600 (headings). Create hierarchy through color/opacity differences, not weight escalation. If two elements are both 600 weight, differentiate them by size or color.

### Anti-Pattern 7: Borders AND Shadows AND Background Colors on the Same Card

**What it looks like:** A card with `border: 1px solid #E5E5E5`, `box-shadow: 0 2px 8px rgba(0,0,0,0.1)`, and `background: #FAFAFA` on a `#FFFFFF` page. Triple visual treatment.

**Why it happens:** AI applies every available differentiation technique simultaneously. Each line of CSS adds a "card-like" property.

**What to do instead:** Choose ONE differentiation method per card. Either a subtle border, or a subtle shadow, or a background color difference. Premium platforms use 1-2 treatments. Each additional treatment adds cognitive noise without adding information.

### Anti-Pattern 8: Linear Animation Timing

**What it looks like:** Elements move at constant speed. Dropdowns slide out linearly. Hover transitions use `transition: all 0.3s linear`.

**Why it happens:** `linear` is the simplest timing function. AI sometimes defaults to it, or uses `ease` for everything without considering the direction of animation.

**What to do instead:** Use `ease-out` for elements entering (fast start, slow settle). Use `ease-in` for elements leaving (slow start, fast exit). Use spring physics (damping 0.7-0.8) for interactive elements. Never use `linear` for UI transitions.

### Anti-Pattern 9: Same Line-Height for Headings and Body

**What it looks like:** A 48px heading with `line-height: 1.5` (72px total), creating vast gaps between heading lines. A card title with the same generous line-height as the body paragraph.

**Why it happens:** AI applies a single `line-height: 1.5` globally. This is correct for body text but wrong for headings.

**What to do instead:** Body text: line-height 1.5-1.6. Subheadings (18-22px): line-height 1.3-1.4. Headings (24-40px): line-height 1.15-1.25. Display text (40px+): line-height 1.05-1.15. Large headings also need negative letter-spacing (-0.01em to -0.03em).

### Anti-Pattern 10: Full-Width Text on Wide Screens

**What it looks like:** A property description that spans 1200px on a desktop monitor. Lines are 120+ characters long. Reading requires head movement.

**Why it happens:** AI uses `width: 100%` or the full grid column width for text containers. The concept of "measure" (optimal line length) is not standard in component libraries.

**What to do instead:** Constrain body text to max-width: 680px (approximately 65-75 characters per line). Images and data tables can go wider. The width constraint is on the text, not the page.

### Anti-Pattern 11: Button Fatigue -- Too Many CTAs per Card

**What it looks like:** Every listing card has "View Property" AND "Message Host" AND a heart icon AND a share icon. Four interactive elements on a 300px card.

**Why it happens:** AI generates all possible actions for every context. "The user might want to message, or view, or save, or share" results in all four being present.

**What to do instead:** Maximum 1 primary action per card (the entire card is clickable). Secondary actions (save, share) appear as subtle icons on hover. "Message" lives on the listing detail page, not on the card. Reduce visible actions to reduce decision paralysis.

### Anti-Pattern 12: Inconsistent Badge/Pill Styles

**What it looks like:** "Pending" uses a gray outlined pill. "New" uses a purple filled badge. "HOST" uses a green outlined tag. "Active" uses bold colored text with no container.

**Why it happens:** AI generates each badge in isolation, choosing whatever treatment seems appropriate for that specific label. Without a system constraint, each badge is designed independently.

**What to do instead:** One badge component with color variants. All badges: same height (24px), same border-radius (6px), same font size (12px/500), same padding (4px 10px). Color variants: background at 12% opacity, text at 100%. Green for success, amber for pending, purple for informational, red for error.

### Anti-Pattern 13: Decorative Colored Section Backgrounds

**What it looks like:** Alternating sections with full-width colored backgrounds: white, then pale blue, then white, then pale purple, then white. Colors have no semantic meaning -- they are purely decorative.

**Why it happens:** AI tries to create visual variety in long pages. "Make each section visually distinct" translates to "change the background color."

**What to do instead:** If background alternation is needed, use only two values: #FFFFFF and #F9FAFB (barely-off-white). If sections need stronger separation, use 48-64px spacing with a subtle 1px divider. Color in backgrounds should only appear when it carries meaning (e.g., an alert banner).

### Anti-Pattern 14: Missing or Generic Empty States

**What it looks like:** "No listings yet." in gray text centered in a white card. Or a blank area where listings would be.

**Why it happens:** AI focuses on the happy path. The empty state is an afterthought rendered with a single text node.

**What to do instead:** Every empty state needs three elements: (1) an illustration or icon (60-120px), (2) a heading explaining the state (16-20px/600), (3) a CTA that moves the user forward (primary button). Example: icon of a house + "Create your first listing" + "Get Started" button. Empty states are trust signals -- they prove the product is designed, not abandoned.

### Anti-Pattern 15: Footer as Junk Drawer

**What it looks like:** A footer containing an import form, referral CTA, app store badges, social links, legal links, company links, and a newsletter signup. Everything that did not fit on a page ends up in the footer.

**Why it happens:** AI places all "global" elements in the footer because the footer is the conventional location for site-wide content. Without curation, everything accumulates.

**What to do instead:** The footer should contain: (1) link columns organized by category (Company, For Hosts, For Guests, Support), (2) legal links (Privacy, Terms), (3) social icons. Maximum 4 columns. No forms. No complex CTAs. No functionality that belongs in the product itself. The footer is a site map, not a feature.

---

## Part 6: The Split Lease Taste Test

*30 evaluation questions an AI agent should run against any UI it generates. Score each Yes (1) or No (0).*

### Brand Identity (Questions 1-6)

1. **Does the header match Split Lease's pattern: logo left, dropdown menus center ("Host with Us," "Stay with Us"), pill CTA ("Explore Rentals") right, and auth links far-right?** The header is the brand's most recognizable element and must be consistent on every page.

2. **Is the Weekly Schedule Selector (S M T W T F S circles) present wherever users make day-of-week choices?** This includes: homepage hero, listing detail booking sidebar, proposal cards, and search filters. It is Split Lease's single most distinctive UI element.

3. **Is the Proposal Lifecycle Stepper (Submitted > Application > Review > Accepted > Signing > Active) present on all proposal cards, and does it use the same number of steps for both host and guest views?** Agent 4 noted the host version has 7 steps while the guest version has 6 -- they must be unified.

4. **Is the price formula transparent?** The booking sidebar must show: nightly rate, nights per week, weeks in reservation span, 4-week rent, and total. The formula ($X/night x Y nights x Z weeks) should be visible wherever a total is displayed.

5. **Are circular property images used only on the homepage hero (as the distinctive "floating circles" pattern) and not on search or listing pages?** Circular images are a homepage brand element; search and listing pages use standard rectangular images.

6. **Is the purple brand color restricted to primary CTA buttons, the header bar, and the logo, with prices and body text in near-black?** Purple should not appear on prices, metadata text, or secondary UI elements.

### Layout and Spacing (Questions 7-12)

7. **Are all spacing values multiples of 8px?** Check padding, margins, and gaps. No spacing value should be 15px, 17px, 23px, or any non-multiple of 4 (with 8 as the primary unit).

8. **Is the whitespace-to-content ratio between 30-45% on every page?** No page should be 70% whitespace (current Host Overview problem) or 15% whitespace (cramped search).

9. **Do all pages use the same three-tier spacing: 48px between sections, 24px between groups, 12px within groups?** The spacing should be identical whether on the dashboard, a listing, or the search page.

10. **Is the listing detail page using a 60:40 content-to-sidebar split with the booking sidebar sticky at top: 80px?** This is the industry standard pattern (Airbnb, Blueground, Zillow all use it).

11. **Is body text constrained to 680px max-width for readability?** Property descriptions, house rules, and about sections should not span the full content column.

12. **Are cards using image-first design with minimal container treatments (1-2 visual treatments max: either subtle border OR subtle shadow, not both)?** Cards should feel like content, not like decorated boxes.

### Typography (Questions 13-18)

13. **Does the interface use exactly 3 font weights: 400 (body), 500 (navigation/emphasis), 600 (headings/prices)?** Fewer than 3 creates flat hierarchy. More than 3 creates visual noise.

14. **Are there 5 visible text color levels (primary, secondary, tertiary, quaternary, quinary)?** Each information type should have a distinct brightness level. Headings and prices at primary. Descriptions at secondary. Metadata at tertiary. Timestamps at quaternary.

15. **Do headings use tighter line-height (1.15-1.25) than body text (1.5-1.6)?** A 40px heading with 1.5 line-height looks broken.

16. **Do large headings (24px+) use negative letter-spacing (-0.01em to -0.03em)?** Large text at default tracking looks loose and billboard-like.

17. **Are all number columns and price displays using `font-variant-numeric: tabular-nums`?** Prices must align vertically in lists. Dashboard metrics must maintain stable widths.

18. **Is the body font readable at the sizes used, with adequate contrast against the background?** Minimum 14px for body text. Color contrast ratio at least 4.5:1 for body text, 3:1 for large text (WCAG AA).

### Color and Visual System (Questions 19-24)

19. **Does the page use 3 or fewer distinct hues (excluding semantic status colors and the gray scale)?** Count the hues. If you see purple AND blue AND green AND orange on the same page (outside of status badges), the palette is too wide.

20. **Are status badges using the unified pattern: semantic color background at 12% opacity, text at 100%, same height/radius/font across all variants?** Check "Host Review," "Pending," "New," "Active," "Upcoming" -- they must all follow one pattern.

21. **Are interactive states (hover, pressed, selected, focus) all derived from the brand purple at different opacities (4%, 8%, 12%, 100%)?** Not separate, unrelated colors.

22. **Is the primary CTA button the most visually prominent element on the page?** It should be the only fully-saturated brand color element. If badges, links, and prices are also in full brand purple, the CTA loses prominence.

23. **Are shadows using at least 2 layers (tight + diffuse) and offset downward?** No single-layer `box-shadow: 0 0 10px` glow effects. All shadows should imply a light source above.

24. **Are error states using the Zone pattern (red border + 2% red background tint) rather than just a red border?** Errors should be visible in peripheral vision.

### Interactions and Motion (Questions 25-28)

25. **Do dropdowns, modals, and tooltips use 150-200ms animations with ease-out timing for entry?** No instant appearance (0ms) and no slow animations (400ms+). No linear timing.

26. **Is the map (on search/explore pages) bidirectionally connected to the listing cards?** Hovering a card highlights the pin. Hovering a pin highlights the card.

27. **Does the "Submit Proposal" or "Reserve" flow show a confirmation with visual feedback?** At minimum: button state change, loading indicator, and a confirmation checkmark animation or success state.

28. **Are hover states present on all clickable cards and interactive elements?** Every element that responds to click must visually respond to hover first. No "surprise" click targets.

### Trust and Completeness (Questions 29-30)

29. **Are all visible data fields populated with realistic, complete information?** No "Unnamed Listing," no "Address not available," no gray placeholder thumbnails. If data is missing, show a designed empty state, not raw database nulls.

30. **Is there at least one trust signal visible on every page that displays listing or transaction information?** Verification badges, review counts, response rate stats, "Strict" policy indicators, the proposal lifecycle stepper (which itself is a trust signal showing process transparency).

### Scoring Interpretation

- **27-30 (90-100%):** Production-quality output. The UI will be perceived as trustworthy and professionally crafted.
- **22-26 (73-87%):** Above average but with specific areas where template patterns have crept in. Fix the failing items before shipping.
- **17-21 (57-70%):** Uncanny valley territory. The design has some premium elements but enough violations that it may feel worse than a clean template. Prioritize consistency over polish.
- **Below 17 (<57%):** Fundamental issues. Start with spacing (Q7-9), color (Q19-22), and typography (Q13-16) before addressing anything else.

---

## Appendix A: Quick-Reference Measurements

These specific values are validated across multiple premium platforms and represent safe, tested defaults for Split Lease.

| Property | Value | Validated By |
|---|---|---|
| Base grid unit | 8px | Stripe, Vercel, Material Design, Tailwind |
| Card border-radius | 12px | Airbnb, Stripe, Pitch, Craft |
| Button border-radius | 8px (standard), full-pill for primary hero CTAs | Stripe, Vercel, Untitled UI |
| Badge border-radius | 6px | Stripe, Shopify Polaris |
| Card gap in grid | 24px | Airbnb, Framer, Etsy, Peerspace |
| Section spacing (large) | 48px | Vercel, Stripe, Untitled UI |
| Group spacing (medium) | 24px | Vercel, Stripe, Airbnb |
| Element spacing (small) | 12px | All platforms consistently |
| Body font size | 15-16px | Airbnb (15px), Notion (16px), Medium (21px for reading) |
| Navigation font | 14px/500 weight | Airbnb, Zillow, Sonder, Stripe, Notion |
| Button height (primary) | 48px | Airbnb, Sonder, Blueground, Untitled UI |
| Button height (secondary) | 36-40px | Stripe, Linear, Vercel |
| Input height | 44px | Raycast, Cal.com, Shopify Polaris |
| Icon size (navigation) | 20px | Linear, Shopify |
| Icon size (content) | 24px | Airbnb, Shopify |
| Sidebar width | 320-380px (booking sidebar) | Airbnb, Blueground, Zillow |
| Max content width | 1120-1200px | Airbnb, Vercel, Stripe |
| Max text width (readability) | 640-720px | Plum Guide, Notion, Apple, Medium |
| Transition (hover states) | 150-200ms ease-out | All platforms |
| Transition (layout changes) | 200-300ms ease-out or spring | Linear, Notion, Framer |
| Transition (celebrations) | 300-500ms spring | Superlist, Cal.com |
| Shadow (low/cards) | 0 1px 3px rgba(0,0,0,0.08), 0 1px 2px rgba(0,0,0,0.06) | Pitch, Stripe, Framer |
| Shadow (medium/dropdowns) | 0 4px 16px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04) | Stripe, Airbnb |
| Shadow (high/modals) | 0 12px 40px rgba(0,0,0,0.12), 0 4px 8px rgba(0,0,0,0.06) | Arc, Notion, Sonder |
| Photo aspect ratio (search card) | 20:19 (near-square) or 4:3 | Airbnb (20:19), Hipcamp (4:3) |
| Photo aspect ratio (bento hero) | 1 large (50%) + 4 small (2x2) | Airbnb, Plum Guide |
| Color: max distinct hues | 3 + semantic (green/amber/red) | Sonder (3-4), Notion (3-4), Vercel (6-7 with strict assignment) |
| Color: brand accent pixel coverage | Under 8% of total screen | Airbnb (~8%), Vercel (~5%), Stripe (~3%) |

## Appendix B: Split Lease Design DNA -- What to Preserve

These are the uniquely differentiated elements that define Split Lease and must never be lost in the pursuit of polish:

1. **The Weekly Schedule Selector** (S M T W T F S circles with purple fill on selected days). This is the visual signature of the product's core concept. It must appear on homepage, booking sidebar, proposals, and search filters.

2. **The Proposal-Based Architecture** (propose-negotiate-accept rather than instant-book). The UI must reflect negotiation: editable fields, lifecycle steppers, Accept/Modify/Decline patterns.

3. **The Proposal Lifecycle Stepper** (Submitted > Application > Review > Accepted > Signing > Active). This transforms an opaque process into a visible journey.

4. **Price Formula Transparency** ($X/night x Y nights x Z weeks = Total). The math is visible, not hidden.

5. **AI Integration as Visible Feature** (AI Import Assistant, AI Summary boxes). These are differentiated product features, not hidden backend processes.

6. **Quick-Action Message Pills** ("Say hello," "Ask about availability"). Reduce friction of first contact.

7. **The "Give $50, Get $50" Referral System.** Present but not visually dominant.

8. **Co-Host Scheduling** (meeting calendar with topic selection). A human-support feature that builds trust for a new platform.

9. **Deep Purple Brand Identity** (#2D1B69 or refined variant). The color is the brand, but it must be used with restraint (primary CTAs and header, not everywhere).

10. **Circular Floating Property Images** on the homepage hero. This is a brand-specific creative element, not to be replicated on search or listing pages.

---

*This document should be loaded as context by any AI agent before generating Split Lease UI code. It is a living reference: when a design decision feels uncertain, return to the Perception Stack (Part 1) to understand what the user's brain is evaluating, the Decision Framework (Part 4) for specific guidance, and the Taste Test (Part 6) to validate the output.*
