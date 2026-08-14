# Case Study — RoboPay: Unitree Go2 Tier-1 Simulation

> **Role:** Open-source contributor
> **Repository:** [`fabricfoundation/RoboPay`](https://github.com/fabricfoundation/RoboPay)
> **Contribution:** [PR #89](https://github.com/fabricfoundation/RoboPay/pull/89) —
> plus platform contributions in [#91](https://github.com/fabricfoundation/RoboPay/pull/91),
> [#92](https://github.com/fabricfoundation/RoboPay/pull/92),
> [#93](https://github.com/fabricfoundation/RoboPay/pull/93),
> [#94](https://github.com/fabricfoundation/RoboPay/pull/94),
> [#95](https://github.com/fabricfoundation/RoboPay/pull/95).

## Problem

RoboPay lets robots earn and pay for actions on-chain. A Unitree Go2 robot must
be able to **execute paid skills reliably**, settle payments only when the
action actually succeeded, and reproduce that behaviour in simulation before
hardware runs cost money.

The hard part is not the motion — it is **proving** the motion: measurable
execution, reproducible physics, and honest failure semantics.

## Architecture

```
Skill request → x402 payment gate → Policy → Controller → Simulator
        → Metrics → Validation report → Settlement decision
```

- **Policy / controller** drive deterministic action execution
  (wave, sit, stand, bow, nod, turn_to_face, hold, navigate_obstacle,
  plus `stop` as the always-available fail-safe).
- **MuJoCo** (mujoco_menagerie Go2 model) and **PyBullet** backends behind a
  shared contract → **sim-to-sim validation**.
- **Payment gate** (Go tunnel) enforces `no-settle-on-failure`: the settlement
  decision is correlated with the measured execution result.

## Implementation highlights

- `navigate_obstacle` — online obstacle navigation with waypoint tracking,
  contact detection, and goal-distance metrics.
- Sim-to-sim: measured cross-simulator deviation on identical tasks.
- Durable, replayable experiment runs with pinned versions and seeds.
- Go tunnel E2E path: real tunnel binary, WS proxy, x402 flow, paid skill
  execution.

## Validation

- 34 tests across 5 suites (control, payment_gate, result_semantics, link,
  sim2sim).
- Live EIP-3009 settlement: 3 real USDC transactions on Base Sepolia, each
  verifiable on Basescan, reproducible with zero deposited capital.
- Honesty boundary documented in `docs/validation-report.md` — what was
  validated, and what was not.

## Platform contributions (same repo)

- **#91 CI hardening** — pinned golangci-lint action, concurrency/timeout/paths,
  single test pass, zenoh-c cache.
- **#92 Security/config** — payment payload redaction, 1 MiB body cap (413),
  CORS fix, strict env parsing, with tests.
- **#93 Registry gate** — `docs/registry.md` + permissive validator; the gate
  auto-runs stricter per-profile validators.
- **#94 Python baseline** — ruff + pytest for the shared bridge; fixed a real
  parser crash (non-object JSON raised AttributeError).
- **#95 Docs/front door** — `CONTRIBUTING.md`, README TOC and layout.

## Lessons learned

1. **CI proof is part of the submission.** A green, GitHub-hosted run on the
   exact frozen SHA is worth more than prose.
2. **Simulation is only as honest as its boundary.** Document what is physics
   and what is approximated.
3. **Settlement and execution must be correlated.** Pay only for what happened.
4. **Small, isolated platform PRs** build reviewer trust faster than one giant
   change.
