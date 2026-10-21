# AGENTS.md: AI Tools Orchestration

Instructions for any AI agent (Claude Code, Codex, Gemini) working in this repo.

## What this project is

Planning and operations home for running Claude, ChatGPT, Grok and Kimi as one system, with Claude as the hub. See [README.md](README.md) for roles and working patterns. This repo holds docs only. The code lives in a separate repo, the Model Council MCP server (`model-council`).

## Files

| File | Purpose | How to edit |
|---|---|---|
| `README.md` | Plan, roles, status checklist | Keep the Status checklist current |
| `decisions.md` | Decisions and their reasons | Add new entries at the bottom, dated `## YYYY-MM-DD — title` |
| `context.md` | Running session log | **Append only.** See below |
| `council/` | Saved `/council` outputs (gitignored, local only) | One file per run: `YYYY-MM-DD-topic.md` |

## context.md: append every session

At the end of every working session, and after any meaningful change, append one entry to `context.md`:

```
## YYYY-MM-DD HH:MM — short title
- Done: what changed (with file paths)
- State: anything now true that wasn't before
- Next: open items
```

Never rewrite or delete earlier entries. If something in an old entry turns out wrong, add a correction in a new entry. Read the last few entries at the start of a session to pick up where work left off.

## Secrets (hard rules)

- The OpenRouter key lives **only** in the user-level Claude Code config, as the Model Council MCP env. Never write it into any file in this repo or `model-council`, and never into a council output or log.
- Refer to it as `$OPENROUTER_API_KEY`.
- Both repos have a `.gitignore` covering `.env*`, `*.key`, `*.pem`, `secrets*` and `.claude/settings.local.json`. Both also have a `pre-commit` hook in `.git/hooks/` that blocks commits containing OpenRouter, OpenAI, Anthropic or xAI keys. Don't bypass it with `--no-verify`.
- Before any push, run `grep -rIlE "sk-or-v1-[A-Za-z0-9]{20,}" .` and confirm it prints nothing.

## Council usage

- Keep client-confidential material out of council prompts unless it's cleared for OpenAI, xAI and Moonshot.
- Every call costs money. Spend is logged locally in the Model Council `usage.jsonl`.
- Change default models through `COUNCIL_*_MODEL` env vars on the MCP registration, not by editing code, and record the change in `decisions.md`.
