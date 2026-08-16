# Distribution & Adoption — EslaM-X

> **Purpose:** move the public engineering evidence from *visible* to *adopted*.
> Distribution puts each launchable artifact in front of the right audience;
> Adoption turns viewers into contributors, users, and opportunities.
> Every post below links to the same evidence graph — no new numbers, no
> unverifiable superlatives.

---

## The funnel

```
PUBLIC EVIDENCE
   │  (profile README → repos → PRs → tests → releases → GHCR package)
   ▼
DISTRIBUTION          Adoption metric
   ├─ Launch posts     → profile views, repo page visits, clones
   ├─ Release notes    → releases page, dependabot subscribers
   ├─ GitHub Discussions → questions, ideas, show-and-tell
   ▼
ADOPTION
   ├─ Contributors     → PRs merged, first-time contributors
   ├─ Users            → forks, issues opened, package pulls
   ├─ Signals          → followers, stars, followers→engagement
   ▼
MEASUREMENT            (see scripts/collect-metrics.js in the profile repo)
```

Each project has a **launch post** and a **measured baseline**. After a post
ships, compare the weekly metrics snapshot to the baseline and record the
delta in `metrics/`. Numbers in this folder are only ever *recorded* — never
predicted.

---

## Launch plan (ordered)

| Order | Artifact | Audience | Channel priority |
| --- | --- | --- | --- |
| 1 | **RoboPay Go2 Tier-1** (PR #89 + archive repo + GHCR image) | robotics / ML engineers, x402 builders | X (tech thread) → LinkedIn → Medium |
| 2 | **RoboPay Spot Tier-1** (PR #86 + archive repo) | robotics / sim engineers | X → LinkedIn → Medium |
| 3 | **RoboPay Robotics case study** | recruiters / hiring managers | LinkedIn (long-form) |
| 4 | **ai-agent-automation-platform** (v0.3.0) | AI / agent engineers | X → LinkedIn → Medium |
| 5 | **production-systems-lab** (v0.1.0) | backend / reliability engineers | LinkedIn → X |
| 6 | **Portfolio re-launch** | everyone | LinkedIn + all channels |

Full post copy lives in [`posts/`](posts/). Each file has: hook, body,
links used, and the exact evidence each claim maps to.

---

## Contributor on-ramp (already live)

Both RoboPay archive repos ship a complete contributor funnel:

- `CONTRIBUTING.md` — first-contribution path in 6 steps
- `CODE_OF_CONDUCT.md`, `SECURITY.md`
- Issue templates (`bug`, `feature`), `config.yml`, PR template
- `CODEOWNERS`, `dependabot.yml`, discussion welcome template
- Labels: `good first issue`, `good first contribution`, `help wanted`

Flagship repos (`ai-agent-automation-platform`, `robot-sim-policy-lab`,
`production-systems-lab`, `engineering-notes`) already carry the same funnel.

### Good first issue seeding

Open 2–3 genuinely small, well-scoped issues per robotics repo, tagged
`good first contribution`, e.g.:

- Go2: *"Add a `back_up` skill with the same joint-space controller + test"*
  (mirrors an existing skill; full template in the registry).
- Go2: *"Render an obstacle-course trace SVG from `obstacle_nav_report.json`"*
  (docs-only, no physics).
- Spot: *"Extend the README skill table with the measured `stop` latency"*
  (docs-only).

Keep them honest: each must be completable with the repo's own test command.

---

## Measurement

The profile repo's `update-profile-assets` workflow now appends a **daily
metrics snapshot** to `profile-data/metrics-history.json`:

```json
{ "date": "2026-08-16", "repos": {
    "robopay-go2-tier1": { "stars": 1, "forks": 0, "views": 12, "clones": 4 },
    "...": "..."
}}
```

`scripts/collect-metrics.js` fetches stars, forks, views, and clones for the
adoption-tracking repos (unauth traffic metrics are GitHub's own, 14-day
window) and appends one row per day. The file is committed automatically.

### Reading the funnel weekly

1. Open `profile-data/metrics-history.json` (profile repo) or the
   `assets/metrics.svg` chart.
2. Compare **views vs clones** per repo — views are discovery, clones are intent.
3. Compare **contributors / PRs** opened since the last launch post.
4. Record the delta in this folder's `metrics/` log (append-only).

> GitHub only exposes traffic data for the last 14 days — snapshot daily and
> store locally, or the window slides away.

---

## Golden rules

- **Every number is measured, never invented** — a launch post states what a
  test or report proves, nothing more.
- **RoboPay = external OSS** — always labelled as a contribution to
  fabricfoundation/RoboPay, with the authorship archive as the proof of work.
- **Release notes are real** — tags correspond to actual releases with real
  CI results.
- **No deletion, no inflating** — if a repo has 1 star, the post does not
  claim adoption; it invites review instead.
