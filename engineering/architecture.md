# Architecture Notes

How I structure systems. These are working principles distilled from building
robotics, payments, web, and enterprise systems.

## Layered, testable cores

Every serious system gets a **core that has no I/O**:

```
policy (pure) → controller (pure) → simulator interface → adapter (I/O)
```

Pure cores are unit-testable without hardware, network, or databases. Adapters
are thin and swappable. This is the same pattern behind the RoboPay Go2
simulation: the policy and metrics layer is physics-agnostic; MuJoCo and
PyBullet are just backends.

## Contracts over concreteness

Define the **interface first**, then implement. Examples:

- `Simulator` interface → MuJoCo / PyBullet backends
- `Agent` interface → research / content / QA agents
- `Store` interface → in-memory / Postgres / Redis implementations

Swapping an implementation is a small change when the contract is good; it is a
rewrite when it is not.

## Data flow over file layout

Documents flow, not directories: `input → validate → transform → persist →
notify → audit`. If I cannot draw the flow in one diagram, the design is not
ready.

## See also

- [Methodology](methodology.md) — how I run and verify work.
- [Testing](testing.md) — what "tested" means here.
- [Security](security.md) — threat-model-first design.
