# Launch Post — ai-agent-automation-platform (v0.3.0)

> Channel: **X (thread)** → **LinkedIn** → **Medium**.
> Timing: after the robotics pair — AI agents are the second-largest audience.
> Goal: developers evaluating agent frameworks try the evaluation harness.

---

## X thread (9 tweets)

1. 🧠 I open-sourced my **policy-driven AI agent platform** — agents that
   cannot act until a human policy approves. Current release: **v0.3.0**.

2. The difference: execution is **human-gated and fully audited**. Agents
   propose, a policy decides, and every run lands in an append-only audit log.

3. 🧪 The part I care most about: a **deterministic evaluation harness**.
   17 scenario cases scored across 6 dimensions, with a committed baseline and
   a CI regression gate — no "trust me, it works."

4. Benchmarks are versioned: `benchmarks/history/` keeps a reproducible
   baseline so a change either improves or fails the gate.

5. 🔌 Clean seams: `Provider`, `ToolPolicy`, `RetryPolicy`, `Evaluator`,
   `AuditLog` — plug in your own LLM without touching the core.

6. 🧯 Reliability built in: idempotency and replay protection on agent runs
   (the same discipline as my payment-grade Go work).

7. ✅ Fully offline-testable: the test suite runs with a **fake provider**,
   no keys, no network. CI is green.

8. 📦 Repo: [github.com/EslaM-X/ai-agent-automation-platform](https://github.com/EslaM-X/ai-agent-automation-platform)
   — docs, evaluation cases, baseline, demo in 60 seconds.

9. Built for teams that need governed AI in production. Reviews welcome —
   `good first issue` labels are open. 🧵/end

---

## LinkedIn post

**"Governed AI agents: human-gated, audited, and proven by 17 evaluation
cases."**

Most agent frameworks optimise for autonomy. This one optimises for
*governance*: agents execute only within policy, every run is audited, and
quality is enforced by a deterministic evaluation harness — 17 scenario cases,
6 scored dimensions, a committed baseline, and a CI regression gate that
rejects regressions.

Built the way I build payment rails: idempotent, replay-safe, and
offline-testable. `v0.3.0` is public:
[github.com/EslaM-X/ai-agent-automation-platform](https://github.com/EslaM-X/ai-agent-automation-platform)

---

## Medium draft

**Title:** *Human-Gated AI Agents: Evaluation as a Feature, Not an
Afterthought*

Cover: the governance problem, the policy decision boundary, the evaluation
harness design (17 cases, 6 dimensions, baseline, regression gate), the seams
that keep it provider-agnostic, and the reliability primitives. Reuse the
numbers verbatim from the repo's README/benchmarks.

**Links used:** repo, `evaluation/cases/`, `benchmarks/baseline.json`,
`benchmarks/history/`, case study in portfolio.
