# Case Study — RoboPay: Spot and Go2 Tier-1 Simulations

> **Role:** Open-source contributor
> **Repository:** [`fabricfoundation/RoboPay`](https://github.com/fabricfoundation/RoboPay)
> **Contributions:** [PR #86 (Spot)](https://github.com/fabricfoundation/RoboPay/pull/86) ·
> [PR #89 (Go2)](https://github.com/fabricfoundation/RoboPay/pull/89) — plus platform
> hardening in [#91](https://github.com/fabricfoundation/RoboPay/pull/91),
> [#92](https://github.com/fabricfoundation/RoboPay/pull/92),
> [#93](https://github.com/fabricfoundation/RoboPay/pull/93),
> [#94](https://github.com/fabricfoundation/RoboPay/pull/94),
> [#95](https://github.com/fabricfoundation/RoboPay/pull/95).

## Problem

RoboPay lets robots earn and pay for actions on-chain. A robot must execute a
**paid skill reliably**, settle payment **only when the action actually
succeeded**, and reproduce that behaviour in simulation before hardware runs
cost money. The hard part is not the motion — it is **proving** it: measurable
execution, reproducible physics, and honest failure semantics.

## Two separate Tier-1 submissions

Two distinct robot profiles, both by EslaM-X, in the same program — they are
easy to conflate and must not be:

### Boston Dynamics Spot — [PR #86](https://github.com/fabricfoundation/RoboPay/pull/86)

- **8 paid skills:** `wave`, `sit`, `stand`, `stop` (safe-stop),
  `bow`, `nod`, `turn_to_face`, `hold`.
- Joint-space trajectory controller on the official MuJoCo Spot model
  (mujoco_menagerie) — never a replayed animation.
- **Sim-to-sim:** same joint configurations recomputed in MuJoCo and PyBullet
  agree to **0.06 cm** across all salient poses.
- **6 testable failure paths** (`UNPAID`, `INVALID_PARAMS`, `UNKNOWN_SKILL`,
  `WRONG_ROBOT`, `DUPLICATE`, tampered `paramsHash`); 4 test suites.
- **Payment gate:** unpaid → `402` + `PAYMENT-REQUIRED`; forged/expired
  receipts → `402`; replayed keys → `409`; only `status: success` may settle.
- **Honest scope:** simulator-only; settlement exercised against the same local
  facilitator the robot link trusts — no on-chain settlement.

### Unitree Go2 — [PR #89](https://github.com/fabricfoundation/RoboPay/pull/89)

- **9 paid skills:** the Spot 8 **plus `navigate_obstacle`** — online obstacle
  navigation with a potential-field local planner, waypoint tracking, and
  real physics contact detection (MuJoCo contact pairs, not distance
  estimates).
- **Sim-to-sim:** MuJoCo ⇄ PyBullet identical kinematics by construction,
  observed worst case **≤ 0.02 cm**; plus a real **Webots R2025a** runtime
  run in CI (`go2_sim2sim.wbt`).
- **8 testable failure paths** (adds `TIMEOUT` and `COLLISION` — proven on the
  real controller path); 7 test suites + real Go tunnel E2E in CI (builds the
  actual `tunnel/` binary with zenoh-c).
- **On-chain settlement:** correct EIP-3009 (`TransferWithAuthorization`,
  domain `"USDC"`/version `"2"`/chainId `84532`), offline signer-recovery
  verification, **3 real 1.0 USDC transactions on Base Sepolia** (free faucet
  funding), round-4 live proof in the PR.
- **Durable replay protection:** file-backed store; idempotency keys survive a
  restart (`test_durable_replay.py`).

## Architecture (shared shape, two instantiations)

```
Paid action (x402) → Zenoh robot/tunnel/action
    → robopay_link.py → validate envelope + payment gate (durable replay)
    → joint-space controller on mujoco_menagerie
    → metrics → result on robot/tunnel/result (correlated by actionId)
    → settle ONLY on status:success
```

- **Payment gate enforces `no-settle-on-failure`** — settlement correlates
  with the measured execution result.
- **Sim-to-sim validation** proves the physics claim across engines with
  machine-readable reports.
- **Wire parity** with the production tunnel: identical `ActionEnvelope` and
  `ActionResult` schemas, peer-mode Zenoh, same x402 decision semantics.

## Platform contributions (same repo)

- **#91 CI hardening** — pinned golangci-lint action, concurrency/timeout,
  single test pass, zenoh-c cache.
- **#92 Security/config** — payment payload redaction, 1 MiB body cap (413),
  CORS fix, strict env parsing, with tests.
- **#93 Registry gate** — `docs/registry.md` + permissive validator; the gate
  auto-runs stricter per-profile validators.
- **#94 Python baseline** — ruff + pytest for the shared bridge; fixed a real
  parser crash (non-object JSON raised `AttributeError`).
- **#95 Docs/front door** — `CONTRIBUTING.md`, README TOC and layout.

## Lessons learned

1. **Two robots, two PRs, two claims.** Keeping Spot (8 skills) and Go2
   (9 skills, obstacle navigation) as separate, separately-evidenced
   submissions is what makes either claim defensible.
2. **CI proof is part of the submission.** A green, GitHub-hosted run on the
   exact frozen SHA is worth more than prose.
3. **Settlement and execution must be correlated.** Pay only for what
   happened — `no-settle-on-failure` is a decision, not a nicety.
4. **Small, isolated platform PRs** build reviewer trust faster than one giant
   change.
