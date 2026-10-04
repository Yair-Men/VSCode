# ruff CLI sweep config
 
A standalone [ruff](https://docs.astral.sh/ruff/) config for checking an **entire
codebase** from the command line, independent of the target project's own
`pyproject.toml` / `ruff.toml` and of any VSCode settings. Use it to confirm a
repo is clean (lint + format) without touching any files.
 
## Check an entire codebase (read-only - no changes written)
 
Point the last argument at the code to scan:
 
```bash
# Lint
uvx ruff --config /PATH/TO/RUFF-SWEEP.TOML check /PATH/TO/PROJECT

# Format (reports files that differ; does NOT rewrite them)
uvx ruff --config /PATH/TO/RUFF-SWEEP.TOML format --check /PATH/TO/PROJECT
 ```
Both exit `0` and print nothing when the codebase is clean. Add `--diff` to the `--config` makes ruff use **only** this file and skip auto-discovery, so results don't depend on the target project's config or your editor.
 
## Applying fixes (optional)
 
```bash
uvx ruff --config /PATH/TO/RUFF-SWEEP.TOML check --fix /PATH/TO/PROJECT
uvx ruff --config /PATH/TO/RUFF-SWEEP.TOML format /PATH/TO/PROJECT
```
 
## Notes
 
- `*.md` is excluded on purpose: ruff reformats Python code blocks inside
  Markdown, which would rewrite documentation. Remove that line to include docs.
- No `src` is set, so first-party import detection (rule `I`) uses defaults. If
  imports get misclassified, add `src = ["."]` (or your source dir).
- Adjust `target-version` to match the Python version of the project you scan.
