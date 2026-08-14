# Case Study — Systems Engineering: Enterprise Ops Tooling

> **Role:** Lead Technical Architect / builder
> **Context:** S.I.G / Steinheim — Office of the CEO & Board; MapCap IPO
> platform; invoice, ERP, stock-flow, and audit systems.

## Problem

Operational businesses run on paper and spreadsheets until the friction becomes
the product: invoices get lost, stock goes out of sync, audit trails are
hand-maintained, and reporting arrives late.

The need was not "a dashboard" — it was **trustworthy operations tooling**:
audit-proof, deterministic, and usable by non-engineers.

## Architecture

- **MapCap IPO platform** — TypeScript · Node · MongoDB; frontend + backend for
  IPO workflows.
- **Steinheim ERP / Invoicing / Audit** — enterprise-grade accounting-grade
  flows, in production today (private repositories).
- **Stock-flow systems** — inventory movement tracked as immutable events.

## Implementation highlights

- Every financial record carries an **audit trail** — who, what, when, why.
- Idempotent operation handling to survive retries without double entry.
- Role-based access so the board sees everything, and clerks see their scope.

## Lessons learned

1. **Audit trails are a feature, not an afterthought.** Regulators and boards
   ask "who changed this?" — the system must answer instantly.
2. **ERP success is process-first.** The tool follows the workflow; it does not
   invent one.
3. **Production trust is earned by correctness.** One silent double-entry
   destroys more goodwill than ten feature gaps.
