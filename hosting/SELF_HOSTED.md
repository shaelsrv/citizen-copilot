# Self-hosted Citizen Copilot (local model, private + offline)

Run your Copilot on a model **on your own machine**. Nothing about your location,
interests, notes, or civic profile ever leaves your computer. No subscription, no
per-use cost, and — the reason this matters most — **it can't be geofenced,
throttled, or switched off** by a provider or a government. This is the
censorship-resilient option.

The trade-off: a small local model reasons less well than a frontier cloud model,
and you supply your own web access. This guide makes both manageable.

---

## What you need

- A computer with **≥ 8 GB RAM** (16 GB comfortable). A GPU helps but isn't
  required; modern laptops run 7–8B models on CPU at a usable speed for a weekly
  batch job.
- **[Ollama](https://ollama.com)** (simplest) or **[LM Studio](https://lmstudio.ai)**
  (GUI). Both are free and cross-platform.
- A scheduler you already have: `cron` (Linux/macOS) or Task Scheduler (Windows).
- **Optional but recommended:** a way to fetch current information (see
  [Giving it the news](#giving-it-the-news)). Without it, the model reasons only
  from what you paste in — still useful, but not live.

---

## 1. Install a model

```bash
# install Ollama from https://ollama.com, then pull a capable small model:
ollama pull qwen2.5:7b          # strong general reasoning, good instruction-following
# alternatives:
#   ollama pull llama3.1:8b     # solid all-rounder
#   ollama pull gemma2:9b       # a step up if you have the RAM
#   ollama pull llama3.2:3b     # tiny/fast for weak hardware (lower quality)

ollama run qwen2.5:7b "Say hello in one sentence."   # sanity check
```

Ollama serves an OpenAI-compatible API at `http://localhost:11434/v1` — any tool
that speaks the OpenAI format can drive it.

> **Model choice rule of thumb:** pick the **largest** model your RAM allows for
> the analysis tasks (they need reasoning), and you can drop to a tiny model for
> mechanical steps. This mirrors the sibling project's discipline: *strong model
> where the output matters, cheap model where it's disposable.*

## 2. Load your permanent instructions

A local model has no "project memory," so you supply the context every run. Keep
[`../prompts/PERMANENT_INSTRUCTIONS.md`](../prompts/PERMANENT_INSTRUCTIONS.md)
(filled in) as a file, and prepend it to every task. Persist memory yourself as
plain files the model reads and rewrites:

```
copilot/
  system.md            # your filled-in permanent instructions
  memory/
    promises.md        # Task 2 ledger
    institutions.md    # Task 9 record
    trends.md          # Task 3/14 series
    notes.private.md   # Task 5 — never leaves your disk
    graph.md           # Task 12 knowledge graph
  tasks/               # the 17 prompts
  reports/             # dated outputs
```

The pattern for a run: **read `system.md` + the relevant memory file + the task
prompt → send to the model → append the result to `reports/` and update the memory
file.** Files *are* the memory. This is also what makes it auditable and portable.

## 3. A minimal runner (stdlib + Ollama)

```python
# run_task.py  —  python run_task.py tasks/task-01-weekly-news.md
import sys, json, urllib.request, datetime, pathlib

def ask(prompt, model="qwen2.5:7b"):
    body = json.dumps({"model": model, "stream": False,
        "messages": [{"role": "user", "content": prompt}]}).encode()
    req = urllib.request.Request("http://localhost:11434/v1/chat/completions",
        data=body, headers={"Content-Type": "application/json"})
    with urllib.request.urlopen(req, timeout=600) as r:
        return json.load(r)["choices"][0]["message"]["content"]

system = pathlib.Path("copilot/system.md").read_text(encoding="utf-8")
task   = pathlib.Path(sys.argv[1]).read_text(encoding="utf-8")
context = ""   # optionally paste fetched news / prior memory here
out = ask(f"{system}\n\n---\n\n{task}\n\n---\nCONTEXT:\n{context}")
stamp = datetime.date.today().isoformat()
pathlib.Path("copilot/reports").mkdir(parents=True, exist_ok=True)
pathlib.Path(f"copilot/reports/{stamp}-{pathlib.Path(sys.argv[1]).stem}.md")\
    .write_text(out, encoding="utf-8")
print(out)
```

No dependencies beyond the Python standard library.

## 4. Schedule it

**Linux/macOS (cron)** — run the weekly-news task every Monday at 8am:

```cron
0 8 * * 1  cd ~/copilot && /usr/bin/python3 run_task.py tasks/task-01-weekly-news.md
```

**Windows (Task Scheduler)** — create a Basic Task, trigger Weekly, action:
`python C:\path\to\run_task.py tasks\task-01-weekly-news.md`.

Stagger the tasks across the week so no single run is huge, or loop over several in
one script.

## Giving it the news

A local model has no live internet. Options, cheapest first:

1. **Manual paste** — before the run, paste the week's relevant items into
   `context`. Zero setup; you stay in the loop. Fine to start.
2. **RSS/official feeds** — pull your city/county's press-release and
   meeting-agenda RSS with a small fetch step, and hand the text to the model.
   Fully local except the fetch.
3. **A search API** — wire a search endpoint (SearXNG self-hosted, or a commercial
   search API) into the runner and let the model request lookups. Most capable,
   most setup.

Whatever you choose, keep the honesty rule: the model **proposes and drafts**;
**verification means a real source**, not the model's confidence. A local model is
*more* prone to confabulate, so lean harder on "prefer official sources" and treat
any unsourced claim as unconfirmed.

## Privacy & resilience notes

- `notes.private.md` and your civic profile never touch a network. That's the whole
  point of self-hosting.
- The system survives provider outages, account bans, and regional blocks — it's
  yours. Keep a backup of the `copilot/` folder.
- If you later run the sibling [My Citizen Atlas](https://github.com/shaelsrv/mycitizenatlas)
  map (also self-hostable on local models), you can ground the chain of
  responsibility in real law entirely offline.

---

Next: the [17 tasks](../tasks/) and the [permanent instructions](../prompts/PERMANENT_INSTRUCTIONS.md).
Prefer the least-effort path? See [`HOSTED.md`](HOSTED.md).
