# Decisions

## 2026-10-20 — OpenRouter as the single API layer
One key, one bill, all models. Chosen over an all-in-one chat app because those apps replace Claude's connectors, memory and Claude Code instead of building on them.

## 2026-10-20 — GPT default pinned to `gpt-5.6-sol`
The original default `openai/gpt-5.6` is not a catalog slug; OpenRouter was silently routing it to `sol` (the priciest tier, $4 in / $20 out per M tokens). Pinned explicitly via `COUNCIL_GPT_MODEL` so a routing change can't swap the model. Revisit against `terra` ($2 / $12) or `luna` ($0.20 / $1.20) once the usage log shows real spend.