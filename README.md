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
| 🤖 Robotics (OSS) | Unitree Go2 Tier-1 simulation for Fabric RoboPay | [`RoboPay PR #89`](https://github.com/fabricfoundation/RoboPay/pull/89) |
| 💳 Payments | x402 payment-gated execution, replay-safe semantics | [RoboPay case study](case-studies/robopay.md) |
| 🧠 AI | Agent orchestration, workflow automation, approvals, observability | [`ai-agent-automation-platform`](https://github.com/EslaM-X/ai-agent-automation-platform) |
| ⚙️ Systems | Idempotency, rate limiting, circuit breaking, secure APIs | [`production-systems-lab`](https://github.com/EslaM-X/production-systems-lab) |
| 📚 Knowledge | Technical deep dives with failure modes and benchmarks | [`engineering-notes`](https://github.com/EslaM-X/engineering-notes) |
| ⛓️ Web3 | PiRC1 protocol standards (Pi Network), Stellar upstream PR | [`PiRC PR #2`](https://github.com/PiNetwork/PiRC/pull/2) · [case study](case-studies/pi-network.md) |
| 🛡️ Security | Security architecture & threat-modeling approach | [engineering/security](engineering/security.md) |

---

## Original Projects

| Project | Stack | Status |
| --- | --- | --- |
| [**robot-sim-policy-lab**](https://github.com/EslaM-X/robot-sim-policy-lab) | Python · MuJoCo · PyBullet | v0.1.0 |
| [**ai-agent-automation-platform**](https://github.com/EslaM-X/ai-agent-automation-platform) | Python · agents · workflows | v0.2.0 |
| [**production-systems-lab**](https://github.com/EslaM-X/production-systems-lab) | Go · HTTP · reliability | v0.1.0 |

> See [`projects/`](projects/) for per-area summaries.

## Open Source Contributions

| Project | Role | Proof |
| --- | --- | --- |
| [**fabricfoundation/RoboPay**](https://github.com/fabricfoundation/RoboPay) | Open-source contributor — Go2 Tier-1 simulation, CI, security, registry, Python tooling | [PR #89](https://github.com/fabricfoundation/RoboPay/pull/89) · [#91](https://github.com/fabricfoundation/RoboPay/pull/91) · [#92](https://github.com/fabricfoundation/RoboPay/pull/92) · [#93](https://github.com/fabricfoundation/RoboPay/pull/93) · [#94](https://github.com/fabricfoundation/RoboPay/pull/94) · [#95](https://github.com/fabricfoundation/RoboPay/pull/95) |
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
