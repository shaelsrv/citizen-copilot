# Hosted Citizen Copilot (cloud project)

The fastest, highest-quality way to run your Copilot: a **Project** in a cloud
assistant that supports persistent instructions/memory, built-in web search, and
scheduled tasks. You get frontier-model reasoning and live news with a few minutes
of setup and no maintenance.

The trade-off: your location, interests, and civic profile live with the provider
under their privacy policy, and availability depends on the provider being
reachable where you are. If either matters to you, see [`SELF_HOSTED.md`](SELF_HOSTED.md)
— you can also run both.

---

## Works with any assistant that has: memory + web + scheduling

The concepts map across products; the names differ.

| Capability | ChatGPT | Claude | Gemini |
|---|---|---|---|
| Persistent instructions | **Projects** (project instructions) | **Projects** (project knowledge/instructions) | **Gems** (instructions) |
| Web search | built-in | built-in | built-in |
| Scheduled/recurring tasks | **Tasks / scheduled** (some plans) | usually **none** | usually **none** |

### No native scheduling? Run it manually — it works the same

**Most Claude Projects and Gemini Gems have no built-in scheduler today**, and some
ChatGPT tiers don't either. That's fine — Citizen Copilot doesn't need one. Every
task prompt is **self-contained**, so pasting one into the project on demand produces
the exact same briefing a scheduled run would.

So if you can't schedule:

1. Keep each task's prompt handy (in a note, or just reopen its file here).
2. **Paste the prompt into your project when you want that briefing** — Weekly News on
   a Sunday, Upcoming Decisions on a Monday, and so on.
3. Set a **phone or calendar reminder** for the cadence (e.g. a weekly Sunday-evening
   reminder titled "Citizen Copilot — Weekly News") so it becomes a habit.

The whole system runs perfectly this way; scheduling only saves you the paste. Don't
let a missing scheduler stop you — and if an assistant tells you it "set up recurring
tasks" without a real scheduler, it didn't; ask it for the copy-ready prompts instead.

---

## Setup (≈ 10 minutes)

1. **Create a Project** and name it — *Citizen Copilot*, *My Civic Dashboard*,
   *Local Accountability Assistant*, *Civic Intelligence*, or *My Government Watch*.
   The name doesn't matter; a dedicated project (not a one-off chat) is what gives
   you persistent memory.

2. **Paste the permanent instructions** from
   [`../prompts/PERMANENT_INSTRUCTIONS.md`](../prompts/PERMANENT_INSTRUCTIONS.md)
   into the project's instructions/knowledge, with your location, interests, and
   ground rules filled in. Every task inherits this — it's the multiplier.

   **Read-back check (recommended):** after pasting, send one message:
   *"Read back your understanding of my location, interests, and ground rules
   in your own words before saving anything."* People fill templates tersely,
   autocorrect mangles words, and place names collide across countries - a
   30-second confirmation prevents weeks of subtly mis-aimed briefings. If the
   assistant's read-back is wrong, correct it now, while it's cheap.

3. **Add the tasks you want as scheduled prompts.** Open each
   [task file](../tasks/), copy its "Scheduled prompt" block, and create a recurring
   task with it on the suggested cadence (mostly weekly). Start with **Task 1
   (Weekly News)**, **Task 4 (Upcoming Decisions)**, and **Task 10 (Why This
   Matters)** — add more once the rhythm feels right.

4. **Run Task 1 once by hand** to confirm the output looks the way you want, then
   tune the permanent instructions (tone, length, which sources) and let the
   schedule take over.

## Getting the most from a hosted project

- **Let memory accumulate.** The Accountability Tracker (2), Institutional Memory
  (9), Trend Watch (3), and Knowledge Graph (12) get better every week because the
  project remembers. Don't reset the project.
- **Keep the ground rules in the project instructions**, not just in a task — so
  "separate fact from opinion" and "prefer official sources" apply to everything,
  including your ad-hoc questions.
- **Point it at your official sources.** In the permanent instructions, name your
  city/county's site, meeting portal, and budget page. Hosted models search better
  when told where to look.
- **Privacy hygiene.** Your Task 5 notes and civic profile live with the provider.
  If you want those strictly private, keep *only* the notes task on a
  [self-hosted](SELF_HOSTED.md) local model and run everything else in the cloud —
  a clean hybrid.

## Cost & availability

- Runs on a normal subscription; scheduled weekly tasks are light usage.
- If the provider becomes unavailable in your region, your memory is stranded with
  them. For a briefing you depend on, keep a periodic export of the project's
  accumulated memory (promises ledger, institutional record) as plain text — and
  consider the self-hosted option as a fallback.

---

Next: the [16 tasks](../tasks/) and the [permanent instructions](../prompts/PERMANENT_INSTRUCTIONS.md).
Want privacy / offline / can't-be-switched-off? See [`SELF_HOSTED.md`](SELF_HOSTED.md).
