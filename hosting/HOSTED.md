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
| Scheduled/recurring tasks | **Tasks / scheduled** | scheduling where available | scheduling where available |

If your assistant lacks native scheduling, use any external scheduler (a calendar
reminder, or a small cron job that pings the API) to run each task's prompt on its
cadence.

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

Next: the [15 tasks](../tasks/) and the [permanent instructions](../prompts/PERMANENT_INSTRUCTIONS.md).
Want privacy / offline / can't-be-switched-off? See [`SELF_HOSTED.md`](SELF_HOSTED.md).
