# Design

## Theme

Light mode. Pure white background with generous, deliberate whitespace — clarity and readability first. Brand identity carried by primary green accent, warm amber highlights, and precise typography. Linear-inspired layout: wide, confident sections with breathing room, content never feels cramped.

## Color

Strategy: **Restrained** — tinted neutrals + one primary accent at ≤10% of surface. Brand personality lives in the green and in the precision of the layout, not in decoration.

| Token | OKLCH | Role |
|---|---|---|
| `--color-bg` | `oklch(1.000 0.000 0)` | Page background — pure white |
| `--color-surface` | `oklch(0.965 0.003 140)` | Cards, panels, elevated sections — barely tinted toward green |
| `--color-ink` | `oklch(0.120 0.005 140)` | Body text — near-black with whisper of brand hue |
| `--color-muted` | `oklch(0.440 0.008 140)` | Secondary text, captions, meta — ≥4.5:1 vs bg |
| `--color-primary` | `oklch(0.520 0.135 140)` | Brand green — primary buttons, brand mark, key accents |
| `--color-primary-hover` | `oklch(0.460 0.135 140)` | Hover state — darker |
| `--color-primary-text` | `oklch(1.000 0.000 0)` | Text on primary fills — white |
| `--color-accent` | `oklch(0.550 0.125 45)` | Warm amber — highlights, badges, links, CTA accents |
| `--color-accent-text` | `oklch(1.000 0.000 0)` | Text on accent fills — white |
| `--color-border` | `oklch(0.900 0.005 140)` | Subtle borders, dividers |
| `--color-error` | `oklch(0.500 0.170 25)` | Error states, destructive actions |

### Usage ratios

- Primary green: ~5-10% — buttons, brand mark, step numbers, focus rings
- Accent amber: ~2-5% — badges, inline links, scenario tags, highlights
- Surface tint: alternating sections use `--color-surface` for gentle depth layering

### Contrast

- Body text (`--color-ink`) vs bg: ≥14:1
- Muted text (`--color-muted`) vs bg: ≥4.5:1 (WCAG AA)
- White text on primary/accent fills: readable
- All interactive elements meet WCAG AA minimums

## Typography

**Font**: Manrope — single family, geometric sans with architectural precision. Variable font, 5 weights (200–800). Conveys engineering confidence without feeling cold.

```css
--font-sans: 'Manrope', system-ui, sans-serif;
```

### Scale (Major Third, 1.25)

| Step | Size (clamp) | Weight | Use |
|---|---|---|---|
| `--text-h1` | `clamp(2rem, 4vw, 3.052rem)` | 700 | Page headings |
| `--text-h2` | `clamp(1.5rem, 3vw, 2.441rem)` | 600 | Section headings |
| `--text-h3` | `clamp(1.25rem, 2.5vw, 1.953rem)` | 600 | Subsection headings |
| `--text-h4` | `1.25rem` | 600 | Card headings |
| `--text-body` | `1rem` | 400 | Body copy |
| `--text-small` | `0.875rem` | 400 | Captions, meta |
| `--text-xs` | `0.75rem` | 500 | Labels, badges |

- Body line-height: 1.6
- Heading line-height: 1.15–1.25
- Heading letter-spacing: -0.02em to -0.03em
- `text-wrap: balance` on h1–h3; `text-wrap: pretty` on prose
- Body max-width: 65ch

## Spacing

4px base grid.

```
--space-1:  0.25rem   (4px)
--space-2:  0.5rem    (8px)
--space-3:  0.75rem  (12px)
--space-4:  1rem     (16px)
--space-5:  1.25rem  (20px)
--space-6:  1.5rem   (24px)
--space-8:  2rem     (32px)
--space-10: 2.5rem   (40px)
--space-12: 3rem     (48px)
--space-16: 4rem     (64px)
--space-24: 6rem     (96px)
```

Section vertical padding: `clamp(3rem, 8vw, 6rem)` — generous breathing room on desktop.

## Radius

```
--radius-sm:   0.25rem  (4px)   — subtle rounding
--radius-md:   0.5rem   (8px)   — buttons, inputs, small cards
--radius-lg:   0.75rem (12px)   — cards, panels
--radius-full: 999px            — pills, badges
```

## Motion

Minimal energy. Trust and clarity over spectacle.

- Page load: subtle fade-up on hero content only (300ms, ease-out)
- Hover: 150ms color/opacity transitions on interactive elements
- Scroll: no scroll-driven animations. Static is deliberate.
- Reduced motion: all transitions collapse to 0ms via `prefers-reduced-motion`

## Components

- **Buttons**: Solid primary fill with white text, ghost secondary with subtle border. 48px touch target minimum on mobile. Hover lift 1px.
- **Links**: Accent or primary color, underline on hover.
- **Cards**: White surface with subtle border. No nested cards.
- **Badges**: Primary or accent fill with white text. Pill shape. Subtle glow on hover.
- **Forms**: Clean border inputs on white bg, focus ring using primary color glow. Clear error states with `--color-error`.

## Breakpoints

```
--viewport-sm:  640px
--viewport-md:  768px
--viewport-lg:  1024px
--viewport-xl:  1280px
```

Mobile-first. Grids use `repeat(auto-fit, minmax(280px, 1fr))` for breakpoint-free responsive layouts where appropriate.

## Imagery

Product screenshots preferred over stock photography. Screenshots should show the actual product UI — knowledge base query, answer with citations, document management. Clean device frames or inline screenshots with subtle shadows. If stock is needed, use architectural/workspace imagery with natural light — engineering precision in the physical world.
