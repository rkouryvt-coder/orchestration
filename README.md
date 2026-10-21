# AI Tools Orchestration

Make Claude, ChatGPT, Grok and Kimi work together as one system instead of four separate subscriptions, with Claude as the hub.

## Roles

| Model | Role | Use for |
|---|---|---|
| **Claude** | Hub | Daily driver. Holds connectors (Gmail, M365, Drive, Slack, Strava), memory, projects and Claude Code. Final deliverables live here. |
| **Grok** | Scout | Real-time public sentiment and current events, especially anything on X. |
| **ChatGPT** | Generalist | Second opinion, voice mode, image generation. |
| **Kimi** | Bulk reader and contrarian | Very long documents, broad research sweeps, a view from outside the US labs. |

## Working patterns

1. **Scout, build, attack:** Grok and Kimi gather, Claude builds, the others critique, Claude finalizes.
2. **Blind parallel answers:** for high-stakes calls, ask all four the same question and focus on where they disagree.
3. **Automated orchestration:** Claude Code calls the other models directly through one API layer (OpenRouter).

## Model Council

The MCP server lives in its own repo (`model-council`), registered user-scoped so it works in every Claude Code project.

| Tool | What it does |
|---|---|
| `ask` | One model, one prompt (`gpt`, `grok`, `kimi`, or any OpenRouter slug), optional web search |
| `council` | All three in parallel, `answer` or `critique` mode, tolerates a failed member |
| `list_models` | Live OpenRouter catalog with pricing |
| `/council` | Slash command: consensus, disagreements, unique insights, Claude's view, recommendation |

**Current defaults:** `openai/gpt-5.6-sol`, `x-ai/grok-4.6`, `moonshotai/kimi-k3`

**Usage and cost log:** `usage.jsonl` in the Model Council data folder (local only)

## Status

- [x] Model Council MCP server built, smoke tests pass
- [x] OpenRouter key created and registered (user scope)
- [x] Live verification: `ask`, `council`, `list_models` all working (2026-10-20)
- [x] GPT default pinned to `gpt-5.6-sol`
- [x] Spend cap set on the OpenRouter key: $100 total (2026-10-20)
- [ ] Switch the cap to reset monthly (openrouter.ai → Keys → edit limit → reset: monthly)
- [x] `model-council` scrubbed and committed, smoke tests pass
- [ ] Push the `model-council` repo to GitHub
- [ ] First real use: `/council critique` on a real deck or exec summary
- [ ] After a few months, review the usage log and decide which app subscriptions (Kimi, Grok, ChatGPT) are still worth keeping

## Guardrails

- Keep client-confidential material out of council prompts unless it's cleared for OpenAI, xAI and Moonshot.
- API usage is billed separately from the app subscriptions.
- Grok's API search is not the same as the live X feed in the Grok app.
- The API key lives only in the user-level Claude Code config, as the MCP server's env. Never commit it to this repo or the server repo.

## Layout

- `decisions.md` — decisions made and why
- `council/` — saved `/council` outputs worth keeping (one file per run, `YYYY-MM-DD-topic.md`)
