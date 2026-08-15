# Case Study — Production Systems Lab

> **Role:** Author / architect
> **Repository:** [`production-systems-lab`](https://github.com/EslaM-X/production-systems-lab)
> **Evidence:** [failure matrix](https://github.com/EslaM-X/production-systems-lab/blob/main/docs/failure-matrix.md) ·
> `go test ./...`

## Problem

Money is the harshest test of distributed systems. Two failure modes are
**guaranteed** under retries and are unacceptable in any payment rail:

1. **Double settlement** — a client times out, retries, and the server applies
   the same charge twice.
2. **Replay** — an attacker captures a valid request and re-sends it later to
   trigger a settlement the client never authorised.

A third problem is subtler: even with correct behaviour, **you must be able to
prove it**. If the audit trail can be edited, every "we never double-charged"
claim is unverifiable. This is the class of risk RoboPay settlement work runs
into — and why this lab exists: each defence is a small, dependency-free,
individually testable Go package.

## Architecture — reliability primitives

```
Request (idempotency_key, payload, nonce, timestamp)
   │
   ▼
Idempotency   — first write wins; retries get the stored result
   ▼
Replay guard  — reject old timestamps and duplicate nonces
   ▼
Circuit breaker — stop hammering a dead dependency
   ▼
Write + append-only audit entry (hash-chained)
```

Packages: `idempotency`, `replay`, `retry`, `circuitbreaker`, `auth` (HMAC
keys with rotation), `ratelimit` (token bucket), `validation` (Luhn, amounts),
`audit` (hash-chained), `webhook` (HMAC-SHA256 signing).

## Failure matrix

`docs/failure-matrix.md` maps every real-world failure to the control that
implements it and the **unit test that proves it** — `Failure → Control →
Evidence`. Rows exist only because the code and the test exist; no speculative
defences, no claimed mechanisms without evidence:

| Failure | Defence |
| --- | --- |
| Client retries after timeout | Idempotency: retry returns stored result |
| Key reused for a different payload | Idempotency: `ErrConflict` |
| Attacker replays a captured request later | Replay: time window + nonce registry |
| Stream of failures on a dead dependency | Circuit breaker trips |
| Analyst edits an audit entry after the fact | Audit: hash chain breaks, `Verify()` fails |
| Leaked key | Auth: rotation via key id |
| Burst overload / API abuse | Rate limit: token bucket |
| Forged webhook event | Webhook: HMAC signature verification |

## Validation

- **37 unit tests** across 9 packages, each testing its own failure mode plus
  the happy path — `go test ./...` green.
- `go test -bench=Benchmark -benchmem ./benchmarks` — rate-limiter and
  circuit-breaker benchmarks.
- Every defence is verified in isolation: the storage is behind an interface,
  so the swap to Postgres/Redis in production is one implementation, not a
  redesign.

## Evidence

- `reliability/idempotency` — first-write-wins + payload-hash conflict.
- `reliability/replay` — nonce + timestamp window.
- `observability/audit` — append-only, hash-chained, `Verify()`.
- `docs/failure-matrix.md` — every row tied to a real test.
- ADR-0003 / ADR-0004 in [`engineering-notes`](https://github.com/EslaM-X/engineering-notes)
  record the decisions behind this design.

## Lessons learned

1. **Idempotency is a correctness feature, not a retry feature.** Design it
   before the retry logic exists.
2. **Trust nothing in the client.** A request may be re-sent by the network, a
   retry, or an attacker — the server cannot tell the difference and does not
   need to.
3. **"It happened exactly once" is a claim about records, not memory.** If you
   cannot prove it from an un-editable trail, you do not know it happened.
