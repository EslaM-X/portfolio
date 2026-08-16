# Launch Post — production-systems-lab (v0.1.0)

> Channel: **LinkedIn** → **X**.
> Timing: backend/reliability audience — pairs with the AI-agent post
> (same reliability discipline).
> Goal: engineers who ship payment/API services adopt the primitives.

---

## LinkedIn post

**"Payment-grade Go primitives — proven by 37 tests, mapped in a failure
matrix."**

The systems that can't fail quietly — payment rails, webhooks, audit logs —
deserve more than best-effort. I open-sourced a Go lab of reliability
primitives built for exactly those systems:

- **Idempotency** — retried requests don't double-execute.
- **Replay protection** — replayed messages are rejected, not reprocessed.
- **Circuit breakers** — failing dependencies fail fast and recover cleanly.
- **HMAC-signed APIs** — requests are authenticated and tamper-evident.
- **Hash-chained audit** — a tamper-proof append-only record, provably
  unchanged since append.

**37 tests** across **9 packages**, with a **failure matrix** that maps every
failure mode to its defence. `v0.1.0`:
[github.com/EslaM-X/production-systems-lab](https://github.com/EslaM-X/production-systems-lab)

This is the same discipline I bring to production systems as a Technical
Architect.

---

## X thread (7 tweets)

1. ⚙️ Payment-grade reliability, open-sourced: a Go lab of idempotency,
   replay, circuit-breakers, HMAC auth, and hash-chained audit. **37 tests.**

2. Idempotency: the same request retried 10x produces one effect. Replay: a
   replayed event is rejected, not reprocessed.

3. Circuit breakers: when a dependency degrades, fail fast and recover
   cleanly — no silent retry storms.

4. 🔐 HMAC-signed APIs: requests authenticated and tamper-evident. Audit log:
   **hash-chained**, so post-hoc tampering is detectable by design.

5. 🗺️ A **failure matrix** maps every failure mode to its defence — that's the
   doc every production system deserves.

6. ✅ 37 tests, 9 packages, CI green. Repo:
   [github.com/EslaM-X/production-systems-lab](https://github.com/EslaM-X/production-systems-lab)

7. Built for the systems that can't fail quietly. Reviews welcome. 🧵/end

---

## Medium draft

**Title:** *Designing for the Systems That Can't Fail Quietly*

Cover idempotency/replay/breaker/HMAC/audit each with the failure it prevents,
the failure matrix as a design tool, and the test discipline (37 tests).
Reuse numbers verbatim from the repo.

**Links used:** repo, `reliability/`, `docs/failure-matrix.md`, case study.
