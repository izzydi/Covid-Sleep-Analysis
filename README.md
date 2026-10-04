# COVID-19 and Sleep Quality Analysis

An R-based machine-learning project exploring multi-class sleep-quality classification in data collected in the context of the COVID-19 period.

## Primary workflow

[`covid_sleep_analysis.Rmd`](covid_sleep_analysis.Rmd) is the audited baseline. It performs deterministic BMI feature engineering, creates a stratified hold-out split before learned preprocessing and uses a tidymodels recipe that is re-estimated correctly inside training resamples. A Ranger Random Forest is tuned on training folds and evaluated once on the untouched test partition.

## Repository contents

- [`covid_sleep_analysis.Rmd`](covid_sleep_analysis.Rmd) — audited R Markdown workflow.
- [`archive/legacy_exploration.Rmd`](archive/legacy_exploration.Rmd) — original experimental coursework.
- [`data/README.md`](data/README.md) — expected workbook layout.
- [`R-packages.txt`](R-packages.txt) — version-pinned direct R dependencies.
- [`.github/workflows/r-ci.yml`](.github/workflows/r-ci.yml) — R 4.6.1 dependency and syntax CI.

## Audit improvements

The legacy workflow fitted KNN imputation separately on the test set, made several data-dependent decisions before splitting and contained a Ranger hyperparameter-indexing bug. It also treated the square root of classification error as RMSE. Those choices are removed from the primary workflow.

The current workflow keeps near-zero-variance filtering and imputation inside the resampled recipe, uses `grid_space_filling()` rather than the deprecated Latin-hypercube helper, and reserves the test split for one final `last_fit()` evaluation. SMOTE, AVF and other experimental imbalance/outlier methods are intentionally omitted from the baseline unless they can be applied inside training resamples.

## Reproducibility and CI

The direct R package versions are pinned in [`R-packages.txt`](R-packages.txt). GitHub Actions uses R 4.6.1 and `pak` to install those exact direct package versions, then extracts and parses the canonical R Markdown source on every push and pull request.

`R-packages.txt` is a direct-dependency manifest rather than a complete `renv.lock` snapshot; recursive dependency resolution is handled by `pak`.

## Data

The source workbook is external and is not committed. Place `SleepAllData.xlsx` under `data/` as described in [`data/README.md`](data/README.md).

## Reproducing the analysis

1. Install R 4.6.1.
2. Add the workbook under `data/`.
3. Install `pak` and the pinned direct dependencies:

```r
install.packages("pak")
pak::pkg_install(readLines("R-packages.txt"), upgrade = FALSE)
```

4. Run or knit `covid_sleep_analysis.Rmd` from top to bottom.

## Scope

This is an academic machine-learning project and **not** a clinical diagnostic tool.
