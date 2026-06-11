---
target: src/pages/index.astro
total_score: 28
p0_count: 0
p1_count: 0
timestamp: 2026-06-11T16-29-20Z
slug: src-pages-index-astro
---
# Design Critique — 千忆 AI Landing Page (Run 3)

**Target**: `src/pages/index.astro` · **Score**: 28/40 · **Rating**: Good

## Heuristic Scores

| # | Heuristic | R1 | R2 | R3 | Key Issue |
|---|-----------|----|----|----|-----------|
| 1 | Visibility of System Status | 3 | 3 | 3 | Form submitting state; no nav highlighting |
| 2 | Match System / Real World | 3 | 3 | 3 | Trust section adds honesty; CTA repetition still present |
| 3 | User Control and Freedom | 2 | 3 | 3 | Submitting state; no undo but acceptable for this surface |
| 4 | Consistency and Standards | 2 | 3 | 3 | Spacing/muted/amber aligned; --text-hero & --font-mono still unused |
| 5 | Error Prevention | 1 | 2 | 2 | required + autocomplete; no custom validation |
| 6 | Recognition Rather Than Recall | 3 | 3 | 3 | Step numbers, source tags, trust context |
| 7 | Flexibility and Efficiency | 2 | 2 | 2 | Acceptable for landing page |
| 8 | Aesthetic and Minimalist Design | 3 | 3 | **4** | Scenarios de-carded; heading hierarchy fixed; trust adds variety; amber provides warmth |
| 9 | Error Recovery | 1 | 2 | 2 | Browser validation + submitting state |
| 10 | Help and Documentation | 3 | 3 | 3 | FAQ + privacy note + response timeline + trust |
| **Total** | | **23** | **27** | **28** | **Acceptable → Good** |

## Resolved Since Run 2

- P2: Mobile hero mock order — removed `order: -1`, headline stays first on mobile
- P2: Zero social proof — added trust section ("专注知识库问答的工作室")
- P3: Heading hierarchy — `<h4>` → `<h3>`, WCAG 1.3.1 compliant
- P3: Card pattern repetition — `.how-scenarios` de-carded, now clean inline tag cloud

## Remaining Observations (P3/Polish)

- `--text-hero` token defined but unused — hero h1 uses custom clamp
- `--font-mono` token defined but zero references
- favicon.svg hardcodes `#3d8c5e`, decoupled from `--color-primary`
- No `og:image` meta tag
- Placeholder text contrast could be improved (`oklch(0.600...)` on white ≈ 2.9:1)

## Trend

23 → 27 → 28. All P0–P3 issues from initial critique resolved. Score crosses into Good band. Remaining items are token hygiene and minor polish.
