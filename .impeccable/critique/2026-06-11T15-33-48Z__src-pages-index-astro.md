---
target: src/pages/index.astro
total_score: 23
p0_count: 2
p1_count: 2
timestamp: 2026-06-11T15-33-48Z
slug: src-pages-index-astro
---
# Design Critique — 千忆 AI Landing Page

**Target**: `src/pages/index.astro` · **Score**: 23/40 · **Rating**: Acceptable

## Anti-Patterns Verdict

**AI Slop: MAYBE** — The page dodges all hard bans (no gradient text, no side-stripe borders, no numbered section markers, no glassmorphism, no editorial-typographic reflex). But it fails soft-signal tests: identical card grid (`.prob`), amber accent declared but unused (token rot), zero real imagery, category-reflex "AI tool → green on white" palette.

**Detector**: CLI returned `[]` (exit 0). No automated findings. Detector missed undefined CSS custom properties and contrast failures.

## Heuristic Scores

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 3/4 | No active nav highlighting; form submit has no loading state |
| 2 | Match Between System and Real World | 3/4 | CTA repeated 3 times; workflow language maps well to real needs |
| 3 | User Control and Freedom | 2/4 | Form submit replaces entire form — no undo, no edit, no confirmation |
| 4 | Consistency and Standards | 2/4 | `--text-hero` unused; `--color-muted` DESIGN.md/code mismatch; undefined spacing tokens break layout |
| 5 | Error Prevention | 1/4 | Zero form validation; no required-field indicators |
| 6 | Recognition Rather Than Recall | 3/4 | Step numbers clear; no "copy WeChat ID" button |
| 7 | Flexibility and Efficiency | 2/4 | No search; no "expand all" FAQ; no keyboard shortcuts |
| 8 | Aesthetic and Minimalist Design | 3/4 | Clean hierarchy; visual monotony from repeated card pattern |
| 9 | Error Recovery | 1/4 | No error states defined; no validation messages |
| 10 | Help and Documentation | 3/4 | FAQ clear; no onboarding guide or docs link |
| **Total** | | **23/40** | **Acceptable** |

## Cognitive Load

**2/8 failures** (moderate): Scenario tags 5 items exceeds chunking limit; contact section has 2 parallel channels creating decision point.

## Emotional Journey

**Peak**: Product mock in hero — strongest trust-building moment.
**Critical valley**: Contact section — zero social proof, zero trust signals, bare form.
**End**: Footer emotionally empty. Peak-end rule: weak ending disproportionately damages lasting impression.

## Strengths

1. Product mock as visual anchor — communicates core value in seconds
2. Professional CSS architecture — clamp(), text-wrap, reduced-motion, semantic z-index
3. Native HTML semantics — `<details>` FAQ, aria-labelledby, aria-expanded

## Priority Issues

### P0 — Undefined spacing tokens silently break layout
`--space-5` and `--space-10` used in 7 CSS rules but undefined in tokens.css. All affected gaps/paddings collapse to 0. Fix: add `--space-5: 1.25rem; --space-10: 2.5rem;` to tokens.css.

### P0 — Amber accent token completely unused
`--color-accent: oklch(0.550 0.125 45)` declared but never referenced. Page renders as pure green monochrome. "Professional-but-warm" brand personality has no visual warmth carrier. Fix: apply amber to inline links, source tags, scenario tags per DESIGN.md 2-5% coverage.

### P1 — Global muted text contrast fails WCAG AA
`--color-muted: oklch(0.360 0.008 140)` contrast vs white bg ≈ 3.0:1 (needs 4.5:1). Affects nearly all secondary text on the page. Also DESIGN.md specifies `0.400` but code implements `0.360`. Fix: raise to at least `oklch(0.440 0.008 140)`.

### P1 — Contact form has zero trust infrastructure
No validation, no privacy notice, no response timeline, no security indicators. Submit instantly erases form with no recovery on error. Fix: add required attributes, privacy copy, response timeline, intermediate submitting state.

### P2 — Hero mock appears above value proposition on mobile
`order: -1` moves CSS wireframe above headline at ≤640px. Mobile first impression is gray box, not value prop. Fix: remove `order: -1`, keep text first.

### P2 — Zero social proof
No customer logos, testimonials, user counts, case studies. B2B product targeting team managers lacks expected credibility signals. Fix: add at minimum one trust signal.

### P3 — Heading hierarchy skip (h2→h4)
Problem cards use `<h4>` directly under `<h2>`, skipping `<h3>`. Violates WCAG 1.3.1. Fix: change to `<h3>`.

## Persona Red Flags

**Jordan (First-Timer)**: Product name dropped before value established; nav CTA premature; 3 one-line problem descriptions may not resonate; no "vs ChatGPT" messaging.

**Riley (Stress Tester)**: Zero social proof flagged immediately; mock disclaimer reads as "product may not exist"; no technical differentiation; no pricing; "后续可扩展" flagged as vaporware.

**Casey (Distracted Mobile)**: Mock above headline on mobile; CTA buttons push content below fold; nav CTA hidden in hamburger; no floating/sticky CTA on scroll; headline ~24px for dense Chinese.

**李经理 (Small Business Manager)**: "资料准备完整后" is vague on effort required; no team onboarding story; no ROI framing; WeChat contact feels too casual for business procurement.

## Minor Observations

- `--color-muted` DESIGN.md `0.400` vs tokens.css `0.360` — documentation drift
- `--text-hero` token defined but never used — hero h1 uses custom clamp
- `--font-mono` token defined but zero references — pure token rot
- favicon.svg hardcodes `#3d8c5e`, decoupled from `--color-primary`
- No `og:image` meta tag
- `prefers-reduced-motion` correctly implemented

## Provocative Questions

1. If anyone can guess your entire design system from hearing "AI knowledge base tool," have you actually designed anything?
2. Amber at 0% surface — did you intend to use it and forget, or include it because design systems "should" have a secondary accent?
3. The contact form asks for trust but gives nothing in return. Would YOU fill out this form?
4. A CSS wireframe labeled "to be replaced" — is this page premature? Would honest "launching soon" messaging serve the brand better?
