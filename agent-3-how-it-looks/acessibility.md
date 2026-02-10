# Accessibility Guidelines for Split Lease

Guidelines for creating elderly-friendly, WCAG-compliant interfaces based on the Guest Proposals mockup patterns.

---

## 1. Typography

### Font Sizes (Minimum Requirements)

| Element | Size | Purpose |
|---------|------|---------|
| Body text | **17px** | Comfortable reading for elderly users |
| Small text | **15px** | Meta info, secondary content |
| Labels | **14px** | Form labels, uppercase section headers |
| Medium text | **18px** | Emphasized body content |
| Large headings | **22px** | Section titles |
| XL headings | **28px** | Page titles |
| 2XL numbers | **36px** | Prominent values (prices, totals) |

### Line Heights

```css
--line-height-tight: 1.3;    /* Headings */
--line-height-normal: 1.6;   /* Body text */
--line-height-relaxed: 1.8;  /* Long paragraphs, descriptions */
```

### Font Weight

- **400** — Regular body text
- **500** — Medium emphasis
- **600** — Semi-bold for labels, buttons, meta
- **700** — Bold for headings, important values

---

## 2. Color & Contrast

### Text Contrast (WCAG AAA)

| Use Case | Color | Hex |
|----------|-------|-----|
| Primary text | Near black | `#111111` |
| Secondary text | Dark gray | `#374151` |
| Muted text | Medium gray | `#4b5563` |

> **Rule**: All text must have a contrast ratio of at least **4.5:1** against its background. Large text (18px+ or 14px+ bold) requires **3:1** minimum.

### Semantic Colors

| Status | Text Color | Background |
|--------|------------|------------|
| Success | `#047857` | `#d1fae5` |
| Warning | `#b45309` | `#fef3c7` |
| Danger | `#b91c1c` | `#fee2e2` |
| Primary | `#6D31C2` | `#f8f5ff` |

> **Rule**: Never rely on color alone to convey meaning. Always pair with text, icons, or patterns.

---

## 3. Touch Targets

### Minimum Sizes

```css
--min-touch-target: 48px;
```

| Element | Minimum Size |
|---------|--------------|
| Buttons | 48px height, 120px min-width |
| Links in navigation | 48px height |
| Interactive rows | 88px height |
| Day pills / toggles | 52×52px |
| Icon buttons | 48×48px |

### Spacing Between Targets

- Minimum **8px** gap between adjacent touch targets
- Recommended **12-16px** for comfortable use

---

## 4. Focus States

### Visible Focus Indicators

```css
:focus-visible {
    outline: 3px solid var(--color-primary);
    outline-offset: 3px;
}
```

### Focus Ring for Interactive Elements

```css
--focus-ring: 0 0 0 4px rgba(109, 49, 194, 0.5);
```

> **Rules**:
> - Focus indicators must be **clearly visible** (3px minimum width)
> - Use `outline-offset` to prevent overlap with element borders
> - Never remove focus styles without providing an alternative

---

## 5. Keyboard Navigation

### Required Behaviors

| Element | Keyboard Support |
|---------|------------------|
| Buttons | `Enter` or `Space` to activate |
| Links | `Enter` to follow |
| Selectable rows | `Enter` to select, arrow keys to navigate |
| Toggle buttons | `Space` to toggle |
| Modals | `Escape` to close, trap focus inside |

### Tab Order

- Logical left-to-right, top-to-bottom flow
- Use `tabindex="0"` for custom interactive elements
- Never use `tabindex` values greater than 0

### Skip Links

```html
<a href="#main-content" class="skip-link">Skip to main content</a>
```

```css
.skip-link {
    position: absolute;
    top: -100%;
    left: 16px;
    padding: 16px 24px;
    background: var(--color-primary);
    color: white;
    font-weight: 600;
    border-radius: 12px;
    z-index: 1000;
}

.skip-link:focus {
    top: 16px;
}
```

---

## 6. Screen Reader Support

### ARIA Landmarks

```html
<header role="banner">...</header>
<main role="main">...</main>
<nav role="navigation" aria-label="Primary">...</nav>
<footer role="contentinfo">...</footer>
```

### Screen Reader Only Text

```css
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
```

### Descriptive Labels

```html
<!-- Hidden heading for screen readers -->
<h2 id="proposals-heading" class="sr-only">Your submitted proposals</h2>

<!-- Described by for additional context -->
<div aria-describedby="proposal-1-status">...</div>
<span id="proposal-1-status">Accepted</span>

<!-- Label for icon-only elements -->
<button aria-label="Close modal">×</button>
```

### Live Regions

```html
<!-- Status updates that should be announced -->
<div role="status" aria-live="polite">
    Proposal Accepted — Lease documents are being prepared
</div>

<!-- Urgent alerts -->
<div role="alert">
    Counteroffer received — Host proposed different terms
</div>
```

---

## 7. Semantic HTML

### Use Correct Elements

| Purpose | Element |
|---------|---------|
| Page title | `<h1>` (one per page) |
| Section headings | `<h2>`, `<h3>`, etc. (in order) |
| Navigation | `<nav>` |
| Lists | `<ul>`, `<ol>`, `<dl>` |
| Buttons | `<button type="button">` |
| Links | `<a href="...">` |
| Images | `<img alt="...">` |
| Time/dates | `<time datetime="...">` |

### Definition Lists for Data

```html
<dl class="info-grid">
    <div class="info-grid__item">
        <dt class="info-grid__label">Duration</dt>
        <dd class="info-grid__value">12 weeks</dd>
    </div>
</dl>
```

### Decorative vs Meaningful Images

```html
<!-- Decorative: hide from screen readers -->
<img src="..." alt="" aria-hidden="true">

<!-- Meaningful: provide description -->
<img src="..." alt="Interior photo of Modern Chelsea Studio">
```

---

## 8. Forms & Inputs

### Labels

```html
<!-- Always associate labels with inputs -->
<label for="email">Email address</label>
<input type="email" id="email" name="email">

<!-- Or wrap the input -->
<label>
    Email address
    <input type="email" name="email">
</label>
```

### Error Messages

```html
<input
    type="email"
    aria-invalid="true"
    aria-describedby="email-error"
>
<span id="email-error" role="alert">
    Please enter a valid email address
</span>
```

### Required Fields

```html
<label for="name">
    Name <span aria-hidden="true">*</span>
    <span class="sr-only">(required)</span>
</label>
<input type="text" id="name" required aria-required="true">
```

---

## 9. Motion & Animation

### Respect User Preferences

```css
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }

    html {
        scroll-behavior: auto;
    }
}
```

### Animation Guidelines

- Keep transitions short: **150-250ms**
- Avoid flashing or strobing effects
- No auto-playing animations that can't be paused
- Provide controls for any animated content

---

## 10. High Contrast Mode

```css
@media (prefers-contrast: high) {
    :root {
        --color-border: #000;
        --color-text-muted: #374151;
    }

    .btn {
        border-width: 3px;
    }

    .card {
        border-width: 3px;
    }
}
```

---

## 11. Responsive Considerations

### Mobile Accessibility

- Touch targets remain 48px minimum on mobile
- Font sizes don't go below 16px on mobile
- Ensure sufficient spacing for finger taps
- Test with screen magnification (up to 200%)

### Viewport Meta

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

> **Never** use `maximum-scale=1.0` or `user-scalable=no` — users must be able to zoom.

---

## 12. Testing Checklist

### Automated Testing

- [ ] Run axe-core or Lighthouse accessibility audit
- [ ] Validate HTML (no duplicate IDs, proper nesting)
- [ ] Check color contrast with WebAIM contrast checker

### Manual Testing

- [ ] Navigate entire page using only keyboard
- [ ] Test with screen reader (VoiceOver, NVDA, JAWS)
- [ ] Test at 200% zoom
- [ ] Test with high contrast mode enabled
- [ ] Test with reduced motion preference

### User Testing

- [ ] Test with users aged 60+
- [ ] Test with users who have low vision
- [ ] Test with users who rely on keyboard navigation

---

## Quick Reference: CSS Custom Properties

```css
:root {
    /* Typography */
    --font-size-sm: 15px;
    --font-size-base: 17px;
    --font-size-md: 18px;
    --font-size-lg: 22px;
    --font-size-xl: 28px;
    --font-size-2xl: 36px;
    --font-size-label: 14px;

    /* Line Heights */
    --line-height-tight: 1.3;
    --line-height-normal: 1.6;
    --line-height-relaxed: 1.8;

    /* Touch Targets */
    --min-touch-target: 48px;

    /* Text Colors (High Contrast) */
    --color-text: #111111;
    --color-text-secondary: #374151;
    --color-text-muted: #4b5563;

    /* Focus */
    --focus-ring: 0 0 0 4px rgba(109, 49, 194, 0.5);

    /* Transitions */
    --transition-fast: 150ms ease;
    --transition-normal: 200ms ease;
}
```
