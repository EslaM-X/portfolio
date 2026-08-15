# Case Study — AI Agent Automation Platform

> **Role:** Author / architect
> **Repository:** [`ai-agent-automation-platform`](https://github.com/EslaM-X/ai-agent-automation-platform)
> **Evidence:** [evaluation harness](https://github.com/EslaM-X/ai-agent-automation-platform/tree/main/evaluation) ·
> [benchmark history](https://github.com/EslaM-X/ai-agent-automation-platform/tree/main/benchmarks)

## Problem

Most agent systems are `User → LLM → Answer`: impressive when it works,
unprovable when it matters. An agent that acts on a company's data must prove
four things before anyone should trust it: it did what it was asked, it did
**not** do what it was forbidden, it left a tamper-evident record, and a
re-run produces the same result. None of that is provable with a prompt and a
chat window.

The goal was a governed agent orchestration system whose behaviour is
**deterministic, auditable, and gated** — not a demo, but a platform with
enforced policy and reproducible evidence.

## Architecture

```
Trigger → Planning → Tool Selection → Execution → Validation
        → Human Approval → Final Action → Audit Log
```

- **Planner + specialised agents** (research, content, QA, analytics) instead
  of one monolithic model call.
- **Approval gate** before irreversible actions — an explicit human loop, not
  an assumption.
- **Policy layer** with deny-by-default tool permissions (`ToolPolicy`).
- **Retry policy** distinguishing transient from permanent failure, with
  bounded exponential backoff.
- **Idempotent runs + checkpoint-based resume** — a retry or a restart never
  redoes completed work.
- **Audit log** recording every decision and action.

## Evaluation harness

The system ships with a deterministic, offline evaluation harness
(`evaluation/runner.py`) that drives the **real Orchestrator** — no LLM, no
network, no mocked engine:

- **17 scenario cases** across approval, basic tasks, failure recovery, and
  idempotency.
- **6 dimensions** checked per case: correctness, policy, safety, execution,
  auditability, idempotency.
- **Regression gate**: `python -m evaluation.runner --gate` compares every
  case and dimension rate against the committed baseline and fails CI on any
  regression.
- **Committed baseline + history**: `benchmarks/baseline.json` (17/17 pass,
  all 6 dimensions at 1.0) plus `benchmarks/history/` — one snapshot per
  released version, so a regression is provable against the previous release
  instead of being a claim.

## Evidence

- `evaluation/runner.py` — deterministic runner + `--gate` regression gate.
- `benchmarks/baseline.json` — committed baseline, 17 cases, 6 dimensions.
- `benchmarks/history/0.3.0.json` — v0.3.0 snapshot: commit `0ba5ce4`,
  49 executions, deterministic hash, gate `pass`.
- `.github/workflows/ci.yml` — gate runs on every push/PR.
- `tests/` — 22 unit tests; CI green.

## Lessons learned

1. **Determinism is the precondition for proof.** If a run can't be repeated
   byte-for-byte, "it passed" is not a claim you can defend.
2. **Gate the baseline, not the mood.** The committed baseline turns
   "performance improved" from marketing into a measurable regression check.
3. **Structure beats prompts.** A planner over specialised agents with an
   approval gate is auditable in a way a single LLM call never is.
