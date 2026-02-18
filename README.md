# Codex Cartographer

<img width="640" height="360" alt="codex-cartographer" src="https://github.com/user-attachments/assets/542818c6-fc2b-41a6-915d-cf196447f346" />

A Codex skill that maps and documents codebases of any size using parallel subagents.

## Repository Layout

- `skills/cartographer/SKILL.md`
- `skills/cartographer/scripts/scan-codebase.py`

## Installation

Install by copying the `skills` folder into your user-level Codex skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
rsync -a skills/ "${CODEX_HOME:-$HOME/.codex}/skills/"
```

## Usage

In Codex, ask:

- `map this codebase`
- `cartographer`
- `create codebase map`

## What It Does

Cartographer analyzes your codebase in parallel and synthesizes results into:

- `docs/CODEBASE_MAP.md` with architecture, module purposes, dependencies, and navigation guides
- `AGENTS.md` summary updates (and `CLAUDE.md` if present)

## How It Works

1. Scans the repository and estimates token counts per file.
2. Splits files into balanced analysis groups.
3. Spawns parallel `gpt-5.3-codex-spark` subagents to analyze file groups.
4. Synthesizes subagent outputs into a single map document.

## Requirements

- Python 3.9+
- `tiktoken` (installed automatically when using `uv run`, or manually via `pip install tiktoken`)

## Skill Details

See `skills/cartographer/SKILL.md` for the full workflow and operational details.
