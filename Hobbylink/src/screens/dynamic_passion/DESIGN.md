---
name: Dynamic Passion
colors:
  surface: '#fcf9f8'
  surface-dim: '#dcd9d9'
  surface-bright: '#fcf9f8'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f6f3f2'
  surface-container: '#f0eded'
  surface-container-high: '#eae7e7'
  surface-container-highest: '#e5e2e1'
  on-surface: '#1b1c1c'
  on-surface-variant: '#5b403d'
  inverse-surface: '#303030'
  inverse-on-surface: '#f3f0ef'
  outline: '#906f6c'
  outline-variant: '#e4beb9'
  surface-tint: '#bb171c'
  primary: '#b7131a'
  on-primary: '#ffffff'
  primary-container: '#db322f'
  on-primary-container: '#fffbff'
  inverse-primary: '#ffb4ac'
  secondary: '#8b5000'
  on-secondary: '#ffffff'
  secondary-container: '#ff9800'
  on-secondary-container: '#653900'
  tertiary: '#006b1b'
  on-tertiary: '#ffffff'
  tertiary-container: '#1e862d'
  on-tertiary-container: '#f7fff1'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#ffdad6'
  primary-fixed-dim: '#ffb4ac'
  on-primary-fixed: '#410002'
  on-primary-fixed-variant: '#93000d'
  secondary-fixed: '#ffdcbe'
  secondary-fixed-dim: '#ffb870'
  on-secondary-fixed: '#2c1600'
  on-secondary-fixed-variant: '#693c00'
  tertiary-fixed: '#94f990'
  tertiary-fixed-dim: '#78dc77'
  on-tertiary-fixed: '#002204'
  on-tertiary-fixed-variant: '#005313'
  background: '#fcf9f8'
  on-background: '#1b1c1c'
  surface-variant: '#e5e2e1'
typography:
  display-lg:
    fontFamily: Roboto Flex
    fontSize: 40px
    fontWeight: '800'
    lineHeight: 48px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Roboto Flex
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.01em
  headline-lg-mobile:
    fontFamily: Roboto Flex
    fontSize: 26px
    fontWeight: '700'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Roboto Flex
    fontSize: 22px
    fontWeight: '700'
    lineHeight: 28px
  headline-sm:
    fontFamily: Roboto Flex
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Roboto Flex
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Roboto Flex
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Roboto Flex
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: Roboto Flex
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Roboto Flex
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Roboto Flex
    fontSize: 11px
    fontWeight: '700'
    lineHeight: 14px
    letterSpacing: 0.04em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  touch-target-min: 48px
  space-2xs: 4px
  space-xs: 8px
  space-sm: 12px
  space-md: 16px
  space-lg: 24px
  space-xl: 32px
  space-2xl: 48px
  margin-mobile: 16px
  margin-tablet: 24px
  gutter: 16px
---

## Brand & Style

This design system powers a global social networking ecosystem built to unite people around shared hobbies, niche crafts, and real-time physical activities. The brand personality is spirited, welcoming, energetic, and structurally reliable. It bridges genuine passion with safety, clarity, and rapid discovery.

The design movement is **Corporate / Modern**, guided directly by refined Material 3 principles. The visual posture uses confident primary crimson tones against pristine whites and structured neutral grays, ensuring user-generated imagery, community spaces, and active hobby radar cards remain front and center. The interface communicates immediate utility and joyful human connection, maintaining an authoritative yet warm cadence throughout mobile flows.

## Colors

The palette establishes an energetic visual presence while adhering strictly to Material contrast standards:

- **Primary (`#E53935`) & Primary Dark (`#D32F2F`)**: Drives brand recognition, major calls to action, active tab highlights, and focal badges.
- **Secondary / VIP Gold Amber (`#FF9800`)**: Governs premium membership statuses (VIP Pro), feature highlights, and active attention anchors.
- **Tertiary / Success Green (`#4CAF50`)**: Indicates online activity, validated community milestones, verified credentials, and real-time radar presence.
- **Surfaces & Backgrounds**: Base app canvas utilizes `#F8F9FA` transitioning to `#F5F5F5` for card wells, with `#FFFFFF` anchoring elevated cards, top app bars, and modal surfaces.
- **Text & Neutral Layers**: Deep charcoal `#212121` provides high-contrast typography, `#616161` manages secondary metadata, and `#E0E0E0` defines hairline surface outlines.

## Typography

Typography relies on `Roboto Flex` for unmatched legibility, mechanical precision, and adaptable width parameters across high-density mobile displays.

Headings feature tight tracking to emulate the punchy, confident presence seen in the brand identity. Body copy maintains comfortable leading for rapid scannability in feeds, direct messaging, and community discussion boards. Labels, buttons, and status tokens employ higher weights (`600`-`700`) with subtle letter spacing to preserve crisp rendering on smaller handheld devices.

## Layout & Spacing

This design system uses a strict **8px base grid** with a 4px half-step for micro-alignments, chip insets, and status badge coordinates.

### Touch Target Mandate
All interactive components (buttons, icon triggers, list items, selector chips) must respect a minimum touch target bounding box of **48px × 48px**, even when the visible visual glyph or pill is smaller.

### Breakpoints & Fluid Grid
- **Mobile (<600px)**: 4-column fluid layout with 16px screen edge margins and 16px gutters.
- **Tablet (600px - 1023px)**: 8-column fluid layout with 24px margins and 16px gutters; side sheets and navigation rails replace mobile bottom navigation bars.
- **Desktop (≥1024px)**: 12-column layout centered with max content width of 1200px, utilizing persistent master-detail panes for feed and chat interactions.

## Elevation & Depth

Visual hierarchy leverages Material elevation tiers via subtle, neutral ambient shadows rather than stark heavy outlines:

- **Level 0 (Flat / Canvas)**: `#F8F9FA` background with no shadow.
- **Level 1 (Cards & Feed Items)**: `#FFFFFF` surface with `0px 1px 3px rgba(0, 0, 0, 0.08), 0px 1px 2px rgba(0, 0, 0, 0.05)`.
- **Level 2 (Hover / Active Cards / Chips Selected)**: `0px 3px 6px rgba(0, 0, 0, 0.10), 0px 2px 4px rgba(0, 0, 0, 0.06)`.
- **Level 3 (Floating Action Buttons & App Bars)**: `0px 6px 12px rgba(0, 0, 0, 0.12), 0px 3px 6px rgba(0, 0, 0, 0.08)`.
- **Level 4 (Bottom Sheets, Drawers, Modals)**: `0px 12px 24px rgba(0, 0, 0, 0.16), 0px 4px 8px rgba(0, 0, 0, 0.10)` paired with a 40% `#000000` backdrop scrim.

## Shapes

The interface embraces a structured, modern curvature calibrated around standard 12px radius primitives for content containment:

- **Standard Cards, Panels & Modals**: 12px (`rounded-lg`) corner radii create comfortable visual framing without feeling overly playful.
- **Pills, Action Buttons & Chips**: Fully circular/pill shapes (9999px) are reserved for quick tap targets, activity indicators, and category tag filters.
- **Input Fields**: 8px (`rounded-md`) corner radii to maintain formal input structure and alignment with keyboard layouts.
- **Badges & Micro Indicators**: 4px to 6px radii to keep concise metadata crisp.

## Components

### Buttons
- **Filled Primary**: `#E53935` background with `#FFFFFF` text. Height is 48px, horizontal padding 24px, pill-shaped or 12px radius. Hover/active shifts to `#D32F2F`.
- **VIP Pro Action**: Gradient or solid `#FF9800` fill with deep charcoal `#212121` or white text, featuring bold label typography.
- **Tonal / Outlined**: 1px border `#E0E0E0`, `#212121` text, transparent background. In active state, background shifts to 8% `#E53935` tint.

### Cards
- **Hobby Activity Card**: Built on a `#FFFFFF` surface with a 12px radius and Level 1 elevation. Includes a 16px internal padding, primary title in `headline-sm`, contextual badges in top-right corner, and bottom-aligned action row.

### Chips & Filters
- **Interest Pills**: Height 36px (inside a 48px interactive touch area). Inactive state features `#F5F5F5` background with `#212121` text. Active state uses `#E53935` background with white text, or an outlined red treatment with a 12% fill.

### Status & Activity Indicators
- **Live Radar Dots**: 10px circular indicators with subtle breathing pulse animation:
  - 🟢 Active / Online Now (`#4CAF50`)
  - 🟡 Away / In Hobby Session (`#FF9800`)
  - 🔴 Live Host / Beacon Active (`#E53935`)
- Used on avatar corners with a 2px solid `#FFFFFF` separator border.

### Badges & Trust Accents
- **VIP Pro Badge**: Encapsulated capsule mirroring the brand lockup style. Vibrant `#FF9800` or red container with gold typography (`#FFD54F` or `#FFFFFF`).
- **Trust & Safety Badge**: Shield icon accompanying verified member profiles, rendered in `#4CAF50` with clear microcopy (`label-sm`).

### Input Fields
- Outlined fields with 8px radius, 52px height, 16px horizontal padding. Resting border `#E0E0E0`; focused border 2px solid `#E53935` with floating label transitioning to the primary red.