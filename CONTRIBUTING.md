# Contributing to AEGIS

How the three of us work on this repo. Read this once before your first PR.

## Who owns what

| Member | Area | Folders |
|---|---|---|
| M1 Md. Rafiqul Islam | Systems | `aegis/proxy/`, `aegis/core/`, `demo/` |
| M2 Syeda Safia Akhter | Benchmark | `bench/`, `baselines/`, `eval/` |
| M3 S. M. Mahin | Models | `aegis/models/`, `training/` |
| All three | Shared formats | `aegis/schemas/` |

- Work inside your own folders. If you need a change in someone else's folder, open a PR and let the owner review it.
- `aegis/schemas/` is the contract between all parts. Changing it needs approval from all three, because it can break everyone's code.
- `.github/CODEOWNERS` adds the right reviewer to your PR automatically.

## Branches

- Never push directly to `main`.
- Make a branch per task: `<name>/<task>`, for example `rafiqul/proxy-recorder`, `safia/mock-payment`, `mahin/infiller-lora`.
- Keep branches short-lived. Pull `main` often: `git pull origin main`.

## Pull requests

A PR can be merged when:

1. CI is green (lint and tests pass).
2. At least one other member approved it.
3. The PR template checklist is filled in.

Keep PRs small, one task each. Use "Squash and merge".

## Commit messages

- Short, present tense, says what changed: `Add gap detector`, `Fix ledger read in state reader`.
- One logical change per commit.
- Plain messages only: no footers, no co-author lines.

## Code

- Python 3.11 or newer (3.12 recommended; CI tests both). Install with `pip install -e ".[dev]"`.
- Before pushing, run:
  ```bash
  ruff check .
  ruff format .
  pytest
  ```
- Add tests in `tests/<your-area>/` for new code.
- Keep tests fast. CI does not have a GPU, so tests must not train or load large models.

## Data and models

- Never commit datasets or model weights. Put them in `data/` (ignored by git) or on Kaggle / Hugging Face Hub.
- Commit the script that downloads or builds them instead.

## Project rules from the design

- The model only suggests; plain code decides every action. No code path may let a model output trigger a tool call without the decision gate.
- State readers use read-only tools only.
- Only mock services and made-up data. No real payments, real emails or personal information, anywhere.
- Design documents are in `docs/`. If code and design disagree, raise it with the team before changing either.
