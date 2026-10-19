# CI Drill Log

This repository is a disposable playground for rehearsing an on-call runbook:
how to kill a stuck GitHub Actions job and start it over.

## Drill setup
- Workflow: `.github/workflows/hold-and-release.yml`
- Trigger: manual (`workflow_dispatch`)
- Job: `hold` — parks for five minutes via `sleep 300`

## Drill procedure
1. Dispatch `hold-and-release` manually, wait until the `park` step is genuinely
   executing on a runner (past the queue), then cancel the run mid-flight and
   confirm the conclusion is `cancelled`.
2. Re-run the same cancelled run from scratch (a fresh attempt of the existing
   run, not a new dispatch), confirm attempt 2 actually starts, then cancel it
   as well and confirm its final state.

## Paper trail
- A draft pull request against `main` carries this file and a comment
  summarizing the drill outcome.

## Result
See the PR comment for the final outcome of each stage.
