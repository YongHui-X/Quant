# Reversal Branch Status

## Confirmed Ranking

Only runs with `result_state=confirmed` and `include_in_ranking=yes` count here.

1. `volume_conditioned_reversal_v60`
   Formula: `rank(-ts_delta(close, 1)) * rank(volume / ts_mean(volume, 60))`
   Sharpe `2.13`, Turnover `59.29%`, Fitness `1.03`, Returns `13.92%`, Drawdown `8.76%`, Margin `4.70`

## Excluded Or Pending

- `volume_conditioned_reversal_v80_rerun`
  Formula: `rank(-ts_delta(close, 1)) * rank(volume / ts_mean(volume, 80))`
  Status: `pending_rerun`
  Rule: exclude the earlier `80`-day attempt from ranking until a clean rerun produces a fresh metric set.

## Immediate Next Step

1. Run the clean `80`-day rerun for `rank(-ts_delta(close, 1)) * rank(volume / ts_mean(volume, 80))`.
2. Log the fresh metrics in `research/simulation_results.csv`.
3. Compare only the confirmed `60`-day and confirmed `80`-day rows before changing any other variable.

## Next Controlled Queue

- If the confirmed `80`-day rerun beats the `60`-day row on Sharpe and Fitness without unacceptable turnover or drawdown, test `100` days next.
- If the confirmed `80`-day rerun loses to the `60`-day row or looks unstable, test `40` days next.
- Do not change delay, neutralization, truncation, decay, or the price operator until this volume-lookback sweep is resolved.
