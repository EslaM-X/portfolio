# Testing Notes

What "tested" means in my work.

## Levels

| Level | What it covers | Example |
| --- | --- | --- |
| Unit | One function, no I/O | A validator given bad JSON returns None |
| Component | One module against fakes | Simulator adapter returns expected frames |
| Integration | Real components, real I/O | Go tunnel E2E: WS proxy → x402 → paid skill |
| Validation | Whole-experiment metrics | Sim-to-sim deviation report |

## Rules

1. **Test the boundary, not the internals.** Public behaviour, not private
   methods.
2. **Fake the I/O, keep the logic real.** Physics and network are faked at the
   adapter seam; policy logic runs for real.
3. **Deterministic seeds.** Experiments must reproduce bit-for-bit on the same
   inputs.
4. **Report, don't just pass.** Test runs emit machine-readable evidence
   (metrics, SHAs, exit codes).

## CI as evidence

CI is not decoration. A run on a pinned SHA that exercises the real build,
lint, tests, and security checks is a **claim a reviewer can verify**. That is
why the RoboPay submission treats "approve and run" as the critical path, not
the code itself.

## See also

- [Methodology](methodology.md)
