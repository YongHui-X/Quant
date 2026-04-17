# Dev Doc

## Purpose

This repo is a lightweight research workspace for WorldQuant BRAIN IQC Stage 1.

It is not a full local backtesting engine.

Use this repo to:

- organize alpha families
- write down hypotheses and settings
- preview ledger rows before testing
- log what you tested
- keep a learning history of major changes

## Main Files

- `codex.md`: repo operating policy
- `research/competition_notes.md`: workflow, screening rubric, and execution order
- `research/alpha_ledger.csv`: tracking table for tested variants
- `research/simulation_results.csv`: simulation metrics, ranking state, and rerun quarantine
- `research/reversal_status.md`: current confirmed ranking and next queued reversal test
- `research/change_learning_log.md`: major-change learning log
- `output/jupyter-notebook/iqc-stage1-research.ipynb`: main research notebook

## How To Run

Open PowerShell and run:

```powershell
cd "C:\Users\User\All my projects\Quant"
& ".\.venv\Scripts\python.exe" -m jupyter lab
```

Then open:

- `output/jupyter-notebook/iqc-stage1-research.ipynb`
- choose the kernel `Quant (py313)` if Jupyter asks

## How To Use The Notebook

Run the cells from top to bottom.

The notebook does four main things:

1. defines the helper structures for alpha families and ledger rows
2. loads the starter alpha slate
3. gives three concrete starter variants for the first family
4. prepares preview ledger rows before you write anything to the CSV

For the first session:

1. run all cells
2. inspect `first_family_variants`
3. start with `baseline_reversal_1d`
4. review `variant_rows[0]`
5. if the row looks correct, uncomment the matching `append_ledger_row(...)` line
6. log the variant
7. test the same formula manually in WorldQuant BRAIN
8. write down the result and next action

## How To Test The Workspace

### Manual Test

Use this when you want the simplest check:

1. open the notebook
2. run all cells without errors
3. confirm `starter_families` exists
4. confirm `first_family_variants` contains 3 variants
5. confirm `variant_rows` contains 3 rows

### PowerShell Sanity Test

Use this when you want to verify the notebook code outside Jupyter without changing the repo:

```powershell
cd "C:\Users\User\All my projects\Quant"
& ".\.venv\Scripts\python.exe" -c "import json, pathlib, os; nb=pathlib.Path(r'C:\Users\User\All my projects\Quant\output\jupyter-notebook\iqc-stage1-research.ipynb'); data=json.load(nb.open('r', encoding='utf-8')); g={}; os.chdir(nb.parent); [exec(''.join(cell['source']), g, g) for cell in data['cells'] if cell.get('cell_type')=='code']; print('cells_executed'); print(len(g['starter_families'])); print(len(g['first_family_variants'])); print(g['variant_rows'][0]['family_name']);"
```

Expected result:

- `cells_executed`
- a starter family count
- `3` variants
- `pv_reversal_outsized_move`

## Kernel And Environment

This repo uses:

- local interpreter: `.venv\Scripts\python.exe`
- notebook kernel: `Quant (py313)`

Reason:

- it avoids ambiguity with the global `python3` kernel
- it keeps this repo on a stable Python 3.13 interpreter
- it makes the documented run and test commands match the notebook environment

## How To Log Work

### Alpha testing

Log tested variants in:

- `research/alpha_ledger.csv`

Log simulation metrics and clean ranking state in:

- `research/simulation_results.csv`

Use only these statuses:

- `planned`
- `screened`
- `simulated`
- `submittable`
- `submitted`
- `retired`

For ranking hygiene:

- count only `confirmed` result rows in `research/simulation_results.csv`
- set `include_in_ranking` to `no` for mislabeled or duplicated attempts
- rerun suspicious entries cleanly before comparing them against the current leader

### Major repo changes

Log major changes in:

- `research/change_learning_log.md`

A major change includes:

- workflow changes
- notebook structure changes
- new durable files
- logging changes
- material research-process changes

For every major change:

1. add a learning-log entry
2. explain it normally
3. explain it again in simple language

## What This Repo Does Not Do

- it does not simulate directly on BRAIN
- it does not submit alphas automatically
- it does not replace the official WorldQuant platform

Use this repo to prepare better tests, not to replace platform execution.
