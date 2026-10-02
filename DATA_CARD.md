# Data Card: Irish Mortgage Arrears Forecasting Dataset

## Source
Central Bank of Ireland, *Residential Mortgage Arrears and Repossession Statistics*
(https://data.gov.ie/dataset/residential-mortgage-arrears-and-repossession-statistics). Licence: CC BY 4.0.
Quarterly, 2009-09-30 to latest release, subject to revision. Pulled on 2026-09-30.
Raw file: `raw/moa-open-data.csv` (SHA-256 `67b8ac6b677928f8...`).

## What one row is
One observation per (quarter, format) for the modelling entity **All**.
Features come from quarter t; the label `target_next_q` is **arrears_total** at quarter t+1.

## Split (historical, defined on the target quarter)
| Split | Feature quarters | Feature date range | Target quarters |
|---|---|---|---|
| Train | 41 | 2010-09-30 to 2020-09-30 | 2010Q4 to 2020Q4 |
| Dev | 8 | 2020-12-31 to 2022-09-30 | 2021Q1 to 2022Q4 |
| Test | 8 | 2022-12-30 to 2024-09-30 | 2023Q1 to 2024Q4 |
| New data (sprint 4) | 6 | 2024-12-31 to 2026-03-31 | 2025Q1 to 2026Q2 |

Why by target quarter: a row's label lives one quarter after its features, so splitting on the
feature date would let a later value leak into the labels of the previous split.
`new_data` is held back untouched. Its newest row has no label yet and is the row to predict from.
CV: expanding window on train only, 5 folds, 4 validation quarters each, 1-quarter gap.

## Storage
GCS `gs://mortgage_irish_forecast_trends`: `raw/` (untouched source) and `sharded/` (parquet exports, object versioning on).
BigQuery `mortgages-forecasting-trends.mortgage_arrears`: `moa_tidy_long`, `features_v1`, `coop_features_v1` and one view per split.

## Known issues and decisions
- Values were text in places; coerced to numeric (thousands separators removed).
- The "over 180 days" row exists only for 2009 to mid-2012. Rebuilt as: residual: total - up_to_90 - 91_to_180
  (overlap check, max abs diff: 0.0).
- Banks and Non-Banks are combined for the national series, so loan-book sales between them cancel out.
- BTL data starts 2012; PDH starts 2009.
- Co-operation / restructure features exist only from 2019-09-30 and are kept in `coop_features_v1`;
  too few train quarters overlap them to train a model on this split.
- The publisher revises past figures; `data_vintage` records the pull date of every row.
- Small sample and strong distribution shift (arrears fell sharply after 2013): dev and test are calmer
  than the training crisis period, so always report naive baselines next to model scores.

## Columns
| Column | dtype | Description |
|---|---|---|
| reporting_date | datetime64[us] | Quarter-end date of the FEATURES (dd/mm/yyyy in source, parsed to a date) |
| entity_group | str | Lender group: 'All' = Banks + Non-Banks combined; otherwise 'Banks' or 'Non-Banks' |
| loan_format | str | PDH = principal dwelling home; BTL = buy-to-let |
| arrears_total | float64 | Number of mortgage accounts in arrears (all buckets) |
| over180_share | float64 | Accounts in arrears over 180 days / total accounts in arrears (rebuilt as a residual) |
| b91_180_growth | float64 | Quarter-on-quarter % change in accounts 91-180 days in arrears (inflow signal) |
| target_next_q | float64 | Next quarter's value of 'arrears_total' (forecast label); empty for the newest quarter |
| arrears_total_lag1 | float64 | 'arrears_total' lagged 1 quarter(s) |
| arrears_total_lag2 | float64 | 'arrears_total' lagged 2 quarter(s) |
| arrears_total_lag3 | float64 | 'arrears_total' lagged 3 quarter(s) |
| arrears_total_lag4 | float64 | 'arrears_total' lagged 4 quarter(s) |
| data_vintage | str | Date the raw file was pulled (publisher revises past figures) |
| feature_version | str | Feature-set version that produced the row |
| target_quarter | str | Quarter the label belongs to (feature quarter + 1); the split is defined on this column |
| split | str | train / dev / test / new_data (historical, by target quarter) |