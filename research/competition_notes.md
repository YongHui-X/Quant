# IQC 2026 Competition Notes

## Objective

Build a repeatable Stage 1 workflow that produces differentiated, submittable alphas fast enough to matter before the deadline.

## Key Dates

- Stage 1 start: March 17, 2026
- Team change lock: May 13, 2026
- Stage 1 end: May 18, 2026

## Current Operating Assumption

- Plan and work as if this repo is run by one person.
- Teammates can be added later only after the workflow is stable.

## Research Priorities

1. Price-volume
2. Fundamental and model data
3. Advanced datasets after a stable baseline exists

## Daily Loop

1. Learn one official concept or dataset/operator family.
2. Add or refine one alpha family in the notebook.
3. Simulate only ideas that pass the notebook screen.
4. Log every outcome in the ledger.
5. Review whether the family should continue, pivot, or stop.

## Alpha Family Acceptance Rule

Use this before simulation:

- clear economic or behavioral thesis
- one or two key operator ideas to test
- a defined setting sweep
- a reason the family is not redundant with prior work
- an explicit rule for what counts as promising

## Screening Rubric

Score each new family from 1 to 5 on:

- thesis clarity
- distinctness from existing families
- implementation simplicity
- expected robustness
- overfitting risk, where 5 means low overfitting risk

Do not simulate a family until it has:

- a clear thesis
- at least one concrete operator pattern
- a reason it is different from recent work
- a stop rule if early variants fail

## Ledger Status Convention

Use only these status values in `research/alpha_ledger.csv`:

- planned
- screened
- simulated
- submittable
- submitted
- retired

## Weekly Review

- Count simulated ideas
- Count submittable ideas
- Identify top families by output rate
- Retire families with repeated weak outcomes
- Note duplication risk before testing adjacent variants

## Starter Slate Order

Start with these family groups in order:

1. Price-volume reversal after outsized move
2. Reversal with abnormal volume filter
3. Momentum with liquidity sanity check
4. Volatility-normalized dislocation
5. Valuation-gap reversion
6. Quality and profitability cross-section
7. Model-change or estimate-reaction family
8. One advanced placeholder only after the first groups are producing useful results

## First Practical Execution Order

For the first working session, stay inside one family only:

1. `pv_reversal_outsized_move`
2. test the plain version first
3. test one volatility-normalized version
4. test one volume-conditioned version

Do not move to the next family until you have logged what happened for these first variants.

## Clean Ranking Rule

- Keep simulation metrics in `research/simulation_results.csv`.
- Rank only rows where `result_state` is `confirmed` and `include_in_ranking` is `yes`.
- If a run looks mislabeled, duplicated, or otherwise untrustworthy, mark it as a pending rerun and exclude it from ranking until it is rerun cleanly.
- Do not let an unconfirmed rerun displace a confirmed leader.

## Current Reversal Branch State

- Confirmed leader: `rank(-ts_delta(close, 1)) * rank(volume / ts_mean(volume, 60))`
- Current confirmed metrics: Sharpe `2.13`, Turnover `59.29%`, Fitness `1.03`, Returns `13.92%`, Drawdown `8.76%`, Margin `4.70`
- Pending cleanup: rerun the `80`-day volume-lookback version cleanly and keep the prior `80`-day attempt out of the ranking.
- Follow-up rule: once the clean `80`-day rerun is logged, continue the same axis only. If `80` wins, test `100`; if `80` loses, test `40`.

## Official Source Reminder

Competition rules, eligibility, and scoring details can change. Re-check official WorldQuant pages before making decisions that depend on deadlines, team rules, or evaluation mechanics.
