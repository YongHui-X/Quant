# Major Change Learning Log

## 2026-04-16 - Initial IQC workspace policy

Why this change was made:
- The repo needed a durable operating policy so future work would not restart from zero each session.

Files affected:
- `codex.md`

What changed:
- Added the repo objective, solo-first assumption, research workflow, priority order, required logging fields, anti-patterns, and review cadence.

Validation:
- Reviewed the file content directly and used it as the source of truth for later workspace setup.

Normal explanation:
This created the working rules for the repo. Instead of relying on chat memory, the workspace now has a written policy that fixes the research order, logging expectations, and what to avoid.

Explain like I'm 11:
This is like making the class rules before starting a group project. It tells us what game we are playing, how to keep score, and what cheating or sloppy work looks like.

## 2026-04-16 - Competition notes and execution checklist

Why this change was made:
- The repo needed a single place to capture dates, research priorities, and the day-to-day workflow for Stage 1.

Files affected:
- `research/competition_notes.md`

What changed:
- Added key competition dates, current operating assumption, research priorities, daily loop, alpha acceptance rule, weekly review steps, and an official-source reminder.

Validation:
- Checked the file content after creation and used it to guide later planning.

Normal explanation:
This file became the tactical notebook for the competition process. It translates the high-level policy into a concrete routine for learning, testing, and reviewing ideas.

Explain like I'm 11:
This is the team's checklist page. It says what to do each day, what counts as a good idea, and what to look at every week so we do not get lost.

## 2026-04-16 - Alpha ledger initialization

Why this change was made:
- The research process needed a structured place to track every tested alpha and avoid duplicate, undocumented work.

Files affected:
- `research/alpha_ledger.csv`

What changed:
- Added a CSV header with the key fields needed to track family, settings, status, and notes for each tested variant.

Validation:
- Confirmed the file exists with the expected header and matched the notebook row shape against it.

Normal explanation:
This created a flat tracking table for alpha work. Each concrete tested variant can now be logged consistently instead of living only in notebook text or memory.

Explain like I'm 11:
This is the score sheet. Every time we try an idea, we write down what it was, what settings we used, and whether it worked.

## 2026-04-16 - Competition notebook scaffold

Why this change was made:
- The repo needed a reproducible place to think through alpha families before sending ideas to BRAIN.

Files affected:
- `output/jupyter-notebook/iqc-stage1-research.ipynb`

What changed:
- Created the first experiment notebook, then adapted the generic template into a competition-focused notebook with a minimal alpha structure and ledger row preview.

Validation:
- Parsed the notebook as JSON and executed its code cells successfully.

Normal explanation:
This established the main research surface for the repo. The notebook moved from a generic template to a competition-aware scaffold that could produce structured alpha entries.

Explain like I'm 11:
This is the practice workbook. Instead of scribbling ideas anywhere, we now have one place to think, test, and write things down in the same format every time.

## 2026-04-16 - Quant analyst guidance integration

Why this change was made:
- `Quant_analyst.md` contained useful domain guidance, but it needed a clear place in the repo's rule hierarchy.

Files affected:
- `codex.md`

What changed:
- Added instructions to use `Quant_analyst.md` as helpful quant guidance while keeping it advisory rather than mandatory.

Validation:
- Confirmed the guidance and override rule were present in `codex.md`.

Normal explanation:
This change gave the repo access to stronger domain context without letting that file override better evidence or platform-specific constraints.

Explain like I'm 11:
This is like keeping a smart helper book on the desk. We can use it when it helps, but if we learn something better or more correct, we are allowed to follow that instead.

## 2026-04-16 - Learning log and starter alpha slate

Why this change was made:
- The repo needed to teach as it evolves, and the notebook needed concrete research content instead of a single placeholder idea.

Files affected:
- `codex.md`
- `research/competition_notes.md`
- `research/change_learning_log.md`
- `output/jupyter-notebook/iqc-stage1-research.ipynb`

What changed:
- Added a major-change learning rule to the workspace policy.
- Added a screening rubric, fixed status set, and starter-slate order to the competition notes.
- Added this learning log with backfilled major changes.
- Replaced the notebook placeholder with an executable starter alpha slate covering price-volume, fundamental/model, and one advanced placeholder.

Validation:
- Re-ran the notebook code cells after the update and confirmed they executed successfully and produced valid preview rows.

Normal explanation:
This change turned the repo from a process shell into a teachable research workspace. The policy now requires major changes to be documented for learning, and the notebook now contains an actual first-wave research slate rather than one sample row.

Explain like I'm 11:
Before, we had the rules and an empty workbook. Now we also have lesson notes and a real set of first ideas to practice with, so you can see what we changed and why as we build.

## 2026-04-16 - First concrete family walkthrough

Why this change was made:
- The repo still lacked a simple, actionable starting point for actually testing an idea.

Files affected:
- `research/competition_notes.md`
- `output/jupyter-notebook/iqc-stage1-research.ipynb`

What changed:
- Added a first practical execution order to keep the initial session focused on one family.
- Added three concrete variants for `pv_reversal_outsized_move` plus preview ledger rows and plain-English notes in the notebook.

Validation:
- Re-ran the notebook code cells after the update and confirmed the new variant structures executed successfully.

Normal explanation:
This change narrowed the starting scope from "many possible alpha families" to one concrete family with three initial variants. That reduces confusion and gives a direct first set of tests instead of abstract planning only.

Explain like I'm 11:
This is like saying, "stop looking at the whole textbook and just do page one." We picked one idea and made three simple versions of it so you can start testing instead of feeling lost.

## 2026-04-16 - Development run and test guide

Why this change was made:
- The repo needed a single place that explains how to run the notebook workflow and how to sanity-check it without guessing commands.

Files affected:
- `dev_doc.md`
- `research/change_learning_log.md`

What changed:
- Added `dev_doc.md` with the repo purpose, file map, Jupyter launch command, notebook usage steps, a non-mutating PowerShell sanity test, and logging instructions.

Validation:
- Reviewed the commands against the current environment and confirmed the documented notebook sanity test matches the existing executable workflow.

Normal explanation:
This change added an operator-facing guide for the repo. Instead of relying on scattered chat answers, the project now has one document that explains how to open the workspace, run the notebook, and test that the notebook logic still works.

Explain like I'm 11:
This is the instruction sheet that comes with the project. It tells you which button to press first, what each important file is for, and how to check that the project is still working.

## 2026-04-16 - Repo kernel and environment cleanup

Why this change was made:
- The notebook environment was ambiguous because the repo had no local Python environment and the notebook metadata still pointed at a generic kernel.

Files affected:
- `.gitignore`
- `.venv\pyvenv.cfg`
- `.venv\share\jupyter\kernels\quant-py313\kernel.json`
- `dev_doc.md`
- `output/jupyter-notebook/iqc-stage1-research.ipynb`
- `research/change_learning_log.md`

What changed:
- Reused the existing Python 3.13 installation through a repo-local `.venv`.
- Enabled system site packages for that environment so it can see the installed Jupyter stack.
- Added a dedicated repo kernel named `Quant (py313)`.
- Updated the notebook metadata and developer docs to use that kernel and local interpreter.
- Added a root `.gitignore` so the environment does not pollute git status.

Validation:
- Confirmed the repo-local Python can import `ipykernel` and `jupyterlab`.
- Confirmed Jupyter search paths include `.venv\share\jupyter`.
- Confirmed the new kernel is discoverable and used by the notebook metadata.

Normal explanation:
This change removed kernel ambiguity. The repo now has a stable local interpreter and a dedicated notebook kernel, so running the notebook no longer depends on whichever global Python or generic `python3` kernel Jupyter happens to pick.

Explain like I'm 11:
Before, the notebook was using a vague "some Python" setup. Now it has its own named engine, like putting the right battery into a toy and labeling it so you always know which one to use.

## 2026-04-17 - Simulation result tracker and clean rerun workflow

Why this change was made:
- Live BRAIN metrics for the reversal branch were not stored durably in the repo, which made it too easy to mis-rank a suspicious `80`-day run against the confirmed `60`-day leader.

Files affected:
- `dev_doc.md`
- `research/alpha_ledger.csv`
- `research/change_learning_log.md`
- `research/competition_notes.md`
- `research/reversal_status.md`
- `research/simulation_results.csv`

What changed:
- Added durable ledger rows for the confirmed `60`-day abnormal-volume reversal and the pending `80`-day rerun.
- Added `research/simulation_results.csv` to store simulation metrics, ranking eligibility, and rerun status.
- Added `research/reversal_status.md` to show the current confirmed ranking and the exact next single-variable test.
- Updated the docs to require confirmed-only ranking and to quarantine mislabeled or duplicated runs until rerun.

Validation:
- Reviewed the new CSV and markdown files directly and confirmed the `60`-day row is ranked while the `80`-day rerun is explicitly excluded pending clean metrics.

Normal explanation:
This change turned the current reversal-session memory into durable repo state. The best confirmed `60`-day result is now logged in a place that can be ranked cleanly, and the suspicious `80`-day attempt is held out of the ranking until a proper rerun is entered.

Explain like I'm 11:
We wrote down which test really won and put the confusing `80`-day test in a waiting box. That way the scoreboard only shows real scores, and the messy score has to be replayed before it can count.
