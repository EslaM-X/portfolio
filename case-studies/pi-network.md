# Case Study — PiRC1: Protocol Standards for the Pi Network

> **Role:** Author / contributor
> **Repository:** [`PiNetwork/PiRC`](https://github.com/PiNetwork/PiRC)
> **Contribution:** [PR #2](https://github.com/PiNetwork/PiRC/pull/2)

## Problem

Decentralized ecosystems need **utility standards** that align incentives
against gaming: escrow can be abused, floor prices can be manipulated, power
can be concentrated, and reports can be sybil-flooded.

## What was proposed

Authored PiRC1 utility standards covering:

- **Escrow lock proofs** — verifiable proof that value is committed before
  promises are trusted.
- **Dynamic `p_floor`** — a floor that adapts rather than a static constant.
- **Engagement-weighted PiPower** — influence weighted by real engagement, not
  by token count alone.
- **Sybil-resistant reporting** — designs that make fake identities expensive.

## Outcome

Reviewed by Dr. Nicolas Kokkalis, founder of Pi Network:

> *"Both of these are good ideas. Implementation seems possible."*

## Lessons learned

1. **Standards die on incentive analysis.** Every rule must survive a rational
   attacker.
2. **Grounding matters.** Founder review is a form of validation that code
   reviews cannot replace.
3. **Protocol work is documentation + proof.** Clear spec text is the product.
