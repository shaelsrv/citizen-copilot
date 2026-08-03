# The 16 tasks

Each task is a **single-responsibility scheduled prompt**. You don't need all 16 —
run the ones that matter to you. Each file in this folder is a ready-to-paste
prompt; the permanent instructions ([`../prompts/PERMANENT_INSTRUCTIONS.md`](../prompts/PERMANENT_INSTRUCTIONS.md))
supply your location, interests, and rules, so the task prompts stay short.

**Start here (highest value for a new user):** Task 1, Task 4, Task 10, and Task 16 (Economy Watch).

| # | Task | Answers | Suggested cadence |
|---|---|---|---|
| 1 | [Weekly News](task-01-weekly-news.md) | "What happened?" | weekly |
| 2 | [Accountability Tracker](task-02-accountability-tracker.md) | "What promises are still open?" | weekly |
| 3 | [Trend Watch](task-03-trend-watch.md) | "What is changing?" | weekly |
| 4 | [Upcoming Decisions](task-04-upcoming-decisions.md) | "What can I still weigh in on?" | weekly |
| 5 | [My Personal Notes](task-05-personal-notes.md) | "What did I think at the time?" (private) | weekly |
| 6 | [Follow-up Tracker](task-06-followup-tracker.md) | "What happened after…?" | weekly |
| 7 | [Emerging Issues](task-07-emerging-issues.md) | "What's quietly getting worse?" | weekly |
| 8 | [Positive Developments](task-08-positive-developments.md) | "What's going right?" | weekly |
| 9 | [Institutional Memory](task-09-institutional-memory.md) | "Who's in charge now, and what changed?" | weekly |
| 10 | [Why This Matters](task-10-why-this-matters.md) | "Why should I care about this?" | weekly |
| 11 | [Cross Connections](task-11-cross-connections.md) | "How do these events connect?" | biweekly |
| 12 | [Civic Knowledge Graph](task-12-knowledge-graph.md) | "What's the map of the government that acts on me?" (all levels) | monthly (accumulating) |
| 13 | [Questions to Research](task-13-questions-to-research.md) | "What's worth a closer look?" | weekly |
| 14 | [Compare Over Time](task-14-compare-over-time.md) | "How does now compare to before?" | monthly |
| 15 | [Personal Civic Profile](task-15-civic-profile.md) | "What do I actually prioritize?" | quarterly |
| 16 | [Economy Watch](task-16-economy-watch.md) | "How is the economy I live in doing?" | monthly |

## How they fit together

- Tasks **1, 4, 8, 9** are the *observation* layer — what happened, what's coming,
  what's going right, who's in charge.
- Tasks **2, 6, 10, 13** are the *accountability* layer — open promises, follow-ups,
  why it matters, what to question.
- Tasks **3, 7, 11, 14, 16** are the *systems* layer — trends, emerging drift,
  cross-connections, comparison over time, and the economy you live in. This is
  where slow change gets caught.
- Tasks **5, 12, 15** are the *memory* layer — your private notes, the accumulating
  knowledge graph, and your evolving civic profile.

## The unifying capability: trace the chain of responsibility

The permanent instructions ask the assistant, for every significant event, to
resolve:

```
event → organization → role → officeholder → legal authority →
        budget → project → prior decisions → expected consequences
```

Several tasks lean on this directly (2, 9, 10, 12). If you also run the sibling
[My Citizen Atlas](https://github.com/shaelsrv/mycitizenatlas) map, you can
ground the *role → legal authority* links in the actual constitution and statutes
rather than the model's memory.
