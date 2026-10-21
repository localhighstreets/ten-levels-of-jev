# Ten Levels of Jev

Jev decision examples and Pi integration experiments, maintained here as a LocalHighStreets copy of the project attributed to IndyDevDan.

## Completion and remaining work

Snapshot: **21 October 2026**.

| Measure | Status |
|---|---|
| Overall feature/release completion | **Not yet measurable** — no reconciled, acceptance-tested repository-wide baseline was established in this review |
| Tracked-work completion | **N/A** — no eligible GitHub issues in this repository |
| Open tracked work | 0 issues |
| Excluded closures | 0 cancelled/not-planned or unclassified closures |

The tracked percentage is `completed / (completed + open) × 100`, rounded to one decimal place. It counts repository GitHub issues equally; PRs and closures not marked `completed` are excluded. It is **not** a feature-completeness, effort, test-coverage or production-readiness percentage. Jira work, untracked requirements and upstream-project issues are outside this denominator. An empty tracker means unknown scope, not 100% completion.

### Remaining work and acceptance evidence

The following items identify implementation decisions, tracker reconciliation or validation still needed to establish completion; they are not all newly verified code defects.

- Define which examples and Pi/host integrations are in the intended adoption scope.
- Run the offline example tests and verify the selected live provider/host configurations separately.
- Evaluate guardrail false-positive/false-negative behaviour and deterministic enforcement requirements before relying on examples in an operational workflow.

### Tracked backlog

No open GitHub issues were returned for this repository at the snapshot date. Establish an owner-approved scope and acceptance checklist before assigning an overall percentage.

[Review the current issue tracker](https://github.com/localhighstreets/ten-levels-of-jev/issues?q=is%3Aissue). Reconcile old package scopes, route assumptions and duplicate/superseded tickets against current code before acting on them. Update this dated numerator/denominator and remaining-work list after acceptance changes.

## Contents

[apps/ten-levels](apps/ten-levels) contains the runner, examples and web lab. [justfile](justfile) defines the repository recipes.

| Levels | Example focus |
|---|---|
| 1–5 | Single decisions, multiple choice, scoring, confidence gating and routing |
| 6–7 | Agent guardrail hooks and compaction decisions |
| 8–10 | File questions, batches of files and agent-selected questions |

These are examples, not evidence that the LocalHighStreet agent estate uses them or that model decisions provide a complete security boundary.

## Local commands

Inspect [apps/ten-levels/package.json](apps/ten-levels/package.json) and the [justfile](justfile) before setup. The recipes use zsh, Node, npm and Bun. Some web-launch commands use macOS utilities.

```bash
cd apps/ten-levels/web
bun install
cd ../../..
just test
JEV_BACKEND=mock just jev1
```

`just test` delegates to the app's offline test command. The mock backend is selected by `JEV_BACKEND=mock`. Live recipes require provider credentials and may incur usage charges. Configure [.env.sample](.env.sample) for your environment. No current provider prices or latency guarantees are asserted here.

The `web` recipe builds the web app and serves the lab on port 4399. It also attempts to stop an existing listener on that port. Read the recipe before using it on a shared development machine.

The `install` recipe invokes Claude Code with a permission-skipping flag. It is not a generic installer for every agent host. Manual dependency setup is available through the app manifests.

## Safety and verification

Guardrail outcomes depend on the extension, model response, thresholds and host configuration. A probabilistic judgement is not proof that a command is safe. Review the code and tests for the specific example.

Reviewed against default-branch files on 21 October 2026. This review did not run offline tests, live Jev calls or Pi sessions. Historical example outputs and test totals are not current verification results.

## Attribution

Original walkthrough: [Ten Levels of Jev](https://youtu.be/_U-O5lYhJ7Q). See [LICENSE](LICENSE).
