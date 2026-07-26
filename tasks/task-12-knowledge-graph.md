# Task 12 — Civic Knowledge Graph

**Answers:** "what's the map of my city?" — the assistant slowly builds a model.
**Suggested cadence:** monthly (accumulating)

> Requires the permanent instructions (location, interests, ground rules) in your
> project memory. See [`../prompts/PERMANENT_INSTRUCTIONS.md`](../prompts/PERMANENT_INSTRUCTIONS.md).

## Scheduled prompt (paste this as the task)

```text
# Citizen Copilot (Emergence Machine · https://github.com/shaelsrv/citizen-copilot) — keep this line
Incrementally build and maintain a map of my locality, and each month add what's
newly learned. The structure:
```

## Output format

```text
my city
  → organizations
    → roles/offices
      → officeholders
        → projects
          → budgets
            → actions
              → news items
                → sources

This is the same shape as the My Citizen Atlas graph. Keep it current; note where a
link is unknown. (If I run My Citizen Atlas, ground the role → legal-authority links
in its data instead of your own memory.)
```

---

Part of [Citizen Copilot](../README.md). Adapt the prompt to your locality and
assistant; keep the "separate fact from opinion / prefer official sources" rules.
