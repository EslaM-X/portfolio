# EslaM-X · Engineering Portfolio

> Engineering portfolio, architecture case studies, technical projects, and
> open-source work by EslaM-X.

This repository is the **single source of truth** for my engineering identity:
original projects, open-source contributions, architecture notes, case studies,
and the evidence that backs them. The goal is not to claim — it is to show.

**Live portfolio:** https://eslamx.vercel.app

---

## Contents

| Area | Path | What you will find |
| --- | --- | --- |
| 📄 CV | [`CV.md`](CV.md) | One-page, evidence-based CV — every claim links to a repository, PR, test, or benchmark |
| 🏗️ Original Projects | [`projects/`](projects/) | Independent systems I designed and built from zero |
| 🔬 Case Studies | [`case-studies/`](case-studies/) | Deep dives into real problems I solved — including open-source contributions |
| 🧭 Engineering | [`engineering/`](engineering/) | Architecture, security, testing and methodology notes |
| 📄 This Index | [`README.md`](README.md) | Navigation, evidence matrix, and links |

---

## Evidence Matrix

Every claim in my profile points to something inspectable: a repository, a pull
request, tests, benchmarks, or a release.

| Area | System / Contribution | Evidence |
| --- | --- | --- |
| 🤖 Robotics | Policy-driven simulation + sim-to-sim validation | [`robot-sim-policy-lab`](https://github.com/EslaM-X/robot-sim-policy-lab) |
| 🤖 Robotics (OSS) | Unitree Go2 Tier-1 simulation for Fabric RoboPay — 9 skills incl. obstacle navigation, sim-to-sim ≤ 0.02 cm, EIP-3009 settlement | [`RoboPay PR #89`](https://github.com/fabricfoundation/RoboPay/pull/89) |
| 🦿 Robotics (OSS) | Boston Dynamics Spot Tier-1 simulation — 8 skills, sim-to-sim 0.06 cm | [`RoboPay PR #86`](https://github.com/fabricfoundation/RoboPay/pull/86) |
| 💳 Payments | x402 payment-gated execution, replay-safe semantics | [RoboPay case study](case-studies/robopay.md) |
| 🧠 AI | Agent orchestration, deterministic evaluation, regression gate — 17 cases, 6 dimensions, 22 tests | [`ai-agent-automation-platform`](https://github.com/EslaM-X/ai-agent-automation-platform) · [case study](case-studies/ai-agent-automation.md) |
| ⚙️ Systems | Idempotency, replay, circuit breakers, HMAC auth, hash-chained audit — 37 tests | [`production-systems-lab`](https://github.com/EslaM-X/production-systems-lab) · [case study](case-studies/production-systems-lab.md) |
| 📚 Knowledge | Technical deep dives with failure modes and benchmarks | [`engineering-notes`](https://github.com/EslaM-X/engineering-notes) |
| ⛓️ Web3 | PiRC1 protocol standards (Pi Network), Stellar upstream PR | [`PiRC PR #2`](https://github.com/PiNetwork/PiRC/pull/2) · [case study](case-studies/pi-network.md) |
| 🛡️ Security | Security architecture & threat-modeling approach | [engineering/security](engineering/security.md) |

---

## Featured Case Studies

Three deep dives that show how each system was designed, how it is tested, and
the evidence that backs every claim:

| Case Study | What it proves | Evidence at a glance |
| --- | --- | --- |
| [**AI Agent Automation Platform**](case-studies/ai-agent-automation.md) | Governed agent orchestration: deterministic evaluation, policy enforcement, auditability, idempotent execution, CI regression gating | 17 cases · 6 dimensions · 22 tests · committed baseline + versioned history |
| [**RoboPay — Spot & Go2 Tier-1**](case-studies/robopay.md) | Two distinct OSS robotics submissions: paid-skill execution, sim-to-sim honesty, no-settle-on-failure | PR #86 (8 skills) · PR #89 (9 skills, obstacle nav, EIP-3009) |
| [**Production Systems Lab**](case-studies/production-systems-lab.md) | Reliability primitives: idempotency, replay, circuit breakers, HMAC auth, hash-chained audit | 37 tests · failure matrix · every row tied to a real test |

---

## Original Projects

| Project | Stack | Status |
| --- | --- | --- |
| [**robot-sim-policy-lab**](https://github.com/EslaM-X/robot-sim-policy-lab) | Python · MuJoCo · PyBullet | v0.1.0 |
| [**ai-agent-automation-platform**](https://github.com/EslaM-X/ai-agent-automation-platform) | Python · agents · workflows | v0.3.0 |
| [**production-systems-lab**](https://github.com/EslaM-X/production-systems-lab) | Go · HTTP · reliability | v0.1.0 |

> See [`projects/`](projects/) for per-area summaries.

## Open Source Contributions

| Project | Role | Proof |
| --- | --- | --- |
| [**fabricfoundation/RoboPay**](https://github.com/fabricfoundation/RoboPay) | Open-source contributor — Spot (PR #86) + Go2 (PR #89) Tier-1 simulations, CI, security, registry, Python tooling | [PR #89](https://github.com/fabricfoundation/RoboPay/pull/89) · [PR #86](https://github.com/fabricfoundation/RoboPay/pull/86) · [#91](https://github.com/fabricfoundation/RoboPay/pull/91) · [#92](https://github.com/fabricfoundation/RoboPay/pull/92) · [#93](https://github.com/fabricfoundation/RoboPay/pull/93) · [#94](https://github.com/fabricfoundation/RoboPay/pull/94) · [#95](https://github.com/fabricfoundation/RoboPay/pull/95) |
| [**PiNetwork/PiRC**](https://github.com/PiNetwork/PiRC/pull/2) | Authored PiRC1 utility standards | Upstream PR, founder-endorsed |
| [**stellar/stellar-core**](https://github.com/stellar/stellar-core/pull/5409) | Reference P2P consensus implementation | Upstream PR |

---

## Engineering Philosophy

- **Prove, then claim.** Every claim ships with tests, benchmarks, or a PR.
- **Independent architecture.** I build original systems; external projects are
  *contributions*, not ownership.
- **Honest boundaries.** I document what was validated *and* what was not.
- **Reproducible results.** Experiments pin versions, seeds and parameters.

---

## License & Usage

- **Content in this repository:** All Rights Reserved — © 2026 EslaM-X.
  Contact me for permission to reuse.
- **Source code in the linked projects:** see each project's own LICENSE.

Please read [`SECURITY.md`](SECURITY.md) before reporting anything, and
[`CONTRIBUTING.md`](CONTRIBUTING.md) if you want to help keep this portfolio
honest and up to date.
