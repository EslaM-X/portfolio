# Launch Post — RoboPay Robotics Case Study

> Channel: **LinkedIn (long-form)** → Medium.
> Timing: after the two robot launch threads land (the case study *reuses*
> their momentum for recruiters / hiring managers).
> Goal: translate the robotics work into a career signal.

---

## LinkedIn long-form post

**"How I prove a robot did its job — and got paid for it."**

Robotics demos are everywhere. What's rare is the *audit trail*: how do you
know a paid action actually happened, and that the machine never moved unless
it was paid for?

For the RoboPay bounty (fabricfoundation), I built two machine-payable robot
profiles with that trail baked in:

**Unitree Go2 (Tier-1, PR #89)**
- 9 priced skills — including `navigate_obstacle`, a potential-field
  navigation run on the official model: 3/3 waypoints, 0 obstacle contacts,
  final goal distance 0.099 m.
- Sim-to-sim across MuJoCo ⇄ PyBullet to **≤ 0.02 cm** agreement.
- **3 live EIP-3009 USDC settlements on Base Sepolia**, plus a proven
  no-settle-on-failure path.
- One command reproduces the whole suite; the environment ships as a public
  container image.

**Boston Dynamics Spot (Tier-1, PR #86)**
- 8 priced skills, same gate semantics, sim-to-sim agreement to **0.06 cm**.

**Why I publish it this way:** every number in these posts is a link — to a
test, a report, a transaction, or a repo. "We could do this" is not my
standard; "here is the proof it works" is.

Both submissions are external OSS contributions to
[fabricfoundation/RoboPay](https://github.com/fabricfoundation/RoboPay). The
authorship archives are timestamped and tagged:
[Go2](https://github.com/EslaM-X/robopay-go2-tier1) ·
[Spot](https://github.com/EslaM-X/robopay-spot-tier1).

I'm a Technical Architect focused on reliable AI, robotics, distributed
systems, and Web3 security — open to Technical Architect / Engineering Lead
opportunities, remote worldwide.

---

## Why this post exists

| Post | Audience | Converts to |
| --- | --- | --- |
| Go2/Spot X threads | engineers | clones, reviews, contributions |
| This case study | recruiters / hiring managers | profile views, interviews |
