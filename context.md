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

## 2026-10-20 21:15 — model-council scrubbed, spend cap checked
- Done: Replaced the client names and personal paths in the `model-council` README examples with generic ones. Set its commit email to the GitHub noreply address and amended its single commit. All 6 smoke tests pass. Checked the OpenRouter key limit through the API.
- State: The key has a $100 cap with no reset, so it's lifetime, not monthly. About $0.01 spent so far. The `model-council` repo is committed locally but not on GitHub, because creating the repo needs the founder's approval.
- Next: Set the cap to reset monthly on openrouter.ai. Create and push the `model-council` GitHub repo. Run the first real `/council critique`.
