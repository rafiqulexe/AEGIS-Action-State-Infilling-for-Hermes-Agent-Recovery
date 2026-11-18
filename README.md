# AEGIS

Action-State Infilling for Hermes Agent Recovery

CSE499 capstone project, Group 6, Fall 2026, North South University.
Supervisor: Dr. Mohammad Ashrafuzzaman Khan

## What is this

AI agents can crash in the middle of a task. After restart the agent often does not know if its last action went through or not, so it may repeat it (e.g. charge a customer twice) or skip it.

AEGIS is a layer that sits between the agent and its tools. After a crash it guesses what could have happened, checks those guesses against the real data, and then either continues safely or asks a person.

## How it works

1. Record every tool call the agent makes
2. After a crash, find where the log stopped and read the current state
3. A fine-tuned model suggests possible histories for the missing part
4. Keep only the histories that are likely enough
5. Act if the action is safe for all of them, otherwise ask a human

## Folder structure

```
aegis/schemas/   shared JSON formats: trace event, world state, history
aegis/proxy/     MCP proxy and trace recorder
aegis/core/      gap detector, state reader, history set, decision gate
aegis/models/    infiller and scorer, prompts
bench/           CrashBench: mock tools, crash injector, task templates
baselines/       simple methods we compare against
training/        LoRA training scripts and notebooks
eval/            metrics and experiments
demo/            demo dashboard
tests/           tests for every part
docs/            proposal and design documents
```

## Setup

```bash
python -m venv .venv
pip install -e ".[dev]"
pytest
```

See [CONTRIBUTING.md](CONTRIBUTING.md) for how we work as a team.

## Status

Work in progress. Currently setting up the project.
