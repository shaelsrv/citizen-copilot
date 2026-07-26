# Contributing to Citizen Copilot

This is a spec, not an app — so contributions are mostly **prompts, guides, and
localizations**, not code. The bar is: does it help a citizen become better
informed without telling them what to think?

## Good contributions

- **A new task** — a single-responsibility weekly prompt that answers a question
  the 15 don't. Add `tasks/task-NN-<slug>.md` in the existing format (Purpose →
  scheduled prompt → output format), and a row in `tasks/README.md`.
- **A hosting guide** — setup for another assistant or scheduler (a new cloud
  project type, a home-server recipe, a phone-based flow).
- **A localization** — the permanent instructions and tasks translated/adapted for
  another country's government structure and sources. Keep the ground rules intact.
- **Better source lists** — official-source pointers for a specific city/county so
  the assistant searches the right places.

## The non-negotiable rules (same spirit as the sibling project)

Every task and guide must preserve these, because they're what make the Copilot a
tool for the citizen's judgment rather than a persuasion engine:

1. **Separate fact from opinion**, and label which is which.
2. **Prefer official / primary sources**; a model's confidence is not a source.
3. **Never recommend candidates or tell the user how to vote.**
4. **Surface uncertainty honestly** — a labeled "unconfirmed" beats false
   confidence.
5. **Curiosity, not accusation** — questions are framed to inform, not to indict.

## Sibling project

The map that grounds the "chain of responsibility" lives in
[My Citizen Atlas](https://github.com/shaelsrv/mycitizenatlas) (who holds what
public authority, traced to the constitution and statutes). If your contribution
connects the Copilot's output to that graph, link it — the two are designed to fit.

## How to submit

Open a pull request. Keep prompts in plain text (they're meant to be copied), keep
files LF-ended, and describe what question your addition helps a citizen answer.
