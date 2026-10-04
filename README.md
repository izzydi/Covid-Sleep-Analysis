# COVID-19 and Sleep Quality Analysis

An R-based machine-learning project exploring multi-class sleep-quality classification in data collected in the context of the COVID-19 period.

## Primary workflow

[`covid_sleep_analysis.Rmd`](covid_sleep_analysis.Rmd) is the audited baseline. It performs deterministic BMI feature engineering, creates a stratified hold-out split before learned preprocessing and uses a tidymodels recipe that is re-estimated correctly inside training resamples. A Ranger Random Forest is tuned on training folds and evaluated once on the untouched test partition.

## Repository contents

- [`covid_sleep_analysis.Rmd`](covid_sleep_analysis.Rmd) — audited R Markdown workflow.
- [`archive/legacy_exploration.Rmd`](archive/legacy_exploration.Rmd) — original experimental coursework.
- [`data/README.md`](data/README.md) — expected workbook layout.
- [`R-packages.txt`](R-packages.txt) — direct R dependencies.

## Audit improvements

The legacy workflow fitted KNN imputation separately on the test set, made several data-dependent decisions before splitting and contained a Ranger hyperparameter-indexing bug. It also treated the square root of classification error as RMSE. Those choices are removed from the primary workflow.

The audited version deliberately starts with a simpler leakage-safe Random Forest baseline. SMOTE, AVF and other experimental imbalance/outlier methods can be reintroduced only if they are applied inside training resamples.

## Data

The source workbook is external and is not committed. Place `SleepAllData.xlsx` under `data/` as described in [`data/README.md`](data/README.md).

## Reproducing the analysis

1. Add the workbook under `data/`.
2. Install packages listed in [`R-packages.txt`](R-packages.txt).
3. Run or knit `covid_sleep_analysis.Rmd` from top to bottom.

## Scope

This is an academic machine-learning project and **not** a clinical diagnostic tool.
