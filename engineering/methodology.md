# Methodology

How I plan, build, and verify work.

## Plan → Prove → Present

1. **Plan:** write the flow and the metric before the code. If it cannot be
   drawn, it cannot be built.
2. **Prove:** build the smallest thing that demonstrates the claim, then test
   it for real. Local runs, pinned SHAs, recorded outputs.
3. **Present:** document what was done, how it was validated, and — critically —
   what was **not** validated.

## Working principles

- **Evidence over adjectives.** "94% success, 2% collisions over 100 seeded
  episodes" beats "excellent performance."
- **Small, reviewable increments.** Each change is isolated and testable.
- **Frozen targets are sacred.** Once a submission target is frozen, no edits —
  it becomes a verifiable artifact.
- **Honest boundaries.** A documented limitation is credibility; a hidden one
  is a liability.
- **No fake metrics.** No fake stars, bots, or inflated claims. Trust is earned
  in the diff.

## Personal standard

- Type every interface.
- Test every seam.
- Document every boundary.
- Reproduce every result.
