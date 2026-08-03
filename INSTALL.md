# Citizen Copilot — guided installation (no GitHub needed)

This is the **fastest way to install Citizen Copilot** — and the only practical one
inside a chat assistant, where there's no GitHub connection to clone the repo or
reference its files. Instead of copying files by hand, you paste **one guided prompt**
that interviews you, produces tailored project instructions, and prepares or creates
the recurring briefings you approve. Every task it generates is **self-contained** (it
doesn't depend on any repo file), which is exactly what a chat assistant needs.

Works in any assistant that has **Projects/Gems + memory**: **ChatGPT Projects**,
**Claude Projects**, or **Gemini Gems**. (Prefer to set it up by hand from the files
instead? See [`hosting/HOSTED.md`](hosting/HOSTED.md).)

Citizen Copilot is part of the Emergence Machine project. Original repository: https://github.com/shaelsrv/citizen-copilot

## Is it safe to paste a big prompt? (yes — here's why)

A long instruction prompt can look like a prompt-injection attempt. This installer is designed to be the opposite: it follows a **Review → Explain → Confirm → Apply** workflow and **never assumes permission to change behavior**.

- When you paste it, it should **explain itself first** and **ask before doing anything** — not silently reconfigure your assistant.
- It only affects **this Project/Gem**, not your global assistant settings.
- It won't ask for a street address or sensitive personal data, won't send your data anywhere, and creates **no recurring task** until you approve the exact list shown.
- You can inspect and edit everything it produces, choose a Minimal / Recommended / Full setup, and say `cancel` at any time.

If the assistant instead tries to act without confirming, or asks for sensitive data, stop — that's not how this installer is meant to behave.

## What you need

- An assistant account with **Projects** (ChatGPT / Claude) or **Gems** (Gemini).
- Scheduled tasks/automations if your plan and client support them. If they are unavailable, the installer produces ready-to-copy prompts instead.
- About 5–10 minutes to answer the setup questions.

## Install

1. Create a new **Project** (ChatGPT / Claude) or **Gem** (Gemini) named **Citizen Copilot**.
2. Open it and start a new chat inside it.
3. Open `BOOTSTRAP_PROMPT.md`, copy everything between `BEGIN BOOTSTRAP PROMPT` and `END BOOTSTRAP PROMPT`, and paste it into the chat.
4. Answer the interview. The installer asks one question at a time. You may say `use defaults`, `skip`, or `back` at any point.
5. When it shows the completed **Project instructions**, copy that block into the Project's instructions/settings field.
6. Return to the installer chat and say `done`.
7. Review the proposed recurring-task table. Nothing recurring should be created until you explicitly approve it.
8. If ChatGPT can create automations, allow it to create only the approved tasks. Otherwise, copy each generated task prompt into ChatGPT's task/automation interface manually.
9. Run each task once as a test. Check that the location, dates, citations, and official sources are correct before leaving it recurring.

## Recommended first installation

Choose **Starter** during the interview:

| Briefing | Default schedule | Purpose |
| --- | --- | --- |
| Weekly News | Sunday, 6:00 PM | What happened? |
| Upcoming Decisions | Monday, 7:00 AM | What can I still influence or attend? |
| Why This Matters | Monday, 6:00 PM | What are the concrete consequences? |

The installer confirms your timezone and lets you change every day and time.

## Installation modes

- **Starter:** Tasks 1, 4, and 10 from the original methodology.
- **Accountability:** Starter plus open promises, follow-ups, and questions worth researching.
- **Systems Watch:** Starter plus trends, emerging issues, connections, and comparisons over time.
- **Custom:** Choose from all 16 Citizen Copilot task types.

Start with Starter. Add tasks only after the first two or three reports are useful; this keeps noise and active-task usage under control.

## Privacy note

The original methodology includes My Personal Notes and Personal Civic Profile. These may contain sensitive personal or political information. The installer excludes them by default and requires a separate confirmation before including either. Do not include anything you would not want stored by your chosen service.

## Updating later

In the Project (or Gem), tell your assistant:

> Re-run the Citizen Copilot setup interview using my current Project instructions as the starting profile. Show every proposed change and wait for my approval before modifying or replacing any recurring task.

## Troubleshooting

- **The assistant answers the prompt instead of interviewing me:** Start a fresh Project chat and paste the whole bootstrap block, including its first and last delimiter lines.
- **It asks many questions at once:** Reply, `Ask one question at a time as instructed.`
- **It cannot create scheduled tasks:** Ask it to print each self-contained prompt, name, schedule, and timezone. Create them manually in the Tasks/Automations area.
- **Reports use the wrong city:** Pause the task, correct the Project instructions and the location embedded in that task, then test it again.
- **Reports have weak sourcing:** Add the official city, county, meeting-calendar, agenda, budget, procurement, court, and public-notice URLs during setup.
- **A task depends on another chat or report:** Replace it with the self-contained version generated by the installer.

## Files in this package

- `BOOTSTRAP_PROMPT.md` — the one prompt to paste into a new Project/Gem chat.
- `INSTALL.md` — these setup and troubleshooting instructions.

## How this relates to the rest of the repo

The installer's interview mirrors the hand-setup files — it just does the assembly
for you and bakes everything into self-contained prompts:

- `prompts/PERMANENT_INSTRUCTIONS.md` — the project-memory template the interview fills.
- `tasks/` — the 16 task specifications; the installer adapts the ones you pick.
- `hosting/HOSTED.md` / `hosting/SELF_HOSTED.md` — the manual (cloud / local-model) paths.

Sibling project: **[My Citizen Atlas](https://github.com/shaelsrv/mycitizenatlas)** — the
source-backed map of who holds what public authority. Citizen Copilot is the assistant;
the atlas is the map it can ground the chain of responsibility in.

