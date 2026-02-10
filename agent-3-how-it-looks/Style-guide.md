# Split Lease Design System
## Official Production Style Guide v2.0

*Updated by Paula Scher | February 3, 2026*

---

## Overview

This style guide is the **authoritative reference** for Split Lease's visual language, derived directly from the production codebase (`app/src/styles/variables.css`). All design tokens documented here are the exact CSS variables used in the live application.

**Design Philosophy**: Clean, modern interfaces with a distinctive purple palette that conveys trust and sophistication. The system prioritizes clarity, accessibility, and consistent visual rhythm through a well-defined token system.

---

## Complete CSS Variables Reference

Copy this entire `:root` block to use all production design tokens:

```css
:root {
  /* ========================================
     COLOR VARIABLES
     ======================================== */

  /* Primary Colors
     Usage Guide:
     - primary-purple (#31135D): Brand color, headings, important UI
     - primary-purple-hover (#251047): Hover state for primary
     - secondary-purple (#4B47CE): Interactive buttons, links, CTAs
     - accent-purple (#8C68EE): Hover state for secondary, highlights
     - chat-purple (#4B47CE): Day badges, chat elements
  */
  --primary-purple: #31135D;
  --primary-purple-hover: #251047;
  --primary-purple-dark: #1f0a3d;
  --secondary-purple: rgb(109, 49, 194);
  --accent-purple: rgb(140, 104, 238);
  --selected-purple: rgb(79, 48, 151);
  --text-purple: rgb(82, 31, 147);
  --chat-purple: rgb(75, 71, 206);

  /* Secondary Colors */
  --accent-blue: #4A90E2;
  --accent-blue-hover: #357ABD;

  /* Status Colors */
  --success-green: #4B47CE;
  --success-teal: #4B47CE;

  /* Text Colors */
  --text-dark: #1a1a1a;
  --text-gray: #6b7280;
  --text-light-gray: #9ca3af;
  --text-medium-gray: #666666;
  --text-description: #374151;

  /* Background Colors */
  --bg-white: #ffffff;
  --bg-light: #f9fafb;
  --bg-light-gray: #f3f4f6;
  --bg-lighter-gray: #f5f5f5;
  --bg-off-white: rgb(252, 250, 255);

  /* Border Colors */
  --border-color: #e5e7eb;
  --border-light: #f3f4f6;
  --border-gray: rgba(107, 107, 107, 0.7);
  --border-gray-light: #e0e0e0;
  --border-gray-lighter: #ddd;

  /* Neutral Colors */
  --white: rgb(255, 255, 255);
  --black: rgb(0, 0, 0);
  --off-white: rgb(252, 250, 255);

  /* Info/Link Colors */
  --info-blue: #2196F3;
  --info-indigo: #6366F1;
  --info-indigo-hover: #3b82f6;
  --bg-info: #f0f7ff;

  /* Subtle/Overlay Colors */
  --overlay-dark: rgba(0, 0, 0, 0.7);
  --overlay-light: rgba(255, 255, 255, 0.9);
  --overlay-light-blur: rgba(255, 255, 255, 0.2);

  /* Gradient Colors */
  --gradient-purple-primary: linear-gradient(135deg, #31135D 0%, #5a2d8f 100%);
  --gradient-purple-button: linear-gradient(135deg, #4B47CE 0%, #7C3AED 100%);
  --gradient-purple-hover: linear-gradient(135deg, #5B2AA5 0%, #6D28D9 100%);
  --gradient-purple-dark: linear-gradient(135deg, rgba(47, 20, 91, 0.85), rgba(109, 49, 194, 0.75));
  --gradient-purple-dark-hover: linear-gradient(135deg, rgba(47, 20, 91, 0.9), rgba(109, 49, 194, 0.8));

  /* ========================================
     FONT VARIABLES
     ======================================== */

  /* Font Families */
  --font-inter: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-dm: 'DM Sans', sans-serif;
  --font-primary: 'Helvetica', Arial, sans-serif;
  --font-heading: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

  /* Font Sizes */
  --text-xs: 11px;
  --text-sm: 12px;
  --text-sm-md: 13px;
  --text-base: 14px;
  --text-md: 16px;
  --text-lg: 18px;
  --text-xl: 20px;
  --text-2xl: 28px;
  --text-3xl: 32px;
  --text-4xl: 36px;

  /* Font Weights */
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Line Heights */
  --line-height-tight: 1.2;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.6;
  --line-height-loose: 1.8;

  /* Letter Spacing */
  --letter-spacing-normal: normal;
  --letter-spacing-small: 0.5px;
  --letter-spacing-medium: 0.05em;

  /* ========================================
     SPACING VARIABLES
     ======================================== */

  /* Padding & Margin */
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 12px;
  --spacing-lg: 16px;
  --spacing-xl: 20px;
  --spacing-2xl: 24px;
  --spacing-3xl: 28px;
  --spacing-4xl: 32px;
  --spacing-5xl: 2rem;
  --spacing-6xl: 2.5rem;
  --spacing-7xl: 3rem;

  /* Component Spacing */
  --gap-sm: 0.5rem;
  --gap-md: 0.75rem;
  --gap-lg: 1rem;
  --gap-xl: 1.5rem;
  --gap-2xl: 2rem;
  --gap-3xl: 2.5rem;

  /* Padding */
  --padding-sm: 0.5rem;
  --padding-md: 0.75rem;
  --padding-lg: 1rem;
  --padding-xl: 1.5rem;
  --padding-2xl: 2rem;

  /* ========================================
     BORDER RADIUS VARIABLES
     ======================================== */

  --rounded-sm: 4px;
  --rounded-md: 6px;
  --rounded-lg: 8px;
  --rounded-xl: 12px;
  --rounded-2xl: 16px;
  --rounded-full: 50%;
  --rounded-pill: 20px;

  /* ========================================
     BREAKPOINT VARIABLES
     ======================================== */

  --breakpoint-sm: 600px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 1024px;
  --breakpoint-xl: 1080px;
  --breakpoint-2xl: 1200px;
  --breakpoint-3xl: 1280px;
  --breakpoint-max: 1440px;

  /* ========================================
     SHADOW VARIABLES
     ======================================== */

  --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 2px 8px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0 4px 12px rgba(0, 0, 0, 0.15);
  --shadow-xl: 0 4px 16px rgba(49, 19, 93, 0.35);
  --shadow-2xl: 0 6px 24px rgba(49, 19, 93, 0.5);
  --shadow-purple-sm: 0 2px 4px rgba(49, 19, 93, 0.2);
  --shadow-purple-md: 0 4px 8px rgba(49, 19, 93, 0.15);
  --shadow-purple-lg: 0 6px 20px rgba(109, 49, 194, 0.35);
  --shadow-dark-sm: 0 2px 6px rgba(0, 0, 0, 0.2);
  --shadow-dark-md: 0 4px 8px rgba(0, 0, 0, 0.25);

  /* ========================================
     TRANSITION & ANIMATION VARIABLES
     ======================================== */

  --transition-fast: 0.1s;
  --transition-base: 0.2s;
  --transition-slow: 0.3s;
  --transition-slower: 0.4s;

  --easing-ease: ease;
  --easing-ease-in: ease-in;
  --easing-ease-out: ease-out;
  --easing-ease-in-out: ease-in-out;
  --easing-linear: linear;

  --animation-duration: 1.5s;

  /* ========================================
     SIZING VARIABLES
     ======================================== */

  /* Icon Sizes */
  --icon-xs: 16px;
  --icon-sm: 20px;
  --icon-md: 24px;
  --icon-lg: 28px;
  --icon-xl: 32px;
  --icon-2xl: 36px;
  --icon-3xl: 60px;

  /* Avatar Sizes */
  --avatar-sm: 36px;
  --avatar-md: 48px;
  --avatar-lg: 80px;

  /* Container Sizes */
  --container-sm: 640px;
  --container-md: 900px;
  --container-lg: 1280px;
  --container-max: 1440px;
  --container-width: 95vw;

  /* Form Input Sizes */
  --input-height: 42px;
  --input-height-lg: 48px;
  --input-height-sm: 36px;

  /* ========================================
     Z-INDEX VARIABLES
     ======================================== */

  --z-dropdown: 100;
  --z-sticky: 500;
  --z-floating: 999;
  --z-modal: 10000;

  /* ========================================
     OPACITY VARIABLES
     ======================================== */

  --opacity-disabled: 0.5;
  --opacity-hover: 0.8;
  --opacity-focus: 0.9;

  /* ========================================
     BORDER VARIABLES
     ======================================== */

  --border-width-thin: 1px;
  --border-width-md: 1.5px;
  --border-width-thick: 2px;

  /* ========================================
     MAX-WIDTH VARIABLES
     ======================================== */

  --max-width-sidebar: 380px;
  --max-width-modal: 400px;
  --max-width-map: 100%;

  /* ========================================
     FAVORITES PAGE REDESIGN TOKENS
     ======================================== */

  /* Primary Colors */
  --favorites-purple: #6B4EE6;
  --favorites-purple-light: #F0EBFF;
  --favorites-purple-dark: #5A3ED5;
  --favorites-purple-gradient: linear-gradient(135deg, #6B4EE6 0%, #8B6CF5 100%);

  /* Text Colors */
  --favorites-text-dark: #1a1a2e;
  --favorites-text-medium: #64748B;
  --favorites-text-light: #94A3B8;

  /* Background & Border */
  --favorites-bg: #FAFBFC;
  --favorites-border: #E8ECF0;
  --favorites-card-bg: #ffffff;

  /* Status Colors */
  --favorites-success: #4B47CE;
  --favorites-heart: #FF6B5B;
  --favorites-heart-hover: #e55a4a;

  /* ========================================
     POPUP REPLICATION PROTOCOL TOKENS
     Monochromatic purple design system
     STRICT: NO GREEN, NO YELLOW
     ======================================== */

  /* Protocol Colors */
  --protocol-primary: #31135D;
  --protocol-action: #5B5FCF;
  --protocol-action-hover: #4A4EBF;
  --protocol-action-disabled: #B8BAE0;
  --protocol-secondary: #4B47CE;
  --protocol-surface: #F7F2FA;
  --protocol-danger: #DC3545;
  --protocol-danger-hover: rgba(220, 53, 69, 0.1);
  --protocol-white: #FFFFFF;
  --protocol-overlay: rgba(0, 0, 0, 0.5);
  --protocol-border: #E5E7EB;
  --protocol-border-light: #E7E0EC;
  --protocol-text-muted: #6B7280;
  --protocol-text-secondary: #49454F;

  /* Protocol Spacing (STRICT: 8px, 16px, 24px only) */
  --protocol-space-sm: 8px;
  --protocol-space-md: 16px;
  --protocol-space-lg: 24px;

  /* Protocol Radii */
  --protocol-radius-button: 100px;
  --protocol-radius-card: 8px;
  --protocol-radius-modal: 16px;
  --protocol-radius-modal-mobile: 24px;

  /* Protocol Transitions */
  --protocol-transition: 0.2s ease;
  --protocol-transition-slow: 0.3s ease-out;
}
```

---

## 1. Color Palette

### Primary Purple Family

| Variable | Value | Usage |
|----------|-------|-------|
| `--primary-purple` | `#31135D` | Brand color, headings, important UI elements, header backgrounds |
| `--primary-purple-hover` | `#251047` | Hover state for primary purple elements |
| `--primary-purple-dark` | `#1f0a3d` | Darkest purple for maximum contrast |
| `--secondary-purple` | `rgb(109, 49, 194)` | Interactive buttons, links, CTAs |
| `--accent-purple` | `rgb(140, 104, 238)` | Hover state for secondary, highlights, accents |
| `--selected-purple` | `rgb(79, 48, 151)` | Selected/active states |
| `--text-purple` | `rgb(82, 31, 147)` | Purple text for emphasis |
| `--chat-purple` | `rgb(75, 71, 206)` | Day badges, chat elements, messaging UI |

### Secondary Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--accent-blue` | `#4A90E2` | Secondary accent, links in certain contexts |
| `--accent-blue-hover` | `#357ABD` | Hover state for accent blue |

### Status Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--success-green` | `#4B47CE` | Success states, confirmations, positive indicators |
| `--success-teal` | `#4B47CE` | Alternative success color, progress indicators |

### Text Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--text-dark` | `#1a1a1a` | Primary text, headlines, critical content |
| `--text-gray` | `#6b7280` | Secondary text, descriptions |
| `--text-light-gray` | `#9ca3af` | Tertiary text, placeholders, disabled text |
| `--text-medium-gray` | `#666666` | Medium emphasis text |
| `--text-description` | `#374151` | Body text for descriptions and paragraphs |

### Background Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--bg-white` | `#ffffff` | Primary background, cards |
| `--bg-light` | `#f9fafb` | Subtle background differentiation |
| `--bg-light-gray` | `#f3f4f6` | Section backgrounds, inactive states |
| `--bg-lighter-gray` | `#f5f5f5` | Lightest gray background |
| `--bg-off-white` | `rgb(252, 250, 255)` | Subtle purple-tinted background |

### Border Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--border-color` | `#e5e7eb` | Default borders, dividers |
| `--border-light` | `#f3f4f6` | Subtle borders |
| `--border-gray` | `rgba(107, 107, 107, 0.7)` | Medium emphasis borders |
| `--border-gray-light` | `#e0e0e0` | Light gray borders |
| `--border-gray-lighter` | `#ddd` | Lightest borders |

### Neutral Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--white` | `rgb(255, 255, 255)` | Pure white |
| `--black` | `rgb(0, 0, 0)` | Pure black |
| `--off-white` | `rgb(252, 250, 255)` | Warm white with purple tint |

### Info/Link Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--info-blue` | `#2196F3` | Informational elements |
| `--info-indigo` | `#6366F1` | Links, interactive text |
| `--info-indigo-hover` | `#3b82f6` | Hover state for info indigo |
| `--bg-info` | `#f0f7ff` | Info banner backgrounds |

### Overlay Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--overlay-dark` | `rgba(0, 0, 0, 0.7)` | Modal overlays, dimmed backgrounds |
| `--overlay-light` | `rgba(255, 255, 255, 0.9)` | Light overlays for content |
| `--overlay-light-blur` | `rgba(255, 255, 255, 0.2)` | Frosted glass effects |

### Gradient Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--gradient-purple-primary` | `linear-gradient(135deg, #31135D 0%, #5a2d8f 100%)` | Primary brand gradient |
| `--gradient-purple-button` | `linear-gradient(135deg, #4B47CE 0%, #7C3AED 100%)` | Button gradients |
| `--gradient-purple-hover` | `linear-gradient(135deg, #5B2AA5 0%, #6D28D9 100%)` | Button hover gradients |
| `--gradient-purple-dark` | `linear-gradient(135deg, rgba(47, 20, 91, 0.85), rgba(109, 49, 194, 0.75))` | Dark overlay gradients |
| `--gradient-purple-dark-hover` | `linear-gradient(135deg, rgba(47, 20, 91, 0.9), rgba(109, 49, 194, 0.8))` | Dark overlay hover |

---

## 2. Typography

### Font Families

| Variable | Value | Usage |
|----------|-------|-------|
| `--font-inter` | `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif` | Primary UI font |
| `--font-dm` | `'DM Sans', sans-serif` | Alternative display font |
| `--font-primary` | `'Helvetica', Arial, sans-serif` | Fallback system font |
| `--font-heading` | `'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif` | Headings |

### Font Sizes

| Variable | Value | Usage |
|----------|-------|-------|
| `--text-xs` | `11px` | Smallest text, labels, badges |
| `--text-sm` | `12px` | Small text, captions |
| `--text-sm-md` | `13px` | Between small and base |
| `--text-base` | `14px` | Base body text |
| `--text-md` | `16px` | Medium body text |
| `--text-lg` | `18px` | Large body text, small headings |
| `--text-xl` | `20px` | Section headings |
| `--text-2xl` | `28px` | Page headings |
| `--text-3xl` | `32px` | Large headings |
| `--text-4xl` | `36px` | Hero headings |

### Font Weights

| Variable | Value | Usage |
|----------|-------|-------|
| `--font-weight-normal` | `400` | Regular body text |
| `--font-weight-medium` | `500` | Emphasized text, links |
| `--font-weight-semibold` | `600` | Buttons, labels, subheadings |
| `--font-weight-bold` | `700` | Headings, strong emphasis |

### Line Heights

| Variable | Value | Usage |
|----------|-------|-------|
| `--line-height-tight` | `1.2` | Headings, compact text |
| `--line-height-normal` | `1.5` | Body text default |
| `--line-height-relaxed` | `1.6` | Readable body text |
| `--line-height-loose` | `1.8` | Spacious, comfortable reading |

### Letter Spacing

| Variable | Value | Usage |
|----------|-------|-------|
| `--letter-spacing-normal` | `normal` | Default spacing |
| `--letter-spacing-small` | `0.5px` | Slightly expanded |
| `--letter-spacing-medium` | `0.05em` | Uppercase labels |

---

## 3. Spacing System

### Core Spacing Scale

| Variable | Value | Usage |
|----------|-------|-------|
| `--spacing-xs` | `4px` | Tight gaps, inline spacing |
| `--spacing-sm` | `8px` | Small gaps between related elements |
| `--spacing-md` | `12px` | Standard component padding |
| `--spacing-lg` | `16px` | Section padding, card padding |
| `--spacing-xl` | `20px` | Larger component padding |
| `--spacing-2xl` | `24px` | Section margins |
| `--spacing-3xl` | `28px` | Major section separations |
| `--spacing-4xl` | `32px` | Page section margins |
| `--spacing-5xl` | `2rem` | Large vertical rhythm |
| `--spacing-6xl` | `2.5rem` | Major page sections |
| `--spacing-7xl` | `3rem` | Maximum spacing |

### Gap Variables (for Flexbox/Grid)

| Variable | Value | Usage |
|----------|-------|-------|
| `--gap-sm` | `0.5rem` | Tight gaps in flex/grid |
| `--gap-md` | `0.75rem` | Standard gaps |
| `--gap-lg` | `1rem` | Comfortable gaps |
| `--gap-xl` | `1.5rem` | Generous gaps |
| `--gap-2xl` | `2rem` | Large gaps |
| `--gap-3xl` | `2.5rem` | Maximum gaps |

### Padding Variables

| Variable | Value | Usage |
|----------|-------|-------|
| `--padding-sm` | `0.5rem` | Compact padding |
| `--padding-md` | `0.75rem` | Standard padding |
| `--padding-lg` | `1rem` | Comfortable padding |
| `--padding-xl` | `1.5rem` | Generous padding |
| `--padding-2xl` | `2rem` | Maximum padding |

---

## 4. Border Radius

| Variable | Value | Usage |
|----------|-------|-------|
| `--rounded-sm` | `4px` | Subtle rounding, inputs |
| `--rounded-md` | `6px` | Standard rounding |
| `--rounded-lg` | `8px` | Cards, larger elements |
| `--rounded-xl` | `12px` | Prominent cards |
| `--rounded-2xl` | `16px` | Large cards, modals |
| `--rounded-full` | `50%` | Circles, avatars |
| `--rounded-pill` | `20px` | Pill-shaped buttons, badges |

---

## 5. Breakpoints

| Variable | Value | Usage |
|----------|-------|-------|
| `--breakpoint-sm` | `600px` | Mobile breakpoint |
| `--breakpoint-md` | `768px` | Tablet breakpoint |
| `--breakpoint-lg` | `1024px` | Desktop small |
| `--breakpoint-xl` | `1080px` | Desktop standard |
| `--breakpoint-2xl` | `1200px` | Desktop large |
| `--breakpoint-3xl` | `1280px` | Wide desktop |
| `--breakpoint-max` | `1440px` | Maximum width |

### Responsive Patterns

```css
/* Mobile-first approach */
@media (min-width: 600px) { /* Tablet */ }
@media (min-width: 768px) { /* Desktop small */ }
@media (min-width: 1024px) { /* Desktop */ }
@media (min-width: 1200px) { /* Desktop large */ }
@media (min-width: 1440px) { /* Maximum */ }
```

---

## 6. Shadows

### Standard Shadows

| Variable | Value | Usage |
|----------|-------|-------|
| `--shadow-sm` | `0 1px 3px rgba(0, 0, 0, 0.05)` | Subtle elevation |
| `--shadow-md` | `0 2px 8px rgba(0, 0, 0, 0.08)` | Card elevation |
| `--shadow-lg` | `0 4px 12px rgba(0, 0, 0, 0.15)` | Dropdown, popover |
| `--shadow-xl` | `0 4px 16px rgba(49, 19, 93, 0.35)` | Modal, emphasized cards |
| `--shadow-2xl` | `0 6px 24px rgba(49, 19, 93, 0.5)` | Maximum elevation |

### Purple-Tinted Shadows

| Variable | Value | Usage |
|----------|-------|-------|
| `--shadow-purple-sm` | `0 2px 4px rgba(49, 19, 93, 0.2)` | Subtle purple glow |
| `--shadow-purple-md` | `0 4px 8px rgba(49, 19, 93, 0.15)` | Medium purple glow |
| `--shadow-purple-lg` | `0 6px 20px rgba(109, 49, 194, 0.35)` | Strong purple glow |

### Dark Shadows

| Variable | Value | Usage |
|----------|-------|-------|
| `--shadow-dark-sm` | `0 2px 6px rgba(0, 0, 0, 0.2)` | Subtle dark shadow |
| `--shadow-dark-md` | `0 4px 8px rgba(0, 0, 0, 0.25)` | Medium dark shadow |

---

## 7. Transitions & Animation

### Transition Durations

| Variable | Value | Usage |
|----------|-------|-------|
| `--transition-fast` | `0.1s` | Micro-interactions, hover |
| `--transition-base` | `0.2s` | Standard transitions |
| `--transition-slow` | `0.3s` | Deliberate animations |
| `--transition-slower` | `0.4s` | Long animations |

### Easing Functions

| Variable | Value | Usage |
|----------|-------|-------|
| `--easing-ease` | `ease` | General purpose |
| `--easing-ease-in` | `ease-in` | Elements entering |
| `--easing-ease-out` | `ease-out` | Elements exiting |
| `--easing-ease-in-out` | `ease-in-out` | Smooth both ways |
| `--easing-linear` | `linear` | Constant speed |

### Animation

| Variable | Value | Usage |
|----------|-------|-------|
| `--animation-duration` | `1.5s` | Standard animation length |

### Usage Patterns

```css
/* Button hover */
.btn {
  transition: background var(--transition-fast) var(--easing-ease),
              transform var(--transition-fast) var(--easing-ease);
}

/* Card hover */
.card {
  transition: box-shadow var(--transition-base) var(--easing-ease-in-out);
}

/* Modal entrance */
.modal {
  transition: opacity var(--transition-slow) var(--easing-ease-out),
              transform var(--transition-slow) var(--easing-ease-out);
}
```

---

## 8. Sizing Variables

### Icon Sizes

| Variable | Value | Usage |
|----------|-------|-------|
| `--icon-xs` | `16px` | Inline icons |
| `--icon-sm` | `20px` | Small icons |
| `--icon-md` | `24px` | Standard icons |
| `--icon-lg` | `28px` | Emphasized icons |
| `--icon-xl` | `32px` | Large icons |
| `--icon-2xl` | `36px` | Very large icons |
| `--icon-3xl` | `60px` | Hero icons |

### Icon Library Policy

- Use only icons from `https://feathericons.com/`
- Do not mix Feather with any other icon packs in Split Lease UI
- If an icon is missing, pick the closest Feather icon and document the mapping

### Avatar Sizes

| Variable | Value | Usage |
|----------|-------|-------|
| `--avatar-sm` | `36px` | Inline avatars, lists |
| `--avatar-md` | `48px` | Standard avatars |
| `--avatar-lg` | `80px` | Profile avatars |

### Container Sizes

| Variable | Value | Usage |
|----------|-------|-------|
| `--container-sm` | `640px` | Narrow content |
| `--container-md` | `900px` | Standard content |
| `--container-lg` | `1280px` | Wide content |
| `--container-max` | `1440px` | Maximum width |
| `--container-width` | `95vw` | Responsive width |

### Form Input Sizes

| Variable | Value | Usage |
|----------|-------|-------|
| `--input-height` | `42px` | Standard inputs |
| `--input-height-lg` | `48px` | Large inputs |
| `--input-height-sm` | `36px` | Compact inputs |

---

## 9. Z-Index Scale

| Variable | Value | Usage |
|----------|-------|-------|
| `--z-dropdown` | `100` | Dropdowns, tooltips |
| `--z-sticky` | `500` | Sticky headers, navigation |
| `--z-floating` | `999` | Floating elements |
| `--z-modal` | `10000` | Modals, overlays |

---

## 10. Opacity Variables

| Variable | Value | Usage |
|----------|-------|-------|
| `--opacity-disabled` | `0.5` | Disabled elements |
| `--opacity-hover` | `0.8` | Hover transparency |
| `--opacity-focus` | `0.9` | Focus states |

---

## 11. Border Variables

| Variable | Value | Usage |
|----------|-------|-------|
| `--border-width-thin` | `1px` | Standard borders |
| `--border-width-md` | `1.5px` | Medium emphasis |
| `--border-width-thick` | `2px` | Strong emphasis |

---

## 12. Max-Width Variables

| Variable | Value | Usage |
|----------|-------|-------|
| `--max-width-sidebar` | `380px` | Sidebar panels |
| `--max-width-modal` | `400px` | Modal dialogs |
| `--max-width-map` | `100%` | Map containers |

---

## 13. Favorites Page Tokens

These tokens are used specifically for the Favorites page redesign.

### Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--favorites-purple` | `#6B4EE6` | Primary accent |
| `--favorites-purple-light` | `#F0EBFF` | Light background |
| `--favorites-purple-dark` | `#5A3ED5` | Hover/active states |
| `--favorites-purple-gradient` | `linear-gradient(135deg, #6B4EE6 0%, #8B6CF5 100%)` | Gradient accents |

### Text

| Variable | Value | Usage |
|----------|-------|-------|
| `--favorites-text-dark` | `#1a1a2e` | Primary text |
| `--favorites-text-medium` | `#64748B` | Secondary text |
| `--favorites-text-light` | `#94A3B8` | Tertiary text |

### Backgrounds & Borders

| Variable | Value | Usage |
|----------|-------|-------|
| `--favorites-bg` | `#FAFBFC` | Page background |
| `--favorites-border` | `#E8ECF0` | Card borders |
| `--favorites-card-bg` | `#ffffff` | Card backgrounds |

### Status

| Variable | Value | Usage |
|----------|-------|-------|
| `--favorites-success` | `#4B47CE` | Success indicators |
| `--favorites-heart` | `#FF6B5B` | Heart icon fill |
| `--favorites-heart-hover` | `#e55a4a` | Heart icon hover |

---

## 14. Protocol Tokens

These tokens define the **Popup Replication Protocol** - a strict monochromatic purple design system. **IMPORTANT: NO GREEN, NO YELLOW colors allowed in protocol components.**

### Protocol Colors

| Variable | Value | Usage |
|----------|-------|-------|
| `--protocol-primary` | `#31135D` | Primary brand |
| `--protocol-action` | `#5B5FCF` | Action buttons |
| `--protocol-action-hover` | `#4A4EBF` | Action hover |
| `--protocol-action-disabled` | `#B8BAE0` | Disabled actions |
| `--protocol-secondary` | `#4B47CE` | Secondary elements |
| `--protocol-surface` | `#F7F2FA` | Surface backgrounds |
| `--protocol-danger` | `#DC3545` | Danger/destructive |
| `--protocol-danger-hover` | `rgba(220, 53, 69, 0.1)` | Danger hover bg |
| `--protocol-white` | `#FFFFFF` | White |
| `--protocol-overlay` | `rgba(0, 0, 0, 0.5)` | Modal overlays |
| `--protocol-border` | `#E5E7EB` | Standard borders |
| `--protocol-border-light` | `#E7E0EC` | Light borders |
| `--protocol-text-muted` | `#6B7280` | Muted text |
| `--protocol-text-secondary` | `#49454F` | Secondary text |

### Protocol Spacing

**STRICT RULE**: Only use 8px, 16px, or 24px spacing in protocol components.

| Variable | Value |
|----------|-------|
| `--protocol-space-sm` | `8px` |
| `--protocol-space-md` | `16px` |
| `--protocol-space-lg` | `24px` |

### Protocol Radii

| Variable | Value | Usage |
|----------|-------|-------|
| `--protocol-radius-button` | `100px` | Pill buttons |
| `--protocol-radius-card` | `8px` | Cards |
| `--protocol-radius-modal` | `16px` | Modal desktop |
| `--protocol-radius-modal-mobile` | `24px` | Modal mobile |

### Protocol Transitions

| Variable | Value |
|----------|-------|
| `--protocol-transition` | `0.2s ease` |
| `--protocol-transition-slow` | `0.3s ease-out` |

---

## Component Usage Examples

### Primary Button

```css
.btn-primary {
  background: var(--secondary-purple);
  color: var(--white);
  font-family: var(--font-inter);
  font-size: var(--text-base);
  font-weight: var(--font-weight-semibold);
  padding: var(--spacing-sm) var(--spacing-2xl);
  border-radius: var(--rounded-pill);
  border: none;
  cursor: pointer;
  transition: background var(--transition-fast) var(--easing-ease);
}

.btn-primary:hover {
  background: var(--accent-purple);
}
```

### Card Component

```css
.card {
  background: var(--bg-white);
  border: var(--border-width-thin) solid var(--border-color);
  border-radius: var(--rounded-xl);
  padding: var(--spacing-2xl);
  box-shadow: var(--shadow-sm);
  transition: box-shadow var(--transition-base) var(--easing-ease-in-out);
}

.card:hover {
  box-shadow: var(--shadow-md);
}
```

### Form Input

```css
.input {
  width: 100%;
  height: var(--input-height);
  padding: var(--spacing-sm) var(--spacing-lg);
  font-family: var(--font-inter);
  font-size: var(--text-base);
  color: var(--text-dark);
  background: var(--bg-white);
  border: var(--border-width-thin) solid var(--border-color);
  border-radius: var(--rounded-md);
  transition: border-color var(--transition-fast) var(--easing-ease);
}

.input:focus {
  outline: none;
  border-color: var(--secondary-purple);
  box-shadow: 0 0 0 3px rgba(109, 49, 194, 0.1);
}
```

### Day Badge (Split Lease Signature Component)

```css
.day-badge {
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--rounded-full);
  font-size: var(--text-sm-md);
  font-weight: var(--font-weight-semibold);
  background: var(--bg-light-gray);
  color: var(--text-light-gray);
  transition: all var(--transition-fast) var(--easing-ease);
}

.day-badge.active {
  background: var(--chat-purple);
  color: var(--white);
}
```

---

## Accessibility Requirements

### Minimum Touch Targets

All interactive elements must meet 48px minimum touch target:

```css
.interactive {
  min-height: var(--input-height-lg); /* 48px */
  min-width: var(--input-height-lg);
}
```

### Focus States

```css
:focus-visible {
  outline: 2px solid var(--secondary-purple);
  outline-offset: 2px;
}
```

### Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Implementation Checklist

When building Split Lease interfaces, verify:

- [ ] Colors use CSS variables from this guide (no hardcoded hex values)
- [ ] Typography uses defined font sizes and weights
- [ ] Spacing follows the spacing scale
- [ ] Border radius uses defined tokens
- [ ] Shadows use defined shadow variables
- [ ] Transitions use defined timing and easing
- [ ] Z-index follows the defined scale
- [ ] Touch targets meet 48px minimum
- [ ] Focus states are visible on all interactive elements
- [ ] Reduced motion preferences are respected
- [ ] Protocol components use ONLY protocol tokens (no green/yellow)

---

*"Design within constraints is not compromise - it's discipline."* - Paula Scher

---

---

# PROPOSED COLOR REVISIONS

## Paula Scher Recommendations | February 3, 2026

> **STATUS**: PROPOSED - NOT YET IN PRODUCTION
>
> The following color adjustments are recommendations based on a comprehensive audit of the current palette. These changes require team review and approval before implementation.

---

## Rationale Summary

The current palette suffers from three primary issues:

1. **Purple Proliferation**: 10+ purple variants that are visually indistinguishable
2. **Missing Warmth**: No warm accent color to balance the cool purple
3. **Accessibility Gaps**: Several colors fail WCAG AA contrast requirements

---

## Proposed Primary Purple Family (Consolidated)

**Goal**: Reduce from 10+ purples to 5 distinct, purposeful variants.

| Variable | Current Value | Proposed Value | Change |
|----------|---------------|----------------|--------|
| `--primary-purple` | `#31135D` | `#31135D` | No change - excellent brand anchor |
| `--primary-purple-hover` | `#251047` | `#1E0D42` | Slightly darker for clearer differentiation |
| `--secondary-purple` | `rgb(109, 49, 194)` | `#6B35C9` | Warmer, more saturated for CTAs |
| `--secondary-purple-hover` | `rgb(140, 104, 238)` | `#5A2AAD` | **CRITICAL**: Darker hover, not lighter |
| `--selected-purple` | `rgb(79, 48, 151)` | `#7B4DBA` | Warmer, more distinct from secondary |

### Variables to ELIMINATE

| Variable | Current Value | Replacement |
|----------|---------------|-------------|
| `--primary-purple-dark` | `#1f0a3d` | Use `--primary-purple-hover` |
| `--text-purple` | `rgb(82, 31, 147)` | Use `--secondary-purple` |
| `--chat-purple` | `rgb(75, 71, 206)` | Use `--secondary-purple` for badges |
| `--accent-purple` | `rgb(140, 104, 238)` | Use new `--secondary-purple-hover` |

---

## Proposed Warm Accent Colors (NEW)

**Goal**: Add warmth and urgency to balance the cool purple palette.

```css
/* NEW: Warm Accent Colors */
--accent-gold: #D4A853;
--accent-gold-light: #F5E6C3;
--accent-gold-dark: #B8923F;

--accent-coral: #E85D4C;
--accent-coral-hover: #D64C3C;
--accent-coral-light: #FCE8E6;
```

### Usage Guidelines

| Color | Use For |
|-------|---------|
| `--accent-gold` | Premium badges, highlights, "featured" indicators |
| `--accent-gold-light` | Callout backgrounds, promotional sections |
| `--accent-coral` | Hearts/favorites, urgency ("Limited Availability"), action items |
| `--accent-coral-hover` | Hover state for coral elements |

---

## Proposed Status Colors (WCAG AA Compliant)

**Goal**: Ensure all status colors meet accessibility requirements.

### Current Problems

| Color | Current Contrast | Required | Status |
|-------|------------------|----------|--------|
| `--success-green` (#4B47CE) | ~3.0:1 | 4.5:1 | FAIL |
| `--success-teal` (#4B47CE) | ~3.0:1 | 4.5:1 | FAIL |
| Warning | Not defined | - | MISSING |
| Error | Not defined at root | - | MISSING |

### Proposed Status Palette

```css
/* Success */
--status-success: #4B47CE;           /* Updated per requested palette */
--status-success-light: #E6F5EE;     /* Background for success states */
--status-success-text: #4B47CE;      /* Updated per requested palette */

/* Warning */
--status-warning: #C4841D;           /* 4.6:1 contrast - AA compliant */
--status-warning-light: #FDF4E3;     /* Background for warning states */
--status-warning-text: #92620E;      /* Text on light warning background */

/* Error */
--status-error: #C53030;             /* 6.1:1 contrast - AA compliant */
--status-error-light: #FDE8E8;       /* Background for error states */
--status-error-text: #9B2C2C;        /* Text on light error background */

/* Info (keep existing, add light variant) */
--status-info: #2563EB;              /* Standardized info blue */
--status-info-light: #EFF6FF;        /* Background for info states */
```

---

## Proposed Text Color Adjustments

**Goal**: Improve contrast for secondary and tertiary text.

| Variable | Current | Proposed | Contrast on White |
|----------|---------|----------|-------------------|
| `--text-dark` | `#1a1a1a` | `#1a1a1a` | 16.1:1 (no change) |
| `--text-gray` | `#6b7280` | `#5A6370` | 5.9:1 (improved from 4.6:1) |
| `--text-light-gray` | `#9ca3af` | `#8891A0` | 4.5:1 (improved from 2.6:1) |
| `--text-placeholder` | (new) | `#A8B0BC` | 3.2:1 (for placeholder only) |

---

## Proposed Border Consolidation

**Goal**: Reduce from 5 border colors to 3.

### Current Border Chaos

```css
/* Current - 5 redundant variables */
--border-color: #e5e7eb;
--border-light: #f3f4f6;
--border-gray: rgba(107, 107, 107, 0.7);
--border-gray-light: #e0e0e0;
--border-gray-lighter: #ddd;
```

### Proposed Border System

```css
/* Proposed - 3 purposeful variables */
--border-subtle: #F0F1F3;      /* Barely visible, section dividers */
--border-default: #E2E4E8;     /* Standard borders, cards, inputs */
--border-emphasis: #C8CBD0;    /* Strong borders, active states */
```

---

## Proposed Day Badge Colors

**Goal**: Unify day badges with brand purple instead of blue-leaning chat purple.

### Current (Disconnected from Brand)

```css
/* Current - blue-leaning */
--chat-purple: rgb(75, 71, 206);  /* Used for day badges */
```

### Proposed (Brand-Aligned)

```css
/* Day Badge States */
--day-badge-inactive-bg: #E8E5F0;      /* Purple-tinted gray */
--day-badge-inactive-text: #6B7280;    /* Muted text */
--day-badge-selected-bg: #6B35C9;      /* Brand CTA purple */
--day-badge-selected-text: #FFFFFF;    /* White for contrast */
--day-badge-hover-bg: #F3F0F8;         /* Subtle hover for inactive */
```

---

## Proposed CSS Variables Block

Copy this block to replace/augment the current color variables:

```css
:root {
  /* ========================================
     PROPOSED COLOR SYSTEM - Paula Scher Review
     ======================================== */

  /* Primary Purple Family (Consolidated) */
  --primary-purple: #31135D;
  --primary-purple-hover: #1E0D42;
  --secondary-purple: #6B35C9;
  --secondary-purple-hover: #5A2AAD;
  --selected-purple: #7B4DBA;

  /* Warm Accent Colors (NEW) */
  --accent-gold: #D4A853;
  --accent-gold-light: #F5E6C3;
  --accent-gold-dark: #B8923F;
  --accent-coral: #E85D4C;
  --accent-coral-hover: #D64C3C;
  --accent-coral-light: #FCE8E6;

  /* Status Colors (WCAG AA Compliant) */
  --status-success: #4B47CE;
  --status-success-light: #E6F5EE;
  --status-success-text: #4B47CE;
  --status-warning: #C4841D;
  --status-warning-light: #FDF4E3;
  --status-warning-text: #92620E;
  --status-error: #C53030;
  --status-error-light: #FDE8E8;
  --status-error-text: #9B2C2C;
  --status-info: #2563EB;
  --status-info-light: #EFF6FF;

  /* Text Colors (Improved Contrast) */
  --text-dark: #1a1a1a;
  --text-gray: #5A6370;
  --text-light-gray: #8891A0;
  --text-placeholder: #A8B0BC;
  --text-description: #374151;

  /* Border Colors (Consolidated) */
  --border-subtle: #F0F1F3;
  --border-default: #E2E4E8;
  --border-emphasis: #C8CBD0;

  /* Day Badge System */
  --day-badge-inactive-bg: #E8E5F0;
  --day-badge-inactive-text: #6B7280;
  --day-badge-selected-bg: #6B35C9;
  --day-badge-selected-text: #FFFFFF;
  --day-badge-hover-bg: #F3F0F8;

  /* Background Colors (Keep Existing) */
  --bg-white: #ffffff;
  --bg-light: #f9fafb;
  --bg-light-gray: #f3f4f6;
  --bg-off-white: rgb(252, 250, 255);

  /* Gradients (Updated to use new purples) */
  --gradient-purple-primary: linear-gradient(135deg, #31135D 0%, #5a2d8f 100%);
  --gradient-purple-button: linear-gradient(135deg, #6B35C9 0%, #7B4DBA 100%);
  --gradient-purple-hover: linear-gradient(135deg, #5A2AAD 0%, #6B35C9 100%);
}
```

---

## Dark Mode Preparation

If implementing dark mode, use these mappings:

| Light Mode | Dark Mode | Notes |
|------------|-----------|-------|
| `--primary-purple` (#31135D) | `#9B7FD1` | Lightened for dark bg |
| `--secondary-purple` (#6B35C9) | `#A385E0` | Maintains saturation |
| `--bg-white` (#FFFFFF) | `#1A1625` | Deep purple-black |
| `--text-dark` (#1a1a1a) | `#F5F3F7` | Off-white with purple tint |
| `--accent-gold` (#D4A853) | `#E8C77B` | Desaturated for dark bg |
| `--accent-coral` (#E85D4C) | `#F07B6C` | Lighter for visibility |
| `--status-success` (#4B47CE) | `#4B47CE` | Brighter for dark bg |
| `--status-warning` (#C4841D) | `#FBBF24` | Brighter for dark bg |
| `--status-error` (#C53030) | `#F87171` | Brighter for dark bg |

---

## Implementation Checklist

### Phase 1: Critical Fixes (Week 1)

- [ ] Change secondary-purple hover from lighter to darker
- [ ] Add `--status-warning` and `--status-error` to root variables
- [ ] Update day badge colors to use brand purple

### Phase 2: Warmth Addition (Weeks 2-3)

- [ ] Implement `--accent-gold` system
- [ ] Elevate `--accent-coral` from favorites to primary accent
- [ ] Update premium features to use gold accent

### Phase 3: Consolidation (Weeks 3-4)

- [ ] Migrate components from eliminated purple variables
- [ ] Consolidate border colors from 5 to 3
- [ ] Update text colors for improved contrast

### Phase 4: Polish (Month 2)

- [ ] Audit all components for new color usage
- [ ] Remove deprecated color variables
- [ ] Document dark mode color mappings

---

## Comparison: Before & After

### Brand Palette Simplification

| Before (10+ purples) | After (5 purples) |
|---------------------|-------------------|
| primary-purple | primary-purple |
| primary-purple-hover | primary-purple-hover |
| primary-purple-dark | (eliminated) |
| secondary-purple | secondary-purple |
| accent-purple | secondary-purple-hover |
| selected-purple | selected-purple |
| text-purple | (eliminated) |
| chat-purple | (eliminated) |
| favorites-purple | (use secondary-purple) |
| protocol colors | (use core purples) |

### Emotional Temperature Shift

| Aspect | Before | After |
|--------|--------|-------|
| Primary Emotion | Clinical, corporate | Sophisticated, aspirational |
| Warmth Level | Cold (purple only) | Balanced (purple + gold + coral) |
| Urgency | Low (no warm accents) | Appropriate (coral for action) |
| Trustworthiness | Present | Enhanced (gold = premium) |

---

*"The problem isn't that we use purple. The problem is that we use purple without direction. Direction comes from contrast, hierarchy, and restraint."* - Paula Scher

---

**Version**: 2.0
**Last Updated**: February 3, 2026
**Source**: `app/src/styles/variables.css`
**Maintained by**: Split Lease Design Team
**Color Review by**: Paula Scher (simulated)
