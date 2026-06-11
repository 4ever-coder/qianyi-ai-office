# Design

## Theme

Dark mode. Near-black background with subtle depth — engineering precision and focus. Brand carried by luminous green accent, warm amber highlights, and precise typography against dark surfaces. Atmospheric ambient glow at page edges for depth without distraction.

## Color

Strategy: **Restrained** — dark surfaces + luminous accents ≤10%. Color is light on dark; brand personality lives in the precision, not in decoration.

| Token | OKLCH | Role |
|---|---|---|
| `--color-bg` | `oklch(0.130 0.003 155)` | Page background — near-black with whisper of green |
| `--color-surface` | `oklch(0.170 0.003 155)` | Cards, panels, elevated sections — slightly lifted |
| `--color-ink` | `oklch(0.930 0.002 155)` | Body text — near-white, slightly warm |
| `--color-muted` | `oklch(0.580 0.005 155)` | Secondary text, captions, meta — ≥4.5:1 vs bg |
| `--color-primary` | `oklch(0.620 0.160 150)` | Brand green — luminous on dark, buttons, brand mark |
| `--color-primary-hover` | `oklch(0.680 0.155 150)` | Hover state — lighter |
| `--color-primary-text` | `oklch(0.120 0.003 155)` | Text on primary fills — near-black |
| `--color-accent` | `oklch(0.660 0.150 60)` | Warm amber — luminous on dark, badges, links, highlights |
| `--color-accent-text` | `oklch(0.120 0.003 155)` | Text on accent fills — near-black |
| `--color-border` | `oklch(0.220 0.003 155)` | Subtle borders, dividers — low contrast against dark bg |
| `--color-error` | `oklch(0.580 0.180 25)` | Error states, destructive actions |

### Usage ratios

- Primary green: ~5-10% — buttons, brand mark, step numbers, focus rings
- Accent amber: ~2-5% — badges, inline links, scenario tags, highlights
- Surface elevation: alternating sections use `--color-surface` for subtle depth layering

### Atmosphere

- Body has a fixed `::before` pseudo-element with two subtle radial gradients: a green glow at top-center (4% opacity) and an amber glow at bottom-right (3% opacity). These provide atmospheric depth without distracting from content.

### Contrast

- Body text (`--color-ink`) vs bg: ≥14:1
- Muted text (`--color-muted`) vs bg: ≥4.5:1 (WCAG AA)
- Near-black text on primary/accent fills: ≥10:1
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

- **Buttons**: Solid primary/accent fill with near-black text, ghost secondary with hairline border. 48px touch target minimum on mobile. Hover lift 1px.
- **Links**: Accent or primary color, underline on hover.
- **Cards**: Dark surface with hairline border. No nested cards.
- **Badges**: Primary or accent fill with near-black text. Pill shape. Subtle glow on hover.
- **Forms**: Dark bg inputs with subtle border, focus ring using primary color glow. Clear error states with `--color-error`.

## Breakpoints

```
--viewport-sm:  640px
--viewport-md:  768px
--viewport-lg:  1024px
--viewport-xl:  1280px
```

Mobile-first. Grids use `repeat(auto-fit, minmax(280px, 1fr))` for breakpoint-free responsive layouts where appropriate.

## Imagery

Product screenshots preferred over stock photography. Screenshots should show the actual product UI on dark background — knowledge base query, answer with citations, document management. Clean device frames or inline screenshots with subtle ambient glow. If stock is needed, use architectural/workspace imagery with controlled, directional lighting — precision and depth in the physical world.
