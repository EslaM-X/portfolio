# Security Engineering

Defensive and offensive-minded engineering: threat modeling, secure APIs,
zero-trust design, and verification.

## Areas

- **API security** — authentication, authorization, rate limiting, input
  validation, request signing, secret handling.
- **Payment security** — x402 / EIP-3009 flows, replay protection, idempotency,
  no-settle-on-failure semantics.
- **Threat modeling** — adversarial review of systems before and after build.
- **CI/CD security** — least-privilege permissions, pinned actions, secret
  hygiene.
- **Digital forensics & malware research** — detection and analysis.

## Featured

### [production-systems-lab](https://github.com/EslaM-X/production-systems-lab)

A laboratory of production reliability and security primitives:

- Idempotency and replay protection
- Rate limiting
- Circuit breakers and retries with backoff
- AuthN / AuthZ, audit logging, secure configuration
- Webhook signature verification

## Principles

1. **Assume breach.** Design so one leak is not a total compromise.
2. **Verify, don't trust.** Zero-trust is a default, not a feature.
3. **Secrets never in code or logs.** Redaction is tested, not promised.
