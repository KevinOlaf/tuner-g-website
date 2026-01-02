# Tuner-G Website Design Specification

## Overview

Professional, compact website for Tuner-G iOS guitar tuner application. Design emphasizes clean aesthetics, avoids AI-generated visual clichés (vibrant gradients), and maintains consistency with the iOS app's neumorphic design language.

---

## Design Philosophy

### Core Principles
1. **Professional Minimalism**: Clean, uncluttered layouts with ample whitespace
2. **Native Feel**: Design language consistent with iOS app (neumorphic style)
3. **Accessibility First**: Semantic HTML, readable typography, proper contrast
4. **Performance**: Fast loading, no unnecessary dependencies
5. **Mobile First**: Responsive design starting from mobile breakpoints

### Anti-Patterns to Avoid
- ❌ Blue-purple gradients (AI-generated aesthetic)
- ❌ Overly vibrant, neon colors
- ❌ Complex animations or parallax effects
- ❌ Heavy frameworks or dependencies
- ❌ Generic stock photography

---

## Color System

### Primary Palette
Derived directly from Tuner-G iOS app's neumorphic design system:

```css
/* Background Colors */
--color-bg-dark: #212123        /* Primary dark background */
--color-bg-light: #E9E9EA       /* Primary light background */
--color-surface-dark: #2C2C2E   /* Elevated surfaces (cards) */
--color-surface-light: #FFFFFF  /* Light mode cards */

/* Text Colors */
--color-text-primary-dark: #FFFFFF      /* High emphasis text */
--color-text-secondary-dark: #A8A8A8   /* Medium emphasis */
--color-text-primary-light: #1C1C1E    /* Light mode primary */
--color-text-secondary-light: #6E6E73  /* Light mode secondary */

/* Accent Colors */
--color-accent: #33D98C              /* In-tune green (RGB: 51, 217, 140) */
--color-accent-hover: #2BC278        /* Slightly darker on hover */
```

### Color Usage Guidelines

**Backgrounds**
- Main page: `#212123` (dark charcoal)
- Elevated cards: `#2C2C2E` (slightly lighter)
- No gradients - solid colors only

**Text Hierarchy**
- Primary headings: `#FFFFFF` (100% opacity)
- Body text: `#A8A8A8` (65% opacity equivalent)
- Captions/metadata: Use secondary color

**Accent Color**
- CTAs (Call-to-Action buttons)
- Links and interactive elements
- Focus states
- Success indicators

**Contrast Ratios**
- AA compliance minimum: 4.5:1 for body text
- AAA target: 7:1 for headings
- Current implementation meets WCAG AA standards

---

## Typography

### Font Stack
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
             "Helvetica Neue", Arial, sans-serif;
```

**Rationale**: System fonts provide:
- Native feel on each platform
- Optimal rendering and readability
- Zero font loading time
- Consistent with iOS app

### Type Scale

| Element | Size (Desktop) | Size (Mobile) | Weight | Line Height |
|---------|---------------|---------------|--------|-------------|
| H1      | 48px          | 32px          | 700    | 1.2         |
| H2      | 32px          | 24px          | 600    | 1.3         |
| H3      | 24px          | 20px          | 600    | 1.4         |
| Body    | 18px          | 16px          | 400    | 1.6         |
| Small   | 16px          | 14px          | 400    | 1.5         |

### Typography Guidelines

**Letter Spacing**
- H1: -0.02em (tighter, more impactful)
- H2: -0.01em
- Body: 0 (default)

**Font Weights**
- Bold: 700 (headings only)
- Semibold: 600 (subheadings, labels)
- Regular: 400 (body text)
- Never use weights below 400

**Text Rendering**
```css
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
```

---

## Layout System

### Grid & Spacing

**Container**
- Max width: 1200px
- Horizontal padding: 24px (mobile), 40px (desktop)
- Centered with `margin: 0 auto`

**Spacing Scale**
```css
--spacing-xs: 8px
--spacing-sm: 16px
--spacing-md: 24px
--spacing-lg: 40px
--spacing-xl: 80px
```

**Section Spacing**
- Between major sections: 80px (mobile: 40px)
- Within sections: 40px (mobile: 24px)
- Component margins: 24px

### Responsive Breakpoints

| Breakpoint | Width | Target Devices |
|-----------|-------|----------------|
| Mobile    | 0-480px | Phones portrait |
| Tablet    | 481-768px | Phones landscape, small tablets |
| Desktop   | 769px+ | Tablets landscape, laptops, desktops |

**Approach**: Mobile-first design
```css
/* Mobile styles (default) */
.element { ... }

/* Tablet and up */
@media (min-width: 481px) { ... }

/* Desktop and up */
@media (min-width: 769px) { ... }
```

---

## Component Specifications

### Navigation Header

**Structure**
- Sticky positioning (stays at top on scroll)
- Height: 64px
- Background: Dark with 95% opacity + blur backdrop
- Border bottom: 1px solid rgba(255, 255, 255, 0.1)

**Layout**
```
┌─────────────────────────────────────┐
│ [Logo]              [Nav Links]     │
└─────────────────────────────────────┘
```

**Interactions**
- Nav links: Secondary color → Primary on hover
- Active page: Primary color, no underline
- Mobile: Full navigation visible (no hamburger menu for 3 links)

### Hero Section

**Layout**
- Padding: 160px vertical (mobile: 80px)
- Text alignment: Center
- Max width: 800px (for subtitle)

**Content Hierarchy**
1. App name (H1): Large, bold
2. Tagline: 28px, secondary color
3. Subtitle: 18px, secondary color, max 600px width
4. CTA: Prominent button or App Store badge

**Visual Treatment**
- No background images or decorative elements
- Focus on typography and whitespace
- Optional: Small app icon above name

### Feature Cards

**Grid System**
```css
display: grid;
grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
gap: 40px;
```

**Card Specifications**
- Background: `#2C2C2E` (elevated surface)
- Padding: 40px
- Border radius: 12px
- Hover: translateY(-4px) subtle lift

**Content Structure**
1. Icon/Emoji: 40px size
2. Heading (H3): Feature name
3. Description: 2-3 lines, 16px

**Icon Strategy**
- Use emoji (🎯, 🎸, ✨) for simplicity
- Alternative: SF Symbols-style icons (if SVG assets available)
- No icon libraries or external dependencies

### Footer

**Layout**
- Background: Elevated surface (`#2C2C2E`)
- Padding: 40px vertical
- Border top: 1px solid rgba(255, 255, 255, 0.1)

**Content**
```
┌─────────────────────────────────────┐
│ Copyright © 2026      [Links]       │
└─────────────────────────────────────┘
```

**Mobile**: Stacked vertically, centered

### Form Elements (Contact Page)

**Input Fields**
- Background: `#212123` (darker than card)
- Border: 1px solid rgba(255, 255, 255, 0.1)
- Padding: 12px 16px
- Border radius: 8px
- Focus: Border color → accent green

**Labels**
- Above input, 14px
- Margin bottom: 8px
- Weight: 500 (medium)

**Submit Button**
- Same styling as CTA button
- Full width on mobile
- Inline on desktop

---

## Interactions & Animations

### Hover States

**Links**
```css
transition: color 0.2s ease;
color: var(--color-accent-hover);
```

**Buttons**
```css
transition: all 0.2s ease;
transform: translateY(-2px);
box-shadow: 0 8px 24px rgba(51, 217, 140, 0.3);
```

**Cards**
```css
transition: transform 0.2s ease;
transform: translateY(-4px);
```

### Focus States
- Keyboard navigation: 2px accent-colored outline
- Offset: 2px
- Border radius: match element

### Animation Principles
- Duration: 0.2s for UI feedback, 0.3s for page transitions
- Easing: `ease` for most interactions
- No animation longer than 0.5s
- Respect `prefers-reduced-motion` media query

---

## Accessibility Standards

### Semantic HTML
- `<header>`, `<nav>`, `<main>`, `<footer>` elements
- Proper heading hierarchy (H1 → H2 → H3)
- `<section>` for major content blocks
- Form labels with `for` attribute

### ARIA Labels
```html
<a href="#" aria-label="Download on the App Store">
<button aria-label="Submit contact form">
```

### Keyboard Navigation
- Tab order follows visual order
- Focus states clearly visible
- Skip to content link (optional)
- No keyboard traps

### Screen Reader Support
- Alt text for images
- Descriptive link text (no "click here")
- Form validation messages announced
- Status updates for dynamic content

---

## Performance Specifications

### Loading Strategy
- Critical CSS inline (optional for GitHub Pages)
- No JavaScript required for core functionality
- Images lazy-loaded (when added)
- No external font requests

### File Sizes
- HTML: < 15KB per page
- CSS: < 50KB total
- Total initial load: < 100KB

### Metrics Targets
- First Contentful Paint: < 1s
- Time to Interactive: < 2s
- Lighthouse Score: 90+ across all categories

---

## Content Strategy

### Landing Page (index.html)

**Hero Message**
- Primary: "Tuner-G" (app name)
- Secondary: "Precision Guitar Tuning for iOS" (value prop)
- Tertiary: Longer description of capabilities

**Features Section**
6 key features highlighting:
1. Technical accuracy (YIN/PYIN algorithms)
2. Instrument support (guitar, bass, ukulele)
3. Visual design (neumorphic interface)
4. Customization (settings, tunings)
5. Reference tones
6. Tip jar model (ad removal)

### Privacy Policy (privacy.html)

**Required Sections**
- Microphone usage explanation
- Data collection disclosure (UserDefaults)
- Third-party services (AdMob, StoreKit)
- What data is NOT collected
- User rights and choices
- Contact information
- API usage disclosure (App Store requirement)

**Legal Compliance**
- GDPR considerations
- CCPA compliance
- Apple App Store requirements
- Last updated date

### Contact Page (contact.html)

**Form Fields**
1. Name (required)
2. Email (required)
3. Subject (required)
4. Message (required, textarea)

**Alternative Contact**
- Direct email link: support@tunerg.app
- Formspree integration for form submissions

---

## Technical Implementation

### File Structure
```
tuner-g-website/
├── index.html          # Landing page
├── privacy.html        # Privacy policy
├── contact.html        # Contact form
├── css/
│   └── style.css      # All styles
├── js/
│   └── (future)       # Optional enhancements
└── assets/
    ├── app-icon.png   # To be added
    └── screenshots/   # To be added
```

### HTML Boilerplate
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="...">
    <title>...</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <!-- Content -->
</body>
</html>
```

### CSS Architecture
- CSS Variables for design tokens
- Mobile-first media queries
- BEM-inspired naming (flexible)
- Utility classes for common patterns
- No CSS preprocessors (vanilla CSS)

---

## Browser Support

### Target Browsers
- Safari 15+ (iOS and macOS)
- Chrome 90+
- Firefox 88+
- Edge 90+

### Progressive Enhancement
- Core experience works without JS
- CSS Grid with flexbox fallback (not needed for modern browsers)
- Modern CSS features with fallbacks where needed

---

## Deployment Checklist

### Pre-Launch
- [ ] All links tested and functional
- [ ] Form submission working
- [ ] Privacy policy URL finalized
- [ ] Support email configured
- [ ] Mobile responsiveness verified
- [ ] Accessibility audit passed
- [ ] Performance metrics meet targets
- [ ] SEO meta tags complete

### Post-Launch
- [ ] Submit privacy policy URL to App Store Connect
- [ ] Add App Store badge with live link
- [ ] Monitor form submissions
- [ ] Set up analytics (optional, privacy-respecting)

---

## Future Enhancements (Optional)

### Phase 2 Features
- App screenshots gallery
- User testimonials section
- FAQ section
- Blog/news section
- Multi-language support

### Advanced Features
- Dark/light mode toggle
- Search functionality
- Progressive Web App (PWA) manifest
- Service worker for offline support

---

## Design Deliverables

### Completed Files
1. ✅ `index.html` - Landing page with hero and features
2. ✅ `privacy.html` - Comprehensive privacy policy
3. ✅ `contact.html` - Contact form with email fallback
4. ✅ `css/style.css` - Complete stylesheet (~400 lines)
5. ✅ `README.md` - Deployment and setup instructions
6. ✅ `DESIGN_SPEC.md` - This comprehensive design document

### Assets Needed (To Be Added)
- App icon (PNG, 512x512px or larger)
- App Store badge (SVG from Apple)
- Screenshots (optional, for landing page gallery)

---

## Maintenance Guidelines

### Content Updates
- Privacy policy: Review quarterly, update "Last Updated" date
- Features: Sync with app updates
- Contact info: Verify email deliverability monthly

### Performance
- Monitor Core Web Vitals
- Optimize images when added (WebP format, lazy loading)
- Review and minify CSS for production

### Accessibility
- Annual audit using axe DevTools or Lighthouse
- Test with screen readers (VoiceOver on macOS/iOS)
- Verify keyboard navigation

---

## Credits & References

### Design Inspiration
- Apple.com (clean, product-focused)
- iOS Human Interface Guidelines
- Material Design (spacing/typography principles)

### Color Palette Source
- Derived from Tuner-G iOS app neumorphic design system
- In-tune green: RGB(51, 217, 140) from app code

### Typography
- System font stack best practices
- iOS typography guidelines

---

**Design Specification Version**: 1.0
**Last Updated**: January 2, 2026
**Designer**: Claude (via /sc:design)
**Status**: ✅ Complete and ready for deployment
