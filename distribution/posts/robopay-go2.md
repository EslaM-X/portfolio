# Launch Post — RoboPay Go2 Tier-1 (PR #89)

> Channel: **X (tech thread, primary)** → **LinkedIn** → **Medium**.
> Timing: after the Docker image tag `v1.0.1` is verified live.
> Goal: robotics engineers click → clone → run `verify_go2_tier1.sh`.

---

## X thread (12–14 tweets, ~280 chars each)

1. 🦾 Machines paying machines: I built a **paid-robotics profile for the
   Unitree Go2** — 9 priced skills, runnable today in MuJoCo + PyBullet + Webots.

2. The gist: a paid action arrives on a Zenoh topic → payment gate validates →
   the Go2 runs the skill on the *official* model → **settles only on
   success**. Never on failure.

3. Every skill is a real joint-space PD trajectory with body-weight
   compensation — not a replay, not a built-in demo. Measured: paw lift
   0.167 m, sit depth 0.145 m, bow 18.8°, hold stable at 0.283 m.

4. 🧭 Navigation is the hard part: `navigate_obstacle` steers a slow diagonal
   trot through an obstacle course with a **potential-field planner** and
   physics-detected contacts.

5. Result: 3/3 waypoints, **0 obstacle contacts**, min clearance 0.047 m,
   final goal distance 0.099 m — honest numbers, committed as JSON + SVG.

6. 🔁 Sim-to-sim: the same joint configs recomputed in PyBullet from a URDF
   generated from the *same* `go2.xml`. Foot positions agree to **≤ 0.02 cm**
   worst case (MuJoCo ⇄ PyBullet).

7. 💸 The payment rail is real: **3 live `transferWithAuthorization`
   transactions settled 1.0 USDC each on Base Sepolia** (EIP-3009), funded
   from free faucets, with a **no-settle-on-failure** proof on-chain.

8. ⚠️ Safety semantics that matter: unpaid ⇒ 402 + `PAYMENT-REQUIRED`; forged/
   expired receipts ⇒ 402; replay ⇒ 409; tampered params ⇒ `INVALID_PARAMS`.
   Durable replay keys survive a store restart.

9. ✅ One command reproduces everything:
   `bash simulation/verify_go2_tier1.sh` — every acceptance test, exit nonzero
   on failure. Under 30 minutes from a clean checkout.

10. 🐳 It also ships as a public container image:
    `ghcr.io/eslam-x/robopay-go2-tier1:latest` — `docker run` and verify.

11. 📦 This is PR #89 to @fabricfoundation RoboPay. The repo is an
    **authorship archive** of the submitted work — timestamped, tagged,
    independent of any fork.

12. Full archive: [github.com/EslaM-X/robopay-go2-tier1](https://github.com/EslaM-X/robopay-go2-tier1)
    · PR: [fabricfoundation/RoboPay/pull/89](https://github.com/fabricfoundation/RoboPay/pull/89)
    · video: `simulation/docs/go2.gif`.

13. If you build machine-payable robotics, I'd love a review. `good first
    issue` labels are open — contribute a skill or docs.

14. Evidence, not claims: every number above links to a test, a report, or a
    transaction. 🧵/end

---

## LinkedIn post

**"Machines paying machines — a Go2 that takes paid actions and settles on-chain."**

The exciting part of machine-payable robotics isn't the demo — it's the
*contract*. For my Tier-1 submission to the RoboPay bounty I built a Unitree
Go2 profile where:

- a **paid action** arrives over Zenoh and triggers a real, measured skill
  episode on the official MuJoCo model (9 skills: wave, sit, stand, stop,
  bow, nod, turn_to_face, hold, navigate_obstacle);
- the **x402 gate** blocks unpaid/forged/replayed/tampered actions (402/409/
  INVALID_PARAMS) and settles **only on success**;
- the same joint configs run in PyBullet and agree to **≤ 0.02 cm**;
- **three real EIP-3009 USDC settlements landed on Base Sepolia**, plus a
  proven no-settle-on-failure path.

Everything is reproducible: `bash simulation/verify_go2_tier1.sh` runs the
full acceptance suite, and a public container image ships the whole
environment. This is a contribution to
[fabricfoundation/RoboPay](https://github.com/fabricfoundation/RoboPay) — the
authorship archive lives at
[github.com/EslaM-X/robopay-go2-tier1](https://github.com/EslaM-X/robopay-go2-tier1).

Evidence, not claims — every number links to a test, report, or transaction.
Open to reviews and collaborators.

---

## Medium draft

**Title:** *Machines Paying Machines: Building a Paid Robotics Profile for the
Unitree Go2*

**Opening line:** "The hardest part of machine-payable robotics is not the
controller. It's the promise that the machine only moves when it's paid — and
only settles when the work actually happened."

Then: the chain (paid action → gate → skill → metrics → settle-on-success),
the 9-skill table with measured values, the navigation results, the sim-to-sim
agreement, the live Base Sepolia settlements, the safety semantics, and the
reproducibility story (one command + container image). End with the
authorship archive + invitation to contribute.

**Links used:** PR #89, archive repo, `simulation/docs/go2.gif`,
obstacle course SVG, settlement proofs, GHCR image.
