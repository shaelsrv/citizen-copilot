# Task 12 — Civic Knowledge Graph

**Answers:** "what's the map of the government that acts on me?" — the assistant
slowly builds a model, at every level.
**Suggested cadence:** monthly (accumulating)

> Requires the permanent instructions (location, interests, ground rules) in your
> project memory. See [`../prompts/PERMANENT_INSTRUCTIONS.md`](../prompts/PERMANENT_INSTRUCTIONS.md).

## Scheduled prompt (paste this as the task)

```text
Incrementally build and maintain a map of ALL the government that acts on me —
local (city/county), state/province, AND national/federal — and each month add
what's newly learned. Root the map at me and branch out by level. The structure:
```

## Output format

```text
me
  → level (local / state / national)
    → organizations
      → roles/offices
        → officeholders
          → projects
            → budgets
              → actions
                → news items
                  → sources

Cover all three levels — don't stop at the city. This is the same shape as the My
Citizen Atlas graph. Keep it current; note where a link is unknown. (If I run My
Citizen Atlas, ground the role → legal-authority links in its data instead of your
own memory.)
```

---

Part of [Citizen Copilot](../README.md). Adapt the prompt to your locality and
assistant; keep the "separate fact from opinion / prefer official sources" rules.
