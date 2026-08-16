# Adoption Metrics Log

Append-only log of measured launch results. Baselines come from
`profile-data/metrics-history.json` (profile repo). Record **after the fact** —
never predict.

| Date | Event | Repo | Baseline (views/clones/stars) | After (views/clones/stars) | Delta | Note |
| --- | --- | --- | --- | --- | --- | --- |
| — | (seed) | robopay-go2-tier1 | 0 / 0 / 0 | — | — | Launch posts not yet shipped |

## How to record

1. Snapshot the repo's numbers *before* posting (stars/forks/views/clones from
   `metrics-history.json`).
2. Post.
3. 7 days later, snapshot again.
4. Add a row above; leave the numbers as GitHub reported them.

## What moves the funnel

- **views** = discovery (did the post reach people?)
- **clones** = intent (did they try it?)
- **stars / forks** = public adoption signal
- **PRs / issues** = contributor adoption
