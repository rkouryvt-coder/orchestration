# Context log

Append-only running log of work on this project. Newest entries at the bottom. Format rules are in [AGENTS.md](AGENTS.md).

## 2026-10-20 20:45 — Model Council built and verified
- Done: Built the Model Council MCP server (`ask`, `council`, `list_models`, `/council`) in its own `model-council` repo. Registered it user-scoped with an OpenRouter key. Live-tested all three tools end to end.
- State: Defaults are `openai/gpt-5.6-sol`, `x-ai/grok-4.6`, `moonshotai/kimi-k3`. GPT is pinned explicitly (see `decisions.md`).

## 2026-10-20 20:53 — Orchestration repo scaffolded
- Done: Created `README.md`, `decisions.md`, `council/` and `.gitignore`.

## 2026-10-20 21:00 — Secret protection and agent docs
- Done: Added secret patterns to both repos' `.gitignore` files. Installed a key-blocking `pre-commit` hook in both repos and tested it (a fake key was blocked, a clean commit passed). Added `AGENTS.md`, `context.md`, and a `CLAUDE.md` that imports `AGENTS.md`.
- State: The hooks live in `.git/hooks/`, which git doesn't track, so a fresh clone needs them reinstalled.

## 2026-10-20 21:05 — First commit and push
- Done: Widened `.gitignore` to cover `council/*` (except `.gitkeep`), `.claude/`, editor folders, `node_modules/`, `*.tmp` and `*.jsonl`. Removed personal paths and work context from the docs before the first public push.
- State: Council outputs stay local because they may contain client material.
- Next: Confirm the OpenRouter spend cap. Push the `model-council` repo. Run the first real `/council critique`.
