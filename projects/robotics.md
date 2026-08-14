# Robotics & Simulation

Independent work on policy-driven robot simulation, physics validation, and
simulator-to-simulator testing.

## Featured

### [robot-sim-policy-lab](https://github.com/EslaM-X/robot-sim-policy-lab)

A policy-driven robotics simulation lab with a clean separation between
**policy → planner → controller → simulator → metrics → validation**.

- MuJoCo and PyBullet backends behind one simulator interface
- Task-conditioned local planner with obstacle avoidance
- Collision detection and contact logging
- Deterministic metrics: success rate, collision rate, path length, clearance,
  completion time
- Reproducible experiments (pinned versions, seeds, parameter files)
- Sim-to-sim validation comparing behaviour across simulators

**Design principle:** policies are task-conditioned and measurable — every run
produces a machine-readable report, not a screenshot.

## Open-Source

### [RoboPay — Fabric Foundation](https://github.com/fabricfoundation/RoboPay)

Unitree Go2 Tier-1 simulation contribution (see
[case study](../case-studies/robopay.md)).

- Policy/controller-driven action execution (wave, sit, stand, bow, nod,
  turn_to_face, hold, navigate_obstacle + `stop` fail-safe)
- MuJoCo → PyBullet sim-to-sim with measured deviation
- x402 payment-gated execution with no-settle-on-failure semantics
- Live EIP-3009 settlement evidence on Base Sepolia

## Principles

1. **The numbers speak.** Success/collision/clearance rates are reported from
   runs, not estimated.
2. **Honest boundaries.** Document what was validated and what was not.
3. **Reproducible.** Seeds, versions, and parameters are pinned.
