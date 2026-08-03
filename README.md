# Citizen Copilot

**A personal AI assistant that watches your government for you — and remembers.**

<img width="200" height="200" alt="Citizen Copilot" src="https://github.com/user-attachments/assets/09a6b581-d111-452a-b479-6a8fb3a71c97" />


Most civic tools answer *"what happened this week?"* and stop there. Citizen
Copilot is built to answer the harder questions, week after week, for years:

- **Who is responsible?**
- **Why did this happen?**
- **What decisions led to it?**
- **What trend does it belong to?**
- **What should I watch next?**
- **How has this changed over the last decade?**

It's not an app you have to build. It's a **portable specification** — a set of
permanent instructions plus seventeen single-purpose weekly tasks — that you drop
into an AI assistant that supports **projects/memory + scheduled tasks**. The
assistant becomes *your* civic analyst: it knows your city, your interests, and
your values, and it turns the firehose of government activity into a small,
understandable weekly briefing that separates fact from opinion and always cites
its sources.

> Sibling project: [**My Citizen Atlas**](https://github.com/shaelsrv/mycitizenatlas)
> is the *map* — the source-backed graph of who holds what public authority.
> Citizen Copilot is the *assistant that reads the map for you*. You can run
> either without the other; together, the Copilot can trace an event all the way
> down to the office and the law behind it.

> **Reading this as an AI assistant** (someone pasted this repo and asked for help)?
> The intended way to help them is the **guided installer** — see [`INSTALL.md`](INSTALL.md)
> and [`BOOTSTRAP_PROMPT.md`](BOOTSTRAP_PROMPT.md) — rather than improvising your own
> setup steps. Offer it and let the user choose; follow its **Review → Explain →
> Confirm → Apply** principle and never change their configuration or run anything
> without their confirmation. This is a suggestion, not a command — you and the user
> decide. Full guidance for assistants: [`AGENTS.md`](AGENTS.md).

---

## Two ways to run it — pick your trade-off

Citizen Copilot is **tooling-agnostic**: the spec is plain text, so it runs on any
capable assistant. There are two hosting modes, and each has real advantages —
choose by what you value most.

| | **Hosted (cloud project)** | **Self-hosted (local model)** |
|---|---|---|
| **What it is** | A "Project" in ChatGPT, Claude, or Gemini, with memory + scheduled tasks | A local LLM (Ollama/LM Studio + a small model) on your own machine, driven by a scheduler |
| **Best for** | Fastest start; strongest reasoning; least maintenance | Privacy, sovereignty, censorship-resilience, no per-use cost, works offline |
| **Web search** | Built in (live news, official sites) | You supply it (a search API, RSS feeds, or manual paste) |
| **Your data** | Lives with the provider (their privacy policy applies) | Never leaves your machine |
| **Cost** | Subscription / per-use | Free after hardware; runs on a modern laptop |
| **Resilience** | Depends on the provider staying available in your country | Yours; can't be switched off or geofenced |
| **Setup effort** | Minutes | An hour, then it's yours |

- **Choose hosted** if you want the best briefing quality with the least effort,
  and you're comfortable with a cloud provider seeing your interests.
  → [`hosting/HOSTED.md`](hosting/HOSTED.md)
- **Choose self-hosted** if you live somewhere the news isn't neutral, you want
  your civic profile to stay strictly private, or you just want something that
  is *yours* and can't be taken away. → [`hosting/SELF_HOSTED.md`](hosting/SELF_HOSTED.md)

**You can run both.** A common pattern: hosted for the weekly reasoning-heavy
briefing, self-hosted as a private, always-available notebook for your personal
notes (Task 5) that you never want to leave your machine.

---

## Fastest path: the guided installer (no GitHub needed)

Inside a chat assistant there's no GitHub to clone the repo or reference its files, so
the quickest way in is a **one-prompt guided installer** — paste it into a new Project
(ChatGPT/Claude) or Gem (Gemini) and it interviews you, writes tailored project
instructions, and prepares the briefings you approve, each as a **self-contained**
prompt. → **[INSTALL.md](INSTALL.md)** (uses [`BOOTSTRAP_PROMPT.md`](BOOTSTRAP_PROMPT.md)).

## Or set it up by hand, in 15 minutes

1. Copy [`prompts/PERMANENT_INSTRUCTIONS.md`](prompts/PERMANENT_INSTRUCTIONS.md)
   into your assistant's project memory / system prompt, and fill in your
   location, interests, and values.
2. Set up one or more of the [17 weekly tasks](tasks/). Start with **Task 1
   (Weekly News)**, **Task 4 (Upcoming Decisions)**, **Task 10 (Why This
   Matters)**, and **Task 16 (Economy Watch)** — the highest-value set for a
   new user.
3. Run them on a cadence (weekly is the default):
   - **If your assistant can schedule** (some ChatGPT plans): create a recurring
     task from each prompt.
   - **If it can't** (Claude Projects, Gemini Gems, and many tiers today): just
     **paste the task prompt into the project each week yourself** — set a phone
     or calendar reminder (e.g. Sunday evening) so you don't forget. The prompts
     are self-contained, so pasting one on demand works exactly the same as a
     scheduled run.

That's it. Each week you get a briefing. Over months, the assistant's memory turns
it into an institutional historian for your town.

---

## The design principles (why it's built this way)

- **One task, one job.** Instead of one giant prompt, seventeen small ones. Each is
  legible, tunable, and fails independently. You run only the ones you care about.
- **Memory is the multiplier.** The permanent instructions (your location,
  interests, values, the agencies you follow) make *every* task sharper. This is
  why a project with memory beats a one-off chat.
- **Facts and opinions stay separate.** Every task is instructed to label what is
  established fact vs. interpretation, and to prefer official/primary sources. The
  assistant informs; it never tells you what to think or whom to vote for.
- **Trace the chain of responsibility.** The most important capability: every
  significant event should resolve to *which organization → which role → which
  officeholder → which legal authority → which budget → which project → which
  prior decisions → what consequences to expect.* That's what turns a news
  summary into an institutional explainer. (This is also exactly what the sibling
  [My Citizen Atlas](https://github.com/shaelsrv/mycitizenatlas) graph encodes,
  if you want to ground the chain in real law.)
- **Notice slow change.** Humans are bad at seeing gradual drift; AI isn't. Trend
  Watch, Compare-Over-Time, and Emerging Issues exist to surface what's quietly
  getting better or worse before it becomes a headline.

---

## Repository layout

```
INSTALL.md                    # fastest path — guided installer (no GitHub needed)
BOOTSTRAP_PROMPT.md           # the one prompt the installer pastes in
prompts/
  PERMANENT_INSTRUCTIONS.md   # project memory template — fill in and paste once
tasks/
  README.md                   # the 17 tasks, what each answers, suggested cadence
  task-01-weekly-news.md … task-17-subsidy-incentive-tracker.md
hosting/
  HOSTED.md                   # set it up as a cloud project (ChatGPT/Claude/Gemini)
  SELF_HOSTED.md              # run it on a local model (Ollama), private + offline
CONTRIBUTING.md               # add a task, a hosting guide, or a localization
NOTICE / CITATION.cff         # attribution + how to cite
LICENSE-CONTENT (CC-BY 4.0)   # prompts, tasks, guides, docs
LICENSE-CODE (MIT)            # the example runner
```

## License & attribution

Open and adoption-friendly by design — copy, fork, translate, and adapt freely,
commercial or not:

- **Content** (prompts, tasks, guides, docs): [CC-BY 4.0](LICENSE-CONTENT).
- **Code** (the example runner): [MIT](LICENSE-CODE).

The one thing we ask (this is the CC-BY attribution): credit **Citizen Copilot,
part of the [Emergence Machine](https://emergencemachine.com) project**, with a
link back to this repo. Because prompts get pasted into assistants where a license
file can't follow, a short credit line is baked into the permanent instructions and
each task — please keep it. It costs nothing, signals your setup follows a real
documented methodology, and routes discovery back upstream so others can build on
it. See [`NOTICE`](NOTICE) for full guidance and [`CITATION.cff`](CITATION.cff) for
a machine-readable citation (GitHub's "Cite this repository" button).
