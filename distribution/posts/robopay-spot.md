# Launch Post — RoboPay Spot Tier-1 (PR #86)

> Channel: **X (short thread)** → **LinkedIn**.
> Timing: same window as the Go2 launch (paired narrative — same bounty, two
> robots).
> Goal: show the same evidence discipline on a second platform.

---

## X thread (8 tweets)

1. 🦾 Same contract, second robot: the **Boston Dynamics Spot** Tier-1
   submission to the @fabricfoundation RoboPay bounty — 8 priced skills,
   paid actions, settle-on-success.

2. Skills: wave, sit, stand, stop, bow, nod, turn_to_face, hold — every one a
   real joint-space trajectory with body-weight compensation on the official
   `mujoco_menagerie` Spot model.

3. Measured, not claimed: paw lift 0.212 m, sit depth 0.133 m, stand 0.435 m,
   bow 16.9°, hold stable at 0.434 m, home-stance return after every skill.

4. 💸 Same x402 gate: unpaid ⇒ 402, replay ⇒ 409, tampered params ⇒
   `INVALID_PARAMS`, **settle only on `status: success`**.

5. 🔁 Sim-to-sim: the same joint configs recomputed in PyBullet — agreement
   committed as a report, worst case 0.06 cm.

6. ✅ Reproducible: tests run offline, deterministic physics, no keys.

7. 📦 PR #86, with the authorship archive at
   [github.com/EslaM-X/robopay-spot-tier1](https://github.com/EslaM-X/robopay-spot-tier1).

8. Two robots, one standard: evidence over claims. Go2
   ([PR #89](https://github.com/fabricfoundation/RoboPay/pull/89)) and Spot
   ([PR #86](https://github.com/fabricfoundation/RoboPay/pull/86)) — reviews
   welcome. 🧵/end

---

## LinkedIn post

**"A second machine-payable robot: the Spot profile."**

My Spot Tier-1 submission to
[fabricfoundation/RoboPay](https://github.com/fabricfoundation/RoboPay) — 8
priced skills (wave, sit, stand, stop, bow, nod, turn_to_face, hold) on the
official MuJoCo Spot model, with the same contract discipline as my Go2 work:
a paid action triggers a real, measured skill episode; the x402 gate blocks
unpaid, replayed, or tampered actions; settlement happens **only on success**;
and the same joint configs agree in PyBullet sim-to-sim (worst case 0.06 cm).

Authorship archive:
[github.com/EslaM-X/robopay-spot-tier1](https://github.com/EslaM-X/robopay-spot-tier1)

---

## Medium draft

**Title:** *Two Robots, One Standard: The Spot & Go2 Paid-Robotics Profiles*

Companion piece to the Go2 post — the Spot profile as the "second data point"
that the approach generalises: same gate, same settle-on-success semantics,
same sim-to-sim discipline, different platform. Ends on the common evidence
standard.

**Links used:** PR #86, archive repo, sim2sim report, spot.gif.
