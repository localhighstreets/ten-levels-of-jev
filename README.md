# Ten Levels of Jev

Jev decision examples and Pi integration experiments, maintained here as a LocalHighStreets copy of the project attributed to IndyDevDan.

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
