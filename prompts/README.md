# Versioned Agent Prompts

Store only **reviewed reusable prompts** that define a task, its source inputs, allowed actions, acceptance criteria and stop point. Number prompts chronologically, and archive major revisions as new versions. Do not commit unredacted raw agent conversations, credentials or personal notes.

Before using a prompt: check `AGENTS.md`, `docs/operations/CURRENT_STATE.md` and the decision register. A prompt cannot override the current approval gate.

- `000-resume-project.md` — Turnkey prompt for a fresh AI session to resume work from GitHub without hallucinating.
- `001-product-decision-workshop.md` — Step-by-step interview prompt for reviewing and resolving product decisions.
- `002-review-import-governance.md` — Documentation-only baseline import and governance verification prompt.
- `003-code-review.md` — Professional 10-point code review workflow based on Google Engineering Practices and Flutter quality standards.
