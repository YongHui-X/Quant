# Quant Workspace Policy

## Objective

Maximize the probability of advancing in WorldQuant BRAIN IQC 2026 Stage 1.

## Default Operating Assumptions

- Work as a solo operator unless the user explicitly asks to coordinate teammates.
- Keep the repo notebook-first and research-first.
- Treat official WorldQuant competition pages and platform behavior as the source of truth.
- Use the local workspace to document ideas, decisions, and submission history.
- Use `Quant_analyst.md` as domain guidance for quant research, strategy framing, validation, and risk analysis when it is helpful.
- `Quant_analyst.md` is advisory, not mandatory. If direct evidence, platform constraints, or stronger domain reasoning conflict with it, override it explicitly and proceed with the better approach.

## Research Workflow

1. Capture each idea as an alpha family with a short economic thesis.
2. Write the hypothesis, expected mechanism, settings to test, and acceptance rule in the research notebook.
3. Simulate only ideas that survive the notebook screen.
4. Record every simulated or submitted alpha in the ledger.
5. Review families in batches and stop spending time on weak families quickly.

## Priority Order

1. Price-volume alpha families
2. Fundamental and model-data alpha families
3. Advanced datasets only after the first two groups are producing repeatable submittable ideas

## Required Logging

Every alpha entry must include:

- family name
- thesis summary
- data class
- region
- universe
- delay
- neutralization
- truncation
- decay
- status
- result notes

## Anti-Patterns

- No undocumented submissions
- No duplicate-account behavior
- No account sharing
- No blind parameter spam
- No repeated testing of the same weak family without a clear reason
- No teammate overlap unless roles are explicitly split

## Output Conventions

- Keep notebook experiments in `output/jupyter-notebook/`.
- Keep durable notes in `research/competition_notes.md`.
- Keep alpha tracking in `research/alpha_ledger.csv`.
- Keep major-change learning entries in `research/change_learning_log.md`.
- Use concise filenames and stable family names.

## Major Change Learning Rule

- For every major change, append an entry to `research/change_learning_log.md`.
- A major change includes new workflow files, durable repo policy changes, notebook structure changes, tracking changes, and material research-process changes.
- Minor wording edits, typo fixes, and cosmetic cleanups do not need log entries.
- After every major change, explain it to the user twice:
  - once normally
  - once again in a separate paragraph at an "11-year-old" level

## Review Cadence

- Daily: learn, research, simulate, log
- Twice weekly: rank families by productivity and retire weak ones
- Final week before the Stage 1 deadline: focus on proven families instead of new domains
