# EslaM HeshAM — Systems & Protocol Engineer

**Lead Technical Architect** · Web3 · Cyber Security · Robotics & AI Agents
Cairo, Egypt 🇪🇬 · Remote Worldwide
**Portfolio:** [eslamx.vercel.app](https://eslamx.vercel.app) · **GitHub:** [github.com/EslaM-X](https://github.com/EslaM-X) · **LinkedIn:** [in/eslam-hesham](https://www.linkedin.com/in/eslam-hesham-359964192)

---

## Summary

Systems and protocol engineer focused on **governed, auditable, provable
systems**: AI agent orchestration, policy-driven robotics, payment/API
reliability, and Web3 security. Every claim below links to a public
repository, a PR, a test, or a benchmark you can open and check — no
estimated numbers.

---

## Engineering Evidence

### AI Agent Orchestration — [ai-agent-automation-platform](https://github.com/EslaM-X/ai-agent-automation-platform)

Built a **policy-driven AI agent orchestration platform** with a deterministic
evaluation harness covering **17 scenario cases across 6 dimensions**
(correctness, policy, safety, execution, auditability, idempotency), backed by
a CI **regression gate** and a committed reproducible benchmark baseline
(current engineering state **v0.3.0**; latest release **v0.2.0**).
Evidence: [evaluation harness](https://github.com/EslaM-X/ai-agent-automation-platform/tree/main/evaluation) ·
[benchmark history](https://github.com/EslaM-X/ai-agent-automation-platform/tree/main/benchmarks/history) ·
[22 offline tests](https://github.com/EslaM-X/ai-agent-automation-platform/tree/main/tests) ·
[CI](https://github.com/EslaM-X/ai-agent-automation-platform/actions)

### Production Reliability (Go) — [production-systems-lab](https://github.com/EslaM-X/production-systems-lab)

Engineered **payment-grade reliability primitives**: idempotency, replay
protection, circuit breakers, HMAC auth, rate limiting, hash-chained audit,
webhook security — **37 tests across 9 packages**, every failure mode mapped
in a [failure matrix](https://github.com/EslaM-X/production-systems-lab/blob/main/docs/failure-matrix.md)
to the test that proves it (release **v0.1.0**).
Evidence: [`go test ./...`](https://github.com/EslaM-X/production-systems-lab) ·
[failure matrix](https://github.com/EslaM-X/production-systems-lab/blob/main/docs/failure-matrix.md)

### Policy-Driven Robotics — [robot-sim-policy-lab](https://github.com/EslaM-X/robot-sim-policy-lab)

Built policy → planner → controller → simulator pipelines with **3 physics
backends** (MuJoCo, PyBullet, kinematic) and measurable **sim-to-sim**
validation: **0.26 m max deviation** across engines, **18 tests**, reproducible
experiments (release **v0.1.0**).
Evidence: [validation report](https://github.com/EslaM-X/robot-sim-policy-lab/blob/main/docs/validation.md) ·
[README metrics](https://github.com/EslaM-X/robot-sim-policy-lab#readme)

### Machine-Payable Robotics (External OSS) — [fabricfoundation/RoboPay](https://github.com/fabricfoundation/RoboPay)

Contributed two separately-evidenced Tier-1 robot profiles with paid-skill
execution, sim-to-sim honesty, and on-chain settlement:

- **Boston Dynamics Spot — [PR #86](https://github.com/fabricfoundation/RoboPay/pull/86):**
  8 paid skills, MuJoCo ⇄ PyBullet agree to **0.06 cm**, 6 failure paths.
- **Unitree Go2 — [PR #89](https://github.com/fabricfoundation/RoboPay/pull/89):**
  9 skills incl. obstacle navigation, sim-to-sim **≤ 0.02 cm**, Webots runtime,
  **3 real EIP-3009 USDC settlements on Base Sepolia**.

---

## Web3 & Protocol Engineering

- **Pi Network — PiRC1:** authored utility standards (escrow lock proofs,
  dynamic `p_floor`, engagement-weighted PiPower, Sybil-resistant reporting);
  reviewed by Pi Network founder ([PR #2](https://github.com/PiNetwork/PiRC/pull/2)).
- **Stellar:** contribution to the reference P2P consensus implementation
  ([PR #5409](https://github.com/stellar/stellar-core/pull/5409)).
- Smart-contract auditing (Foundry, invariant testing), consensus research.

---

## Enterprise Experience

- **Lead Technical Architect @ Map of Pi** — high-scale MERN architecture, AI
  integration, security layers.
- **Business Operations Manager @ S.I.G / Steinheim** — designed the ERP,
  invoicing and audit systems running in production today.
- **MapCap IPO platform** — TypeScript · Node · MongoDB, IPO workflow tooling.

*(Enterprise systems live in private repositories — available on request.)*

---

## Core Stack

TypeScript · React · Next.js · Node.js · Go · Python · Solidity · MuJoCo ·
PyBullet · Docker · MongoDB · PostgreSQL · GitHub Actions

## Engineering Method

Architecture decisions are documented as **ADRs** and engineering analysis as
problem-first notes with failure modes and benchmarks —
[engineering-notes](https://github.com/EslaM-X/engineering-notes) (release
**v1.0.0**): [5 notes](https://github.com/EslaM-X/engineering-notes/tree/main/notes) ·
[5 ADRs](https://github.com/EslaM-X/engineering-notes/tree/main/docs/adr).
