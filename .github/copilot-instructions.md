# Solodex - AI Coding Instructions

## Project Overview

Solodex is a minimal, visually-driven contact card display system with a retro aesthetic. It features an interactive 3D card flip mechanism styled to resemble vintage rolodex hardware with mechanical knobs, arms, and realistic shading.

## Architecture & Key Components

### Structure

- **`index.html`** - Single-page HTML with semantic structure and inline footer script for year auto-update
- **`styles.css`** - Comprehensive CSS including reset, complex gradients, 3D transforms, and intricate component styling
- **`assets/img/`** - SVG logos and PNG textures (knob texture, shading overlays)

### Design System

The UI mimics physical Rolodex hardware:

- `.middle` - Central card housing (24rem width, dark gradient background)
- `.side.side--left/right` - Mechanical arms and knobs flanking the cards
- `.card` - Individual contact cards with 3D flip animation
- `.knob` and `.arm` - Decorative mechanical elements with detailed gradient styling

## Critical Patterns & Conventions

### 3D Card Flip Mechanism

- **Hover behavior**: `.card:hover .card__container` transforms rotateY (horizontal) for portrait orientation
- **Vertical cards** use `transform-origin: 100% 180px` and `rotateX` for top-to-bottom flip
- **Touch support**: `ontouchstart="this.classList.toggle('hover')"` in HTML for mobile device interaction
- **Backface visibility**: Hidden on front/back to prevent double-rendering during flip
- **Transition**: `0.3s cubic-bezier(0.33, 1, 0.68, 1)` easing for smooth flip

### Styling Conventions

- **CSS Variables Not Used** - All colors/gradients are hardcoded (consider extracting to CSS custom properties for future maintainability)
- **Gradient Complexity** - Multi-stop gradients (8-10 stops) create metallic/beveled effects on knobs and arms
- **Z-index Layering** - Critical for depth (card-ring: z-5, knobs: z-3, middle: z-3, background: z-1)
- **Absolute Positioning** - Used extensively for logo placement, card rings, and decorative elements

### Typography

- **Header font**: "Instrument Serif" (imported from Google Fonts) - serif serif for elegance
- **Body font**: Bahnschrift/DIN Alternate fallback stack for geometric feel
- **Letter spacing**: Tight (e.g., `-0.012rem` on h2) for retro feel

## Developer Workflows

### Local Development

- No build process required - vanilla HTML/CSS with static assets
- Open `index.html` directly in browser or use simple HTTP server
- All styling is in single `styles.css` file (~422 lines)

### Modifying Cards

1. Add new `.card.vertical` elements inside `.cards__list` div
2. Populate `.card__front` with contact info and `.card__back` (currently empty)
3. Touch/hover interaction is automatic via existing CSS

### Asset Management

- **SVGs**: `logo-full.svg` (header), `logo.svg` (footer), `base-footer.svg`
- **PNGs**: `knob-dial-texture.png` (repeating 4x4px texture), `shading.png` (bottom overlay)
- Textures use `background: url()` with `background-size` to tile

## Code Characteristics

- **No frameworks/libraries** - Pure semantic HTML and CSS
- **Inline JavaScript**: Minimal - only auto-updates footer year
- **Responsive**: Uses flexbox and percentage widths, but layout is desktop-optimized
- **Accessibility notes**: Touch support via `ontouchstart`, but no ARIA labels or semantic button elements

## Common Tasks

- **Change color scheme**: Modify hex colors in gradients throughout `styles.css`
- **Adjust card dimensions**: Height is `180px`, width is `90%` of container
- **Add new mechanical parts**: Follow knob/arm pattern with new `.knob` or `.arm` classes and gradient backgrounds
- **Update header/footer**: Edit `index.html` directly; footer year updates automatically
