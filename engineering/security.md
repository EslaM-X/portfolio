# Security Notes

Security is a design constraint, applied at every layer.

## Threat-model first

Before writing code, answer:

1. **Who attacks?** Script kiddie, competitor, insider, state actor.
2. **What do they want?** Money, reputation damage, data, sabotage.
3. **What is the blast radius of each flaw?** Can one leak be catastrophic?

Design decisions (rate limits, redaction, approval gates) should trace back to
an entry in this model.

## API security checklist

- **AuthN:** verify identity at every entry point; never trust headers alone.
- **AuthZ:** check permissions per-resource, not per-route.
- **Rate limiting:** protect abuse-sensitive endpoints (payments, auth, webhooks).
- **Validation:** reject early and loudly; strict parsing over guessing.
- **Secrets:** never in code, never in logs, injected via env/secret manager.
- **Redaction:** payment payloads and tokens are masked before logging.

## Payment-grade semantics

- **Idempotency keys** so retries cannot double-settle.
- **Replay protection** so captured requests cannot be replayed.
- **No-settle-on-failure:** settlement decision is correlated with execution
  result.

## Verification

- Automated security tests run in CI (auth, authz, rate limit, redaction).
- Adversarial review before release, not after incident.
- Honest documentation of residual risk.

## See also

- [`production-systems-lab`](https://github.com/EslaM-X/production-systems-lab) —
  working implementations of these primitives.
- [Case study: RoboPay](../case-studies/robopay.md) — payment security in the
  wild.
