# COVID-19 and Sleep Quality Analysis

An R-based machine-learning project exploring sleep-quality classification in a dataset collected in the context of the COVID-19 period.

## Project overview

The source analysis implements a substantial preprocessing and modelling workflow rather than a simple descriptive study. It includes missing-data handling, BMI feature engineering, categorical recoding, outlier detection, stratified train/test splitting, K-nearest-neighbour imputation and class-oriented modelling preparation.

## Repository contents

- [`Adepali.Rmd`](Adepali.Rmd) — complete R Markdown analysis.

## Methods and tools

The workflow uses packages including `caret`, `dplyr`, `recipes`, `ranger`, `visdat`, `UBL`, `DMwR`, `vtreat` and `AtConP`.

Key steps include:

- data cleaning and removal of near-zero-variance predictors,
- BMI calculation and grouping,
- sleep-quality target recoding,
- AVF-based outlier detection,
- train/test splitting,
- missing-data visualization,
- KNN imputation,
- preparation for supervised classification.

## Data requirements

The R Markdown file expects an external Excel dataset named `SleepAllData.xlsx`, which is not committed to this repository. Reproducing the full analysis therefore requires access to that source file.

## Reproducing the analysis

1. Place `SleepAllData.xlsx` in the working directory.
2. Open `Adepali.Rmd` in RStudio.
3. Install the packages listed near the top of the file.
4. Run or knit the analysis.

## Scope

This is an academic machine-learning project intended to demonstrate data preparation, feature engineering and classification workflows. It is not a clinical diagnostic tool.
