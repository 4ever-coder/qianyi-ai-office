---
target: src/pages/index.astro
total_score: 27
p0_count: 0
p1_count: 0
timestamp: 2026-06-11T16-15-03Z
slug: src-pages-index-astro
---
# Design Critique — 千忆 AI Landing Page (Re-run)

**Target**: `src/pages/index.astro` · **Score**: 27/40 · **Rating**: Good

## Heuristic Scores

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 3/4 | Form has submitting state; no active nav highlighting |
| 2 | Match Between System and Real World | 3/4 | CTA repeated 3 times; workflow language maps well |
| 3 | User Control and Freedom | 3/4 | Form has intermediate submitting state; no full undo |
| 4 | Consistency and Standards | 3/4 | Spacing tokens all defined; muted/amber consistent with DESIGN.md; --text-hero and --font-mono still unused |
| 5 | Error Prevention | 2/4 | required + autocomplete + browser validation; no custom format checks |
| 6 | Recognition Rather Than Recall | 3/4 | Step numbers, headings, source-tags clear; no copy WeChat button |
| 7 | Flexibility and Efficiency | 2/4 | No search; no expand all FAQ; no keyboard shortcuts |
| 8 | Aesthetic and Minimalist Design | 3/4 | Amber breaks green monochrome; card repetition still present |
| 9 | Error Recovery | 2/4 | Submitting state + browser validation messages; no custom recovery |
| 10 | Help and Documentation | 3/4 | FAQ clear; privacy note and response timeline added |
| **Total** | | **27/40** | **Good** |

## Resolved Issues (since last critique)

- P0: Missing spacing tokens — fixed, 7 layout collapses resolved
- P0: Amber accent unused — fixed, 6 injection points at ~3-5% coverage
- P1: Muted text contrast — fixed, `0.360→0.440` yields ~5.0:1
- P1: Form trust infrastructure — fixed, required attrs, privacy note, response timeline, submitting state

## Remaining Issues

### P2 — Hero mock above value prop on mobile
`order: -1` at ≤640px moves CSS wireframe above headline. Mobile first impression is gray box, not value proposition.

### P2 — Zero social proof
No customer logos, testimonials, user counts, or case studies. B2B product targeting team managers lacks expected credibility signals.

### P3 — Heading hierarchy skip (h2→h4)
Problem cards use `<h4>` directly under `<h2>`, skipping `<h3>`. Violates WCAG 1.3.1.

### P3 — Card pattern repetition
`.prob`, `.hs-item`, `.how-scenarios` use identical visual module (border+surface bg+radius) across three consecutive sections.

## Token Health

- `--color-accent`: 4 refs (was 0)
- `--color-accent-text`: 1 ref (new)
- `--space-5`, `--space-10`: defined and in use
- `--color-muted`: `0.440` matches DESIGN.md
- `--text-hero`: still unused
- `--font-mono`: still unused
